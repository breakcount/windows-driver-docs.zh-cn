---
title: 绘制线条和曲线
description: 绘制线条和曲线
ms.assetid: 0816fb69-7811-4319-b050-00ded21a10d4
keywords:
- 线条 WDK GDI
- GDI WDK Windows 2000 显示，行
- 图形驱动程序 WDK Windows 2000 显示，行
- 绘制 WDK GDI，行
- GDI WDK Windows 2000 显示，曲线
- 图形驱动程序 WDK Windows 2000 显示，曲线
- 绘制 WDK GDI，曲线
- 画笔 WDK GDI
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b462260ecce541e052e0aac4c7030868886a3188
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90717376"
---
# <a name="drawing-lines-and-curves"></a>绘制线条和曲线


## <span id="ddk_drawing_lines_and_curves_gg"></span><span id="DDK_DRAWING_LINES_AND_CURVES_GG"></span>


图形输出中包含的线条和曲线的类型为 [几何线条](geometric-wide-lines.md)、 [修饰线](cosmetic-lines.md)和 [贝塞尔曲线](bezier-curves.md)。

对于线条和曲线输出，驱动程序可支持 [**DrvStrokePath**](/windows/win32/api/winddi/nf-winddi-drvstrokepath)、 [**DrvFillPath**](/windows/win32/api/winddi/nf-winddi-drvfillpath)和 [**DrvStrokeAndFillPath**](/windows/win32/api/winddi/nf-winddi-drvstrokeandfillpath) 函数。 如果图面是设备托管的，则驱动程序必须支持用于绘制线条的 **DrvStrokePath** ;支持曲线不需要驱动程序。

当 GDI 使用任意一组属性绘制线条或曲线时，GDI 可以调用 [**DrvStrokePath**](/windows/win32/api/winddi/nf-winddi-drvstrokepath)。 **DrvStrokePath**函数至少必须支持使用纯色画笔和任意剪裁来绘制纯色和样式修饰线条。 GDI PATHOBJ \_ *XXX*和 CLIPOBJ \_ *Xxx*服务函数可将这些行划分为一个像素范围内具有预计算剪辑的一组行，从而实现此功能。 **DrvStrokePath**向[**LINEATTRS**](/windows/win32/api/winddi/ns-winddi-_lineattrs)结构提供指针**plineattrs**，用于定义各种线条属性。

如果路径或剪辑太复杂，驱动程序在设备上进行处理，则驱动程序可以通过调用 [**EngStrokePath**](/windows/win32/api/winddi/nf-winddi-engstrokepath) 函数来发出对 GDI 的回调。 在这种情况下，GDI 可以将 [**DrvStrokePath**](/windows/win32/api/winddi/nf-winddi-drvstrokepath) 调用分成一组使用预计算剪裁的像素宽的行。

通过从 GDI 调用 CLIPOBJ \_ *Xxx*服务，驱动程序可以对路径中的所有行进行 gdi 枚举，并执行所有的行剪辑计算。 此外，驱动程序可以使用 PATHOBJ \_ *xxx*、CLIPOBJ \_ *xxx*或 XFORMOBJ \_ *Xxx*服务来简化图形操作。 例如，驱动程序可以使用 **CLIPOBJ \_ cEnumStart**，将此区域向下发送到打印机，然后剪辑到该打印机。 驱动程序还可以使用 [**PATHOBJ \_ VEnumStart**](/windows/win32/api/winddi/nf-winddi-pathobj_venumstart) 和 [**PATHOBJ \_ bEnum**](/windows/win32/api/winddi/nf-winddi-pathobj_benum) 来枚举路径中的直线或曲线。 然后，它可以将路径发送到设备，并对其进行描边。

 

