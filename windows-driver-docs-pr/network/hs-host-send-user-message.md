---
title: HS_HOST_SEND_USER_MESSAGE 函数
description: 调用 HS_HOST_SEND_USER_MESSAGE 函数以便与用户通信。 消息内容包含在传递到热点卸载服务的自定义 UI 显示字符串中。
ms.assetid: c4ab1fda-18eb-44e4-aa64-f7b37b4147a3
keywords:
- typedef DWORD (WINAPI HS_HOST_SEND_USER_MESSAGE 从 Windows Vista 开始) 函数网络驱动程序
ms.date: 07/31/2017
ms.localizationpriority: medium
ms.openlocfilehash: 128d81ef1c9e97df4713defe608143485508516e
ms.sourcegitcommit: 7ca2d3e360a4ae1d4d3c3092bd34492a2645ef74
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89403080"
---
# <a name="hs_host_send_user_message-function"></a>HS \_ 主机 \_ 发送 \_ 用户 \_ 消息函数

[!include[Wi-Fi Hotspot Offloading deprecation](../includes/wi-fi-hotspot-offloading-deprecation.md)]


将调用 **HS \_ HOST \_ SEND \_ 用户 \_ 消息** 函数来与用户通信。 消息内容包含在传递到热点卸载服务的自定义 UI 显示字符串中。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
 typedef DWORD (WINAPI *HS_HOST_SEND_USER_MESSAGE)(
  _In_ HANDLE hPluginContext,
  _In_ DWORD  dwConnectionId,
  _In_ DWORD  dwStringID
);
```

<a name="parameters"></a>参数
----------

*hPluginContext* \[中\]  
调用此函数的插件的上下文句柄。

*dwConnectionId* \[中\]  
网络连接的唯一标识符。

*dwStringID* \[中\]  
字符串 ID，用作存储消息的字符串表中的索引。

<a name="return-value"></a>返回值
------------

此函数由插件调用，以与主机通信并且不返回值。

<a name="remarks"></a>备注
-------

热点插件将消息存储在字符串表中。 插件必须将字符串 Id 传递到热点卸载服务，以使其能够加载相应的字符串。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>版本</p></td>
<td><p>Windows 10 移动版</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Hotspotoffloadplugin (包含 Hotspotoffloadplugin) </td>
</tr>
</tbody>
</table>

 

 




