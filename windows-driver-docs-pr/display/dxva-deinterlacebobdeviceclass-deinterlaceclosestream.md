---
title: DeinterlaceCloseStream 方法
description: 示例 DXVA \_ DeinterlaceBobDeviceClass：:D einterlaceclosestream 函数关闭取消隔行扫描流对象，并指示设备驱动程序释放与该流关联的任何硬件资源。
ms.assetid: 89131951-7d79-4236-9d9f-51382d63baa9
keywords:
- DeinterlaceCloseStream 方法显示设备
- DeinterlaceCloseStream 方法显示设备，DXVA_DeinterlaceBobDeviceClass 接口
- DXVA_DeinterlaceBobDeviceClass 接口显示设备，DeinterlaceCloseStream 方法
topic_type:
- apiref
api_name:
- DXVA_DeinterlaceBobDeviceClass.DeinterlaceCloseStream
api_type:
- COM
ms.date: 12/06/2018
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: d87c4d7e8e84eea0c696aaeb81d25a86de4e87c8
ms.sourcegitcommit: b84d760d4b45795be12e625db1d5a4167dc2c9ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90717370"
---
# <a name="dxva_deinterlacebobdeviceclassdeinterlaceclosestream-method"></a>DXVA \_ DeinterlaceBobDeviceClass：:D einterlaceclosestream 方法


示例 *DeinterlaceCloseStream* 函数关闭取消隔行扫描流对象，并指示设备驱动程序释放与该流关联的任何硬件资源。

<a name="syntax"></a>语法
------

```cpp
HRESULT DeinterlaceCloseStream();
```

<a name="parameters"></a>参数
----------

此方法没有任何参数。

<a name="return-value"></a>返回值
------------

如果成功，则返回零 (S \_ 正常或 DD \_ 确定) ; 否则返回错误代码。 有关错误代码的完整列表，请参阅*ddraw。*

<a name="remarks"></a>备注
-------

*DeinterlaceCloseStream*函数直接映射到[**DD \_ MOTIONCOMPCALLBACKS**](/windows/win32/api/ddrawint/ns-ddrawint-dd_motioncompcallbacks)结构的**DestroyMoComp**成员，该成员指向驱动程序提供的*DdMoCompDestroy*回调。

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**DD \_ MOTIONCOMPCALLBACKS**](/windows/win32/api/ddrawint/ns-ddrawint-dd_motioncompcallbacks)

[**DeinterlaceOpenStream**](dxva-deinterlacebobdeviceclass-deinterlaceopenstream.md)

 

