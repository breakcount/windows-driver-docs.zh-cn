---
title: 加载亮显数据
description: 加载亮显数据
ms.assetid: d893fdbe-847d-45a7-b2b2-62da505c8aeb
keywords:
- alpha-blend 数据加载 WDK DirectX VA
- 混合图片 WDK DirectX VA，alpha-blend 数据加载
- 突出显示的矩形区域 WDK DirectX VA
- 矩形突出显示区域 WDK DirectX VA
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 4862fafbbb2c0f1d2b340bdba1cd01ac1704de18
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89065784"
---
# <a name="loading-highlight-data"></a>加载亮显数据


## <span id="ddk_loading_highlight_data_gg"></span><span id="DDK_LOADING_HIGHLIGHT_DATA_GG"></span>


[**DXVA \_ 高光**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_highlight)结构指定了子画面的突出显示的矩形区域，并与 DCCMD 数据和 DPXD 图面一起用于创建 alpha 混合图面。 突出显示数据的格式是与 DVD ROM 规范兼容的方式。 有关 DVD 子画面定义和数据字段解释的详细说明，请参阅 *只读磁盘的 DVD 规范：第3部分-视频规范 (1.11，1999) *。

 

