---
title: 编写设备安装应用程序
description: 编写设备安装应用程序
ms.assetid: 9927e2e0-6c8e-437f-98ce-595bd304ec72
keywords:
- 安装应用程序 WDK，有关编写安装应用程序的信息
- 设备安装应用程序 WDK，有关编写安装应用程序的信息
- 设备设置 WDK 设备安装，编写安装应用程序
- 安装设备 WDK，编写安装应用程序
- 编写设备安装应用程序
- 安装应用程序 WDK
- 设备安装应用程序 WDK
- 应用程序 WDK 设备安装
- 设备安装 WDK，应用程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: cf73c8f67b07491e842ecfc6be06fed843e062d3
ms.sourcegitcommit: 4db5f9874907c405c59aaad7bcc28c7ba8280150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2020
ms.locfileid: "89097065"
---
# <a name="writing-a-device-installation-application"></a>编写设备安装应用程序





**注意**   通用或移动驱动程序包不支持本部分中介绍的功能。 请参阅 [使用通用 INF 文件](using-a-universal-inf-file.md)。

 

如果安装了这些组件的驱动程序包。 设备安装应用程序和分发媒体应该与自动运行兼容，因此当用户插入分发媒体时，自动运行自动启动应用程序。 有关自动运行的详细信息，请参阅 [创建启用自动激活的应用程序](/previous-versions/windows/desktop/legacy/cc144206(v=vs.85))。

有关如何编写设备安装应用程序的指南，请参阅 [编写设备安装应用程序的指南](guidelines-for-writing-device-installation-applications.md)。

[驱动程序包](driver-packages.md)必须处理两种情况：

1.  用户在插入分发媒体之前插入到你的硬件中。 这通常称为 [硬件第一次安装](hardware-first-installation.md)。

2.  用户在插入你的硬件之前插入你的分发媒介。 这通常称为 [软件优先安装](software-first-installation.md)。

 

