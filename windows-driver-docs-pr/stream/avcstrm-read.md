---
title: AVCSTRM \_ 读取
description: AVCSTRM \_ 读取
ms.assetid: 0bc0c8ae-15b8-4f52-b081-f3eb31ac4478
keywords:
- AVCSTRM_READ 流媒体设备
topic_type:
- apiref
api_name:
- AVCSTRM_READ
api_type:
- NA
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 592832aca0f244b6495c8b6739ec79e971d610b8
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89192883"
---
# <a name="avcstrm_read"></a>AVCSTRM \_ 读取


## <span id="ddk_avcstrm_read_ks"></span><span id="DDK_AVCSTRM_READ_KS"></span>


**AVCSTRM \_ READ**函数代码用于提交使用指定流中的数据填充的数据缓冲区*avcstrm.sys* 。

### <a name="io-status-block"></a>I/o 状态块

如果成功， *avcstrm.sys* 将 **Irp- &gt; IoStatus** 设置为状态 " \_ 成功"。

可能的错误返回值包括：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>错误状态</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STATUS_DEVICE_REMOVED</p></td>
<td><p>与 <strong>AVCSTRM_READ</strong> 操作相对应的设备不再存在。</p></td>
</tr>
<tr class="even">
<td><p>STATUS_CANCELLED</p></td>
<td><p>无法完成请求。</p></td>
</tr>
<tr class="odd">
<td><p>STATUS_INVALID_PARAMETER</p></td>
<td><p>IRP 中指定的参数不正确，</p></td>
</tr>
<tr class="even">
<td><p>STATUS_INSUFFICIENT_RESOURCES</p></td>
<td><p>系统资源不足，无法完成请求。</p></td>
</tr>
<tr class="odd">
<td><p>STATUS_PENDING</p></td>
<td><p>已收到请求，但需要进一步处理。 I/o 完成例程将处理最后的响应。</p></td>
</tr>
</tbody>
</table>

 

### <a name="comments"></a>说明

此函数使用 AVC 流请求块结构中的**CommandData**联合的**BufferStruct**成员 \_ ，如下 \_ \_ 所示。

```cpp
typedef struct _AVC_STREAM_REQUEST_BLOCK {
  ULONG  SizeOfThisBlock;
  ULONG  Version;
  AVCSTRM_FUNCTION  Function;
  .
  .
  PVOID AVCStreamContext;
  .
  .
  union _tagCommandData {
    .
    .
    AVCSTRM_BUFFER_STRUCT  BufferStruct;
    .
    .
  } CommandData;
} AVC_STREAM_REQUEST_BLOCK, *PAVC_STREAM_REQUEST_BLOCK;
```

### <a name="requirements"></a>要求

**标头：** 在 *avcstrm*中声明。 包括 *avcstrm*。

### <a name="span-idavc_stream_request_block_inputspanspan-idavc_stream_request_block_inputspanavc_stream_request_block-input"></a><span id="avc_stream_request_block_input"></span><span id="AVC_STREAM_REQUEST_BLOCK_INPUT"></span>AVC \_ 流 \_ 请求 \_ 块输入

<span id="SizeOfThisBlock__Version_and_Function"></span><span id="sizeofthisblock__version_and_function"></span><span id="SIZEOFTHISBLOCK__VERSION_AND_FUNCTION"></span>**SizeOfThisBlock、Version 和 Function**  
使用 [**INIT \_ AVCSTRM \_ 标头**](/windows-hardware/drivers/ddi/avcstrm/nf-avcstrm-init_avcstrm_header) 宏初始化这些成员。 Pass **AVCSTRM \_ 读入** 宏的 Request 参数。

<span id="AVCStreamContext"></span><span id="avcstreamcontext"></span><span id="AVCSTREAMCONTEXT"></span>**AVCStreamContext**  
指定流上下文 (处理由之前的 **AVCSTRM \_ 打开** 调用返回的) ，该调用是读取操作的数据源。

<span id="BufferStruct"></span><span id="bufferstruct"></span><span id="BUFFERSTRUCT"></span>**BufferStruct**  
指定读取操作应将数据放置到的缓冲区。

子单元驱动程序必须首先分配 IRP 和 [**AVC \_ 流 \_ 请求 \_ 块**](/windows-hardware/drivers/ddi/avcstrm/ns-avcstrm-_avc_stream_request_block) 结构。 接下来，它应使用 [**INIT \_ AVCSTRM \_ 标头**](/windows-hardware/drivers/ddi/avcstrm/nf-avcstrm-init_avcstrm_header) 宏来初始化 AVC \_ 流 \_ 请求 \_ 块结构，并 **将 \_ AVCSTRM** 作为 REQUEST 参数传递到宏。 接下来，子单位驱动程序将 **AVCStreamContext** 成员设置为流上下文 (处理提供要读取数据的流) 。 最后，子单位驱动程序设置**CommandData**联合的**BufferStruct**成员，该成员描述读取操作将数据放入的缓冲区。

若要发送此请求，子组会 [**将 irp \_ MJ \_ 内部 \_ 设备 \_ 控制**](../kernel/irp-mj-internal-device-control.md) irp，并将 irp 集的 **IoControlCode** 成员提交给 [**IOCTL \_ AVCSTRM \_ 类**](/windows-hardware/drivers/ddi/avcstrm/ni-avcstrm-ioctl_avcstrm_class) ，并将 irp 集的 **Argument1** 成员设置为 AVC \_ 流 \_ 请求 \_ 块结构，该结构描述要执行的读取操作。

此命令以异步方式完成。 完成后，将调用 IRP 中设置的 i/o 完成例程。

必须在 IRQL = 被动级别调用此函数代码 \_ 。

### <a name="see-also"></a>另请参阅

[**AVC \_流 \_ 请求 \_ 块**](/windows-hardware/drivers/ddi/avcstrm/ns-avcstrm-_avc_stream_request_block)， [**INIT \_ AVCSTRM \_ 标头**](/windows-hardware/drivers/ddi/avcstrm/nf-avcstrm-init_avcstrm_header)， [**IRP \_ MJ \_ 内部 \_ 设备 \_ 控制**](../kernel/irp-mj-internal-device-control.md)， [**IOCTL \_ AVCSTRM \_ 类**](/windows-hardware/drivers/ddi/avcstrm/ni-avcstrm-ioctl_avcstrm_class)， [**AVCSTRM \_ BUFFER \_ STRUCT**](/windows-hardware/drivers/ddi/avcstrm/ns-avcstrm-_avcstrm_buffer_struct)， [**AVCSTRM \_ 函数**](/windows-hardware/drivers/ddi/avcstrm/ne-avcstrm-_avcstrm_function)

 

