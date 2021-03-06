---
title: 'MarkPowerDown 规则 (wdm) '
description: MarkPowerDown 规则指定 IRP \_ MJ \_ 使用 irp \_ MN \_ \_ 为 SystemPowerState IRP 设置 power for IRP 从 s0 到 \ S1 .。。S5 \ 挂起。
ms.assetid: 5C35F607-1550-4B48-8325-8A01D522786F
ms.date: 05/21/2018
keywords:
- 'MarkPowerDown 规则 (wdm) '
topic_type:
- apiref
api_name:
- MarkPowerDown
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 62af0289f9325c307b580a5d625c47af962047d6
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90103072"
---
# <a name="markpowerdown-rule-wdm"></a>MarkPowerDown 规则 (wdm) 


**MarkPowerDown**规则指定 irp \_ MJ \_ 使用 irp \_ MN \_ \_ 为 SystemPowerState IRP 设置 power for **SystemPowerState** IRP 从 s0 到 \[ S1 .。。S5 \] 挂起。

此规则仅适用于 FDO 和 FIDO 驱动程序。

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>MarkPowerDown</strong> 规则。</p>
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
[**IoAllocateIrp**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioallocateirp) 
[**IoCallDriver**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iocalldriver) 
[**IoGetDeviceInterfaces**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iogetdeviceinterfaces) 
[**也**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iomarkirppending) 
[**IoRegisterPlugPlayNotification**](/windows-hardware/drivers/ddi/wdm/nf-wdm-ioregisterplugplaynotification) 
[**IoSetCompletionRoutine**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iosetcompletionroutine) 
[**IoSetCompletionRoutineEx**](/windows-hardware/drivers/ddi/wdm/nf-wdm-iosetcompletionroutineex) 
[**PoCallDriver**](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-pocalldriver)
