---
title: 创建分配时指定段
description: 创建分配时指定段
ms.assetid: 31bfbfd9-89e5-42fe-90bc-8ff54bac4f8b
keywords:
- 内存段 WDK 显示，分配创建
- 分配 WDK 显示
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5be16efd6dd42273ba678906d62d56378cd98104
ms.sourcegitcommit: 7b9c3ba12b05bbf78275395bbe3a287d2c31bcf4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2020
ms.locfileid: "89066592"
---
# <a name="specifying-segments-when-creating-allocations"></a>创建分配时指定段


## <span id="ddk_specifying_segments_for_creating_and_rendering_allocations_gg"></span><span id="DDK_SPECIFYING_SEGMENTS_FOR_CREATING_AND_RENDERING_ALLOCATIONS_GG"></span>


显示微型端口驱动程序指定并返回在视频内存管理器调用驱动程序的 [**DxgkDdiCreateAllocation**](/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_createallocation) 函数时，它更倾向于视频内存管理器使用的内存段的相关信息。 在对 *DxgkDdiCreateAllocation*的调用中，驱动程序将创建视频资源的分配。 驱动程序在描述分配的 [**DXGK \_ ALLOCATIONINFO**](/windows-hardware/drivers/ddi/d3dkmddi/ns-d3dkmddi-_dxgk_allocationinfo) 结构中返回支持的段和段首选项的标识符。

在返回的段信息中，视频内存管理器会确定要为给定操作分页的内存段。

 

