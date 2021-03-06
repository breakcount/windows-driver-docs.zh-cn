---
title: MRxLowIOSubmit \ LOWIO \_ OP \_ SHAREDLOCK \ 例程
description: RDBSS 调用 MRxLowIOSubmit \ LOWIO \_ OP \_ SHAREDLOCK \ 例程来请求网络重定向程序打开文件对象上的共享锁。
ms.assetid: 963ec2d1-5e24-4002-a8c9-44faf1515b9f
keywords:
- MRxLowIOSubmit LOWIO_OP_SHAREDLOCK 日常可安装文件系统驱动程序
- PMRX_CALLDOWN
topic_type:
- apiref
api_name:
- MRxLowIOSubmit LOWIO_OP_SHAREDLOCK
api_location:
- mrx.h
api_type:
- UserDefined
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 09b4ca7b88cb88a37b149dd8cb7a0d737b7ef2ef
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89063306"
---
# <a name="mrxlowiosubmitlowio_op_sharedlock-routine"></a>MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] 例程


[RDBSS](./the-rdbss-driver-and-library.md)调用*MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] *例程来请求网络重定向程序打开文件对象上的共享锁。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
PMRX_CALLDOWN MRxLowIOSubmit[LOWIO_OP_SHAREDLOCK];

NTSTATUS MRxLowIOSubmit[LOWIO_OP_SHAREDLOCK](
  _Inout_ PRX_CONTEXT RxContext
)
{ ... }
```

<a name="parameters"></a>parameters
----------

*RxContext* \[in、out\]  
指向 RX \_ 上下文结构的指针。 此参数包含请求操作的 IRP。

<a name="return-value"></a>返回值
------------

*MRxLowIOSubmit \[LOWIO \_ OP \_ SHAREDLOCK \] *将返回 \_ 成功的状态，或者返回相应的 NTSTATUS 值，如以下之一：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">返回代码</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>STATUS_CONNECTION_DISCONNECTED</strong></td>
<td align="left"><p>连接已断开连接。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>STATUS_INSUFFICIENT_RESOURCES</strong></td>
<td align="left"><p>资源不足，无法完成请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>STATUS_INVALID_BUFFER_SIZE</strong></td>
<td align="left"><p>请求的缓冲区大小太大。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>STATUS_INVALID_NETWORK_RESPONSE</strong></td>
<td align="left"><p>从远程服务器收到无效的响应。</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>STATUS_INVALID_PARAMETER</strong></td>
<td align="left"><p>在 <em>RxContext</em>中指定了无效的参数。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>STATUS_LINK_FAILED</strong></td>
<td align="left"><p>尝试重新连接到远程服务器以完成请求失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>STATUS_NOT_IMPLEMENTED</strong></td>
<td align="left"><p>未实现此例程。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>STATUS_SHARING_VIOLATION</strong></td>
<td align="left"><p>发生共享冲突。</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>STATUS_UNSUCCESSFUL</strong></td>
<td align="left"><p>调用失败。</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

RDBSS 调用*MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] * ，以响应接收[**irp \_ MJ \_ lock \_ 控制**](irp-mj-lock-control.md)请求，但在 \_ \_ **MN &gt; 标记**没有 \_ 设置 SL 排他 \_ 锁位的情况，将会有 irp IrpSp lock 的次代码。

在调用*MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] *之前，RDBSS 会修改 RxContext 参数所指向的 RX 上下文结构中的以下成员 \_ ： *RxContext*

**LowIoContext**成员设置为 LOWIO \_ OP \_ SHAREDLOCK。

**LowIoContext. ResourceThreadId**成员设置为在 RDBSS 中启动操作的进程线程。

**LowIoContext**成员设置为**IrpSp- &gt; **LockControl. ByteOffset. QuadPart. 的值。

将 **LowIoContext** 成员设置为 **IrpSp- &gt; LockControl.** 的值。。

将 **LowIoContext** 成员设置为 **IrpSp- &gt; flags**的值。

**LowIoContext**成员的值设置为**IrpSp- &gt; LockControl. QuadPart.** 的值。

RX 上下文结构的 **LowIoContext** 成员 \_ 指定要执行的低 i/o 操作。 由于可以使用 **LowIoContext** 成员来区分请求的低 i/o 操作，因此几个低 i/o 例程可能会指向网络小型重定向程序中的同一例程。 例如，所有与文件锁相关的 i/o 调用都可以在网络小型重定向程序中调用相同的低 i/o 例程，此例程可以使用 **LowIoContext** 成员来区分所请求的锁定和解除锁定操作。

如果*MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] *例程需要很长时间才能完成，则网络微型重定向程序驱动程序应在启动网络通信之前释放 FCB 结构。 可以通过调用 [**RxReleaseFcbResourceForThreadInMRx**](/windows-hardware/drivers/ddi/mrxfcb/nf-mrxfcb-rxreleasefcbresourceforthreadinmrx)来释放 FCB 结构。 当*MRxLowIOSubmit \[ LOWIO \_ OP \_ SHAREDLOCK \] *例程正在处理时，可保证 RX 上下文的**LowIoContext. ResourceThreadId**成员 \_ 指示在 RDBSS 中启动操作的进程线程。

RX 上下文结构的 **LowIoContext. ResourceThreadId** 成员 \_ 可用于代表其他线程发布 FCB 结构。 异步例程完成后，可以释放从初始线程获取的 FCB 结构。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>目标平台</p></td>
<td align="left">桌面型</td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Mrx (包含 Mrx) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**MRxLowIOSubmit \[ LOWIO \_ OP \_ EXCLUSIVELOCK\]**](mrxlowiosubmit-lowio-op-exclusivelock-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ FSCTL\]**](mrxlowiosubmit-lowio-op-fsctl-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ IOCTL\]**](mrxlowiosubmit-lowio-op-ioctl-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ 通知 \_ 更改 \_ 目录\]**](mrxlowiosubmit-lowio-op-notify-change-directory-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ READ\]**](mrxlowiosubmit-lowio-op-read-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_\]**](mrxlowiosubmit-lowio-op-unlock-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ UNLOCK \_ 多个\]**](mrxlowiosubmit-lowio-op-unlock-multiple-.md)

[**MRxLowIOSubmit \[ LOWIO \_ OP \_ WRITE\]**](mrxlowiosubmit-lowio-op-write-.md)

[**RxReleaseFcbResourceForThreadInMRx**](/windows-hardware/drivers/ddi/mrxfcb/nf-mrxfcb-rxreleasefcbresourceforthreadinmrx)

 

