---
title: BGRA 扫描输出支持
description: BGRA 扫描输出支持
ms.assetid: 88ef5de7-59cc-4a8a-aaf7-74489a7ac0ab
keywords:
- Direct3D 版本 10.1 WDK Windows 7 显示，BGRA 扫描支持
- BGRA 扫描支持 WDK Windows 7 显示
- 扫描支持 WDK Windows 7 显示
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: ad58c77fb1a32ee2676c8b76b4e374788a5e8cf6
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89067478"
---
# <a name="bgra-scan-out-support"></a>BGRA 扫描输出支持


本部分仅适用于 Windows 7 及更高版本的操作系统。

为 DXGI \_ 格式 \_ B8G8R8A8 \_ UNORM 和 dxgi \_ format \_ B8G8R8A8 \_ UNORM \_ SRGB 格式启用了扫描位。 因此，用户模式显示驱动程序应该能够执行以下操作：

-   处理采用这些格式的主表面的请求。

-   对于用这些格式创建的资源，处理其 [**SetDisplayMode**](/windows-hardware/drivers/ddi/d3dumddi/nc-d3dumddi-pfnd3dddi_setdisplaymode) 函数的调用。

-   处理对其 [**PresentDXGI**](/windows-hardware/drivers/ddi/dxgiddi/ns-dxgiddi-dxgi_ddi_base_functions) 函数的调用，以通过两个位块传输 (bitblt) 和翻转操作来显示这些格式。

-   处理对其 [**BltDXGI**](/windows-hardware/drivers/ddi/dxgiddi/ns-dxgiddi-dxgi_ddi_base_functions) 函数的调用，通过拉伸、旋转和解析 (来复制这些格式，这种情况下，RGBA 变体所需的所有 bitblt 操作都) 。

 

