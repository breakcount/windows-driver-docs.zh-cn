---
title: 贝塞尔曲线
description: 贝塞尔曲线
ms.assetid: 322ff79b-e5b8-4247-99eb-1aa3779216ef
keywords:
- GDI WDK Windows 2000 显示器、曲线、贝塞尔
- 图形驱动程序 WDK Windows 2000 显示器、曲线、贝塞尔
- 绘制 WDK GDI、曲线、贝塞尔
- 三次曲线 WDK GDI
- 贝塞尔曲线 WDK GDI
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f0f1a79cc58ff1abc8543794acdb5e95196843b4
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90715374"
---
# <a name="bezier-curves"></a>贝塞尔曲线


## <span id="ddk_bezier_curves_gg"></span><span id="DDK_BEZIER_CURVES_GG"></span>


某些高级硬件设备可以绘制包含贝塞尔曲线 (三次曲线的路径，) ，这是一般用途的曲线基元。 如果是这样，则驱动程序可以将对这些曲线的支持包含在 [**DrvStrokePath**](/windows/win32/api/winddi/nf-winddi-drvstrokepath) 函数中。

当 GDI 必须在设备管理的图面上绘制贝塞尔曲线路径时，它将 \_ 在 [**lnk-devinfo**](/windows/win32/api/winddi/ns-winddi-tagdevinfo) 结构) 中测试 GCAPS 贝塞尔标志 (，以确定它是否应调用 [**DrvStrokePath**](/windows/win32/api/winddi/nf-winddi-drvstrokepath)。 如果调用此函数，则执行所请求的操作或决定不处理它，就像它处理几何宽线一样。 在后一种情况下，GDI 将请求分解为更简单的操作，例如，通过将曲线转换为线条近似值。

 

