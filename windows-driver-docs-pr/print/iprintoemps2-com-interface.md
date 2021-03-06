---
title: IPrintOemPS2 COM 接口
description: IPrintOemPS2 COM 接口
ms.assetid: 6743d73e-243b-4a05-8e88-576c65b37a19
keywords:
- IPrintOemPS2
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 39748fe5dee92badf605679f316216e16b31ce6d
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90105868"
---
# <a name="iprintoemps2-com-interface"></a>IPrintOemPS2 COM 接口





`IPrintOemPS2`Com 接口包含的所有方法，并扩展了[IPrintOemPS COM 接口](iprintoemps-com-interface.md)的功能。 此接口仅限于在 Windows XP 和更高版本的 Windows 操作系统上运行的 Pscript5 呈现插件。

下表列出并描述了接口提供的所有方法 `IPrintOemPS2` 。 呈现插件必须定义所有列出的方法。 如果方法不是必需的，则可以只返回 E \_ NOTIMPL。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方法</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps2-getpdevadjustment" data-raw-source="[&lt;strong&gt;IPrintOemPS2::GetPDEVAdjustment&lt;/strong&gt;](/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps2-getpdevadjustment)"><strong>IPrintOemPS2::GetPDEVAdjustment</strong></a></p></td>
<td><p>使插件能够重写特定的 PDEV 设置。</p></td>
</tr>
<tr class="even">
<td><p><a href="/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps2-writeprinter" data-raw-source="[&lt;strong&gt;IPrintOemPS2::WritePrinter&lt;/strong&gt;](/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemps2-writeprinter)"><strong>IPrintOemPS2::WritePrinter</strong></a></p></td>
<td><p>允许插件捕获由 Postscript 驱动程序生成的所有输出数据。</p></td>
</tr>
</tbody>
</table>

 

有关详细信息，请参阅 [实现打印机驱动程序 COM 接口](implementing-printer-driver-com-interfaces.md)。

