---
title: 超出了 ESRT 的固件最大重试限制的计算机百分比
description: 该度量将 28 天滑动窗口中的遥测数据聚合为达到最大重试限制的计算机数与出现安装事件的计算机数的比率
ms.topic: article
ms.date: 10/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 6237c6588fb2112de1831f0f5a52d8efc320007d
ms.sourcegitcommit: c214e65a7f5dd868037718a34ca7cc80584df5c6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2020
ms.locfileid: "89615485"
---
# <a name="percent-of-machines-exceeded-firmware-max-retry-limit-from-esrt"></a>超出了 ESRT 的固件最大重试限制的计算机百分比

## <a name="description"></a>说明

尝试安装固件成功但超出固件最大重试限制（默认为 3 次）的计算机的百分比。

该度量将 28 天滑动窗口中的遥测数据聚合为达到最大重试限制的计算机数与出现安装事件的计算机数的比率。

许多未达到对此度量的要求的固件未遵守以下协定：当报告的 ESRT 版本与安装之前计算机上的以前版本相同时，ESRT LastAttemptStatus 字段不报告故障代码。 

[本文档的第 3 部分](/windows-hardware/manufacture/desktop/validating-windows-uefi-firmware-update-platform-functionality)提供基本验证方案，以确保固件实现满足此要求。  

## <a name="measure-attributes"></a>度量属性

|属性|值|
|----|----|
|受众 |零售和预览体验成员|
|时间段 |28 天滑动窗口|
|度量标准 |计算机的聚合|
|最小实例数 |200|
|通过标准 |<= 5%|
|度量 ID |20116755 或 23260704|

## <a name="calculation"></a>计算

安装了固件但达到最大重试限制的计算机数/

收到了固件设备的驱动程序安装事件的计算机数