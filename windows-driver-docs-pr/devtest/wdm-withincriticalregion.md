---
title: 'WithinCriticalRegion 规则 (wdm) '
description: WithinCriticalRegion 规则指定仅在调用 KeEnterCriticalRegion 之后和调用 KeLeaveCriticalRegion 之前，对特定同步函数的调用才会出现。
ms.assetid: 9b74b868-6025-4e81-b5ba-21e0da734cd9
ms.date: 05/21/2018
keywords:
- 'WithinCriticalRegion 规则 (wdm) '
topic_type:
- apiref
api_name:
- WithinCriticalRegion
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 240e8a35f161835d852c6adb7e859e592c81f2b9
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90106122"
---
# <a name="withincriticalregion-rule-wdm"></a>WithinCriticalRegion 规则 (wdm) 


**WithinCriticalRegion**规则指定仅在调用[**KeEnterCriticalRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keentercriticalregion)之后和调用[**KeLeaveCriticalRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keleavecriticalregion)之前，对特定同步函数的调用才会出现。

受影响的同步函数如下所示：

-   [**ExAcquireResourceSharedLite**](/previous-versions/ff544363(v=vs.85))

-   [**ExAcquireResourceExclusiveLite**](/previous-versions/ff544351(v=vs.85))

-   [**ExAcquireSharedStarveExclusive**](/previous-versions/ff544367(v=vs.85))

-   [**ExAcquireSharedWaitForExclusive**](/previous-versions/ff544370(v=vs.85))

-   [**ExReleaseResourceLite**](/windows-hardware/drivers/ddi/wdm/nf-wdm-exreleaseresourcelite)

-   [**ExReleaseResourceForThreadLite**](/previous-versions/ff545585(v=vs.85))

此规则不能识别禁用正常 APC 传递的其他方法。 有关详细信息，请参阅 [**禁用 apc**](../kernel/disabling-apcs.md)。

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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>WithinCriticalRegion</strong> 规则。</p>
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

[**ExAcquireResourceExclusiveLite**](/previous-versions/ff544351(v=vs.85)) 
[**ExAcquireResourceSharedLite**](/previous-versions/ff544363(v=vs.85)) 
[**ExAcquireSharedStarveExclusive**](/previous-versions/ff544367(v=vs.85)) 
[**ExAcquireSharedWaitForExclusive**](/previous-versions/ff544370(v=vs.85)) 
[**ExReleaseResourceForThreadLite**](/previous-versions/ff545585(v=vs.85)) 
[**ExReleaseResourceLite**](/windows-hardware/drivers/ddi/wdm/nf-wdm-exreleaseresourcelite) 
[**KeEnterCriticalRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keentercriticalregion) 
[**KeEnterGuardedRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keenterguardedregion) 
[**KeLeaveCriticalRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keleavecriticalregion) 
[**KeLeaveGuardedRegion**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-keleaveguardedregion)另请参阅
--------

[**管理硬件优先级**](../kernel/managing-hardware-priorities.md) 
[**使用自旋锁时防止错误和死锁**](../kernel/preventing-errors-and-deadlocks-while-using-spin-locks.md)
