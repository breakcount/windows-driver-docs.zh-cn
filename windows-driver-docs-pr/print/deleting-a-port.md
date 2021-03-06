---
title: 删除端口
description: 删除端口
ms.assetid: 0d491368-e529-4f04-a323-678e31a862c3
keywords:
- 端口管理 WDK 打印，删除端口
- 删除打印端口
- 删除打印端口
- DeletePort
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 88e100d03883d0c66c184058da59499a7c41fedf
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89216378"
---
# <a name="deleting-a-port"></a>删除端口





删除端口包括从端口监视器服务器 DLL 的本地存储或注册表中删除端口的存储名称和用户可修改的配置信息。

当应用程序调用打印后台处理程序的 **DeletePort** 函数时 (Microsoft Windows SDK 文档) 中所述， **DeletePort** 函数会调用相应端口监视器的端口监视器 UI DLL 中包含的 [**DeletePortUI**](/windows-hardware/drivers/ddi/winsplp/nf-winsplp-deleteportui) 函数。

端口监视器 UI DLL 的 **DeletePortUI** 函数应执行以下操作：

1.  调用打印后台处理程序的 **OpenPrinter** 函数 (Windows SDK 文档) 中所述，这将导致调用端口监视器服务器 DLL 中的 [**XcvOpenPort**](/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvopenport) 函数。

2.  一次或多次调用打印后台处理程序的 [**XcvData**](/previous-versions/ff564255(v=vs.85)) 函数，请求端口监视器服务器 DLL 删除该端口。 **XcvData**函数调用服务器 DLL 的[**XcvDataPort**](/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvdataport)函数。

3.  调用打印后台处理程序的 **ClosePrinter** 函数 (Windows SDK 文档) 中所述，这将导致调用端口监视器服务器 DLL 中的 [**XcvClosePort**](/windows-hardware/drivers/ddi/winsplp/nf-winsplp-xcvcloseport) 函数。

有关这些操作的详细信息，请参阅 [**DeletePortUI**](/windows-hardware/drivers/ddi/winsplp/nf-winsplp-deleteportui)的说明。

 

