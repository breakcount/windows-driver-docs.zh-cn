---
title: 'RemoveLockMnRemove2 规则 (wdm) '
description: RemoveLockMnRemove2 规则验证在将 \_ \_ \_ irp 转发到较低的驱动程序之前，在处理 irp MN 删除设备请求之前，是否正确地使用了对 IoAcquireRemoveLock 和 IoReleaseRemoveLockAndWait 的调用。
ms.assetid: 69CCB0CB-86E0-4994-AC3E-44A4B9993EBC
ms.date: 05/21/2018
keywords:
- 'RemoveLockMnRemove2 规则 (wdm) '
topic_type:
- apiref
api_name:
- RemoveLockMnRemove2
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 733964a9446ad501711913ba28fdf2922644efbf
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90104302"
---
# <a name="removelockmnremove2-rule-wdm"></a>RemoveLockMnRemove2 规则 (wdm) 


**RemoveLockMnRemove2**规则验证在将[**IoAcquireRemoveLock**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioacquireremovelock) [**IoReleaseRemoveLockAndWait**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreleaseremovelockandwait) \_ \_ \_ irp 转发到较低的驱动程序之前，在处理 irp MN 删除设备请求之前，是否正确地使用了对 IoAcquireRemoveLock 和 IoReleaseRemoveLockAndWait 的调用。

此规则仅适用于 FDO 和 FIDO 驱动程序。

例如，请考虑包含筛选器驱动程序、FDO 和 PDO 的 PnP 驱动程序堆栈。

PnP 管理器通过堆栈发送查询删除。 当系统正在运行时，FDO 已启用为空闲状态。 FDO 决定在查询删除状态下断电，因此它请求 d0 IRP。 在 d0 IRP 到达之前，PnP 管理器将发送 PnP 删除 IRP，并由筛选器驱动程序处理 IRP。 筛选器驱动程序与堆栈分离并清除其状态。 D0 到达堆栈顶部，但筛选器驱动程序不会将其发送到堆栈中，因为它没有上下文或数据来知道要将其发送到的位置。 FDO 挂起等待 d0 IRP 到达，但 IRP 永远不会。

**若要避免此错误**

1.  在设备从设备堆栈分离之前， [**IoAcquireRemoveLock**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioacquireremovelock) 必须在将 irp 转发到以下 irp 类型的堆栈之前成功：

    -   IRP \_ MN \_ 查询 \_ 删除
    -   IRP \_ MN \_ SUPRISE \_ 删除
    -   IRP \_ MN \_ 删除 \_ 设备

2.  调用[**IoDetachDevice**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iodetachdevice)或[**IoDeleteDevice**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iodeletedevice)之前应调用[**IoReleaseRemoveLockAndWait**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreleaseremovelockandwait) 。  (这可确保在设备驱动程序) 中释放所有删除锁。

**驱动程序模型： WDM**

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>RemoveLockMnRemove2</strong> 规则。</p>
使用以下步骤来运行代码分析：
<ol>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](./using-static-driver-verifier-to-find-defects-in-drivers.md#preparing-your-source-code)">准备你的代码 (使用) 的角色类型声明。</a></li>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](./using-static-driver-verifier-to-find-defects-in-drivers.md#running-static-driver-verifier)">运行静态驱动程序验证程序。</a></li>
<li><a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](./using-static-driver-verifier-to-find-defects-in-drivers.md#viewing-and-analyzing-the-results)">查看并分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅 <a href="/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](./using-static-driver-verifier-to-find-defects-in-drivers.md)">使用静态驱动程序验证器查找驱动程序中的缺陷</a>。</p></td>
</tr>
</tbody>
</table>

<a name="applies-to"></a>适用于
----------

[**IoAcquireRemoveLock**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioacquireremovelock) 
[**IoCallDriver**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iocalldriver) 
[**IoReleaseRemoveLock**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreleaseremovelock) 
[**IoReleaseRemoveLockAndWait**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioreleaseremovelockandwait) 
[**PoCallDriver**](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-pocalldriver)
