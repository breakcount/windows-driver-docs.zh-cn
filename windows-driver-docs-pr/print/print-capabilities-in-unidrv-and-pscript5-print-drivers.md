---
title: Unidrv 和 PScript5 打印驱动程序中的打印功能
description: Unidrv 和 PScript5 打印驱动程序中的打印功能
ms.assetid: 70f8b846-3e05-4345-baad-a3db6b8df620
keywords:
- 打印功能 WDK，Unidrv
- 打印功能 WDK，PScript5
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8574303fbef773330d41e088f76100ecff174f9c
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89214218"
---
# <a name="print-capabilities-in-unidrv-and-pscript5-print-drivers"></a>Unidrv 和 PScript5 打印驱动程序中的打印功能


Unidrv 和 PScript5 微型驱动程序提供支持打印功能功能所需的打印票证和打印功能接口。 这些打印驱动程序针对 [一般打印机说明 (GPD) 文件](introduction-to-gpd-files.md) 或 PostScript 打印机说明 (PPD) 文件中所述的功能提供了打印票证和打印功能，这些功能是否适用于 [**DEVMODEW**](/windows/win32/api/wingdi/ns-wingdi-devmodew) 结构的公共或私有部分。

[XPSDrv 打印驱动程序](xpsdrv-printer-drivers.md) 还可以使用 Unidrv 打印机配置 DLL 为基于 GDI 的打印机配置接口和 [IPrintTicketProvider 接口](/previous-versions/windows/hardware/drivers/ff554375(v=vs.85))提供所需的支持。 如果使用 Unidrv 配置 DLL，则可以加速为基本功能打印机或直通打印驱动程序开发 XPSDrv 打印机驱动程序。

 

