---
title: ELAM 先决条件
description: 开机初期启动的反恶意软件驱动程序必须遵守以下程序要求：由 WHQL 签名并由 Windows 加载。
ms.assetid: 48759EB3-F8F9-4881-BD30-6D1252F08DFE
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 94a113bc99a28bb3cb925d15fec751ea7ea884cb
ms.sourcegitcommit: 4db5f9874907c405c59aaad7bcc28c7ba8280150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "89096061"
---
# <a name="elam-prerequisites"></a>ELAM 先决条件


开机初期启动的反恶意软件驱动程序必须遵守以下程序要求：由 **WHQL** 签名并由 Windows 加载。

## <a name="antimalware-vendor-participation-requirements"></a>反恶意软件供应商参与要求


Microsoft 要求及早启动反恶意软件供应商是 **[ (MVI) 的 Microsoft 病毒计划 ](/windows/security/threat-protection/intelligence/virus-initiative-criteria)** 的成员。 此成员身份确保供应商处于活跃的反恶意软件社区参与者，具有良好的行业声誉。 如果你不是 MVI 计划的成员并且认为你需要使用 ELAM，请访问以 **[mvi@microsoft.com](mailto:mvi@microsoft.com)** 获取其他信息。


## <a name="windows-hardware-quality-lab-whql-submission"></a>Windows 硬件质量实验室 (WHQL) 提交

-   提交用于验证的驱动程序，如[ELAM 驱动程序提交](elam-driver-submission.md)中所述
-   **WHQL**过程将验证供应商是否允许提交早期启动驱动程序。  如果你不是 MVI 成员或预先批准的 VIA 成员，你的提交将会失败。