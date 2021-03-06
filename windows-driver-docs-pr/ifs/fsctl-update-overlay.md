---
title: FSCTL_UPDATE_OVERLAY 控制代码
description: FSCTL \_ UPDATE \_ 叠加控制代码为附加到卷的后备源更新新的数据源标识符。
ms.assetid: 2A420AE7-68CA-4B6A-82D2-C4C39A892F16
keywords:
- FSCTL_UPDATE_OVERLAY 控制代码可安装的文件系统驱动程序
topic_type:
- apiref
api_name:
- FSCTL_UPDATE_OVERLAY
api_location:
- ntifs.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 988572da6e11105cb039a6240a7d7a06c24a2ac8
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89066932"
---
# <a name="fsctl_update_overlay-control-code"></a>FSCTL \_ 更新 \_ 重叠控制代码


**FSCTL \_ UPDATE \_ 叠加**控制代码为附加到卷的后备源更新新的数据源标识符。

若要执行此操作，请调用具有以下参数的 [**FltFsControlFile**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfscontrolfile) 或 [**ZwFsControlFile**](/previous-versions/ff566462(v=vs.85)) 。

**参数**

<a href="" id="instance--in-"></a>*实例 \[\]*  
仅[**FltFsControlFile**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfscontrolfile) 。 调用方的不透明实例指针。 此参数是必需的，不能为 NULL。

<a href="" id="fileobject--in-"></a>*FileObject \[ in\]*  
仅[**FltFsControlFile**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfscontrolfile) 。 覆盖已更新的卷的文件指针对象。 此参数是必需的，不能为 NULL。

<a href="" id="filehandle--in-"></a>*FileHandle \[\]*  
仅[**ZwFsControlFile**](/previous-versions/ff566462(v=vs.85)) 。 覆盖更新的卷的句柄。 此参数是必需的，不能为 NULL。

<a href="" id="fscontrolcode--in-"></a>*FsControlCode \[\]*  
操作的控制代码。 对于此操作，请使用 **FSCTL \_ 更新 \_ 覆盖** 区。

<a href="" id="inputbuffer"></a>*InputBuffer*  
指向输入缓冲区的指针，该缓冲区必须包含 [**WOF \_ 外部 \_ 信息**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_wof_external_info) 结构。 如果需要，其他提供程序特定的数据将立即包含在 **WOF \_ 外部 \_ 信息**之后。 如果提供程序是 WIM 文件，则在**WOF \_ 外部 \_ 信息**后将包含[**wim \_ 提供程序 \_ 更新 \_ 覆盖 \_ 输入**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_wim_provider_update_overlay_input)结构。

<a href="" id="inputbufferlength--in-"></a>*InputBufferLength \[\]*  
设置为 **sizeof** ([**WOF \_ 外部 \_ 信息**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_wof_external_info)) 以及任何其他提供程序输入数据的大小。

<a href="" id="outputbuffer--out-"></a>*OutputBuffer \[\]*  
未使用。 设置为 NULL。

<a href="" id="outputbufferlength--in-"></a>*OutputBufferLength \[\]*  
设置为0。

<a name="status-block"></a>状态块
------------

如果操作成功，则[**FltFsControlFile**](/windows-hardware/drivers/ddi/fltkernel/nf-fltkernel-fltfscontrolfile)或[**ZwFsControlFile**](/previous-versions/ff566462(v=vs.85))返回状态 \_ SUCCESS。 否则，相应的函数可能会返回以下 NTSTATUS 值之一。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">术语</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>STATUS_ACCESS_DENIED</strong></p></td>
<td align="left"><p>请求者没有管理权限。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>STATUS_BUFFER_TOO_SMALL</strong></p></td>
<td align="left"><p><em>InputBuffer</em>（由<em>InputBufferLength</em>指定）指向的输入缓冲区的长度太小。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>STATUS_INTERNAL_ERROR</strong></p></td>
<td align="left"><p>请求的卷不可访问。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>STATUS_INVALID_DEVICE_REQUEST</strong></p></td>
<td align="left"><p>后备服务不存在或未启动。</p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

当要更新的数据源是 (WIM) 文件的 Windows 映像格式时，输入缓冲区将包含 [**WOF \_ 外部 \_ 信息**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_wof_external_info) 结构，后跟 [**wim \_ 提供程序 \_ 更新 \_ 覆盖 \_ 输入**](/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_wim_provider_update_overlay_input) 结构。 在这种情况下， *InputBufferLength* 将为 **sizeof** (WOF \_ 外部 \_ 信息) + **sizeof** (**WIM \_ 提供程序 \_ 更新 \_ 覆盖 \_ 输入**) 。 **Wim \_ 提供程序 \_ 更新 \_ 覆盖 \_ 输入**中的**DataSourceId**值必须为以前添加到[**FSCTL \_ 添加 \_ 覆盖**](fsctl-add-overlay.md)请求中的 WIM 文件。

其他支持提供商将定义自己的特定输入参数结构。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>版本</p></td>
<td align="left"><p>从 Windows 8.1 更新开始可用。</p></td>
</tr>
<tr class="even">
<td align="left"><p>标头</p></td>
<td align="left">Ntifs (包含 Ntifs 或 Fltkernel) </td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**FSCTL \_ 添加 \_ 覆盖区**](fsctl-add-overlay.md)

[**FSCTL \_ 删除 \_ 覆盖**](fsctl-remove-overlay.md)

[**FSCTL \_ 暂停 \_ 覆盖**](fsctl-suspend-overlay.md)

[**FSCTL \_ 获取 \_ 外部 \_ 支持**](fsctl-get-external-backing.md)

[**FSCTL \_ 设置 \_ 外部 \_ 支持**](fsctl-set-external-backing.md)

 

