---
title: 'IrqlMmApcLte 规则 (wdm) '
ms.assetid: 075f5710-b2bf-4546-9648-661a3c8521f8
ms.date: 05/21/2018
description: ''
keywords:
- 'IrqlMmApcLte 规则 (wdm) '
topic_type:
- apiref
api_name:
- IrqlMmApcLte
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 0e18f59525a71128b50820f9bd4ee8a00d39b5fd
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90107468"
---
# <a name="irqlmmapclte-rule-wdm"></a>IrqlMmApcLte 规则 (wdm) 


**IrqlMmApcLte**规则指定仅当驱动程序在 IRQL &lt; = APC 级别执行时才调用以下内存管理器例程 \_ ：

-   [**MmAllocateNonCachedMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmallocatenoncachedmemory)

-   [**MmFreeNonCachedMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmfreenoncachedmemory)

-   [**MmAllocatePagesForMdl**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmallocatepagesformdl)

-   [**MmFreePagesFromMdl**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmfreepagesfrommdl)

-   [**MmLockPagableDataSection**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmlockpagabledatasection)

-   [**MmLockPagableSectionByHandle**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmlockpagablesectionbyhandle)

-   [**MmPageEntireDriver**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmpageentiredriver)

-   [**MmResetDriverPaging**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmresetdriverpaging)

-   [**MmSecureVirtualMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmsecurevirtualmemory)

-   [**MmUnlockPagableImageSection**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmunlockpagableimagesection)

-   [**MmUnsecureVirtualMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmunsecurevirtualmemory)

**驱动程序模型： WDM**

**Bug 检查 () 发现此规则**： [**bug 检查0XC4：驱动程序 \_ 验证器 \_ 检测到 \_ 违反**](../debugger/bug-check-0xc4--driver-verifier-detected-violation.md) (0x00020019) 


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
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](./static-driver-verifier.md)">静态驱动程序验证程序</a> 并指定 <strong>IrqlMmApcLte</strong> 规则。</p>
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

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在运行时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行 <a href="/windows-hardware/drivers/devtest/driver-verifier" data-raw-source="[Driver Verifier](./driver-verifier.md)">驱动程序验证程序</a> ，并选择 " <a href="/windows-hardware/drivers/devtest/ddi-compliance-checking" data-raw-source="[DDI compliance checking](./ddi-compliance-checking.md)">DDI 相容性检查</a> " 选项。</p></td>
</tr>
</tbody>
</table>

 

<a name="applies-to"></a>适用于
----------

[**MmAllocateNonCachedMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmallocatenoncachedmemory) 
[**MmAllocatePagesForMdl**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmallocatepagesformdl) 
[**MmAllocatePagesForMdlEx**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmallocatepagesformdlex) 
[**MmFreeNonCachedMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmfreenoncachedmemory) 
[**MmFreePagesFromMdl**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmfreepagesfrommdl) 
[**MmLockPagableDataSection**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmlockpagabledatasection) 
[**MmLockPagableSectionByHandle**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmlockpagablesectionbyhandle) 
[**MmPageEntireDriver**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmpageentiredriver) 
[**MmResetDriverPaging**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmresetdriverpaging) 
[**MmSecureVirtualMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmsecurevirtualmemory) 
[**MmUnlockPagableImageSection**](/windows-hardware/drivers/ddi/wdm/nf-wdm-mmunlockpagableimagesection) 
[**MmUnsecureVirtualMemory**](/windows-hardware/drivers/ddi/ntddk/nf-ntddk-mmunsecurevirtualmemory)
