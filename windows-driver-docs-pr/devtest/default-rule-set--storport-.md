---
title: 默认规则集 (Storport)
description: 默认 (规则集) 指定在分析驱动程序时要使用的建议的规则集。
ms.assetid: 8310E393-4CA7-4701-8BBC-6E758C927FBE
ms.date: 05/21/2018
ms.localizationpriority: medium
ms.openlocfilehash: 3355ae362947d369d0a3a052a56651859e87b2fa
ms.sourcegitcommit: faff37814159ad224080205ad314cabf412e269f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89384121"
---
# <a name="default-rule-set-storport"></a>默认规则集 (Storport)


默认 (规则集) 指定在分析驱动程序时要使用的建议的规则集。

) Storport (的[DDI 使用情况规则集](ddi-usage-rule-set--storport-.md) 
[Irql 规则集 (Storport) ](irql-rule-set--storport-.md) 
[锁定规则集 (Storport) ](locking-rule-set--storport-.md) 
[SrbProcessing) ](srbprocessing-rule-set--storport-.md) 
 (Storport 的规则集[VirtualStorport) ](virtualstorport-rule-set--storport-.md) 
 (Storport 的规则集**选择默认规则**

1.  选择你的驱动程序项目 () 在 Microsoft Visual Studio 中。 在 " **驱动程序** " 菜单中，单击 " **启动静态驱动程序验证程序 ...**"。

2.  单击 " **规则** " 选项卡。在 " **规则集**" 下，选择 " **默认**"。

    若要从 Visual Studio 开发人员命令提示符窗口中选择默认规则集，请使用 **/check**选项指定**sdv** 。 例如：

    ```
    msbuild /t:sdv /p:Inputs="/check:Default.sdv" mydriver.VcxProj /p:Configuration="Win8 Release" /p:Platform=Win32
    ```

    有关详细信息，请参阅 [使用静态驱动程序验证器查找驱动程序中的缺陷](./using-static-driver-verifier-to-find-defects-in-drivers.md) 和 [静态驱动程序验证程序命令 (MSBuild) ](./-static-driver-verifier-commands--msbuild-.md)。

 

