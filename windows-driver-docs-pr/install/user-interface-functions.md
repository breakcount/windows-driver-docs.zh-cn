---
title: 用户界面函数
description: 用户界面函数
ms.assetid: 30ec0628-cac7-46ab-a9f2-c81ca3ad7125
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 6a366cd9e09620c518affff9e724f9c2f56831ff
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90714882"
---
# <a name="user-interface-functions"></a>用户界面函数


你可以在类安装程序和共同安装程序中使用以下常规安装函数来确定当前进程是否可以与用户交互。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">函数</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="/windows/win32/api/setupapi/nf-setupapi-setupgetnoninteractivemode" data-raw-source="[&lt;strong&gt;SetupGetNonInteractiveMode&lt;/strong&gt;](/windows/win32/api/setupapi/nf-setupapi-setupgetnoninteractivemode)"><strong>SetupGetNonInteractiveMode</strong></a></p></td>
<td align="left"><p>返回 Setupapi.log 非交互式标志的值，该值指示调用方的进程是否可以通过用户界面组件（如对话框）与用户交互。</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="/windows/win32/api/setupapi/nf-setupapi-setupsetnoninteractivemode" data-raw-source="[&lt;strong&gt;SetupSetNonInteractiveMode&lt;/strong&gt;](/windows/win32/api/setupapi/nf-setupapi-setupsetnoninteractivemode)"><strong>SetupSetNonInteractiveMode</strong></a></p></td>
<td align="left"><p>设置非交互式 Setupapi.log 标志，该标志确定 Setupapi.log 是否可以与用户在调用方的上下文中交互。</p></td>
</tr>
</tbody>
</table>

 

