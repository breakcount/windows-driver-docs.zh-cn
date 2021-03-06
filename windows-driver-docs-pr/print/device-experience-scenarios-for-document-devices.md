---
title: 文档设备的设备体验方案
description: 文档设备的设备体验方案
ms.assetid: 8e01e9d7-5017-4e0a-90b8-4a025e25a60b
ms.date: 01/30/2019
ms.localizationpriority: medium
ms.openlocfilehash: ab6df8bde9cc24a65904e6913b8b318c7ec291c3
ms.sourcegitcommit: 7cc49bb40a3ccf74af333e32955e4f31f4fc1f6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69529753"
---
# <a name="device-experience-scenarios-for-document-devices"></a>文档设备的设备体验方案

"设备和打印机" 文件夹显示连接到计算机的设备, 包括文档设备。

以下屏幕截图显示了典型的设备和打印机文件夹。

![典型设备和打印机文件夹](images/devicestage002.png)

在 "设备和打印机" 中选择设备时, "设备阶段" 会显示该设备的详细信息。 以下屏幕截图显示设备阶段。 

![Device Stage](images/devicestage003.png)

## <a name="document-devices-in-devices-and-printers"></a>设备和打印机中的文档设备

"设备和打印机" 文件夹包含以下各项:

- 本地连接的打印机
- 通过 TCP/IP 连接的联网打印机
- 指向和打印连接
- 连接了 HTTP 的打印机
- 通过远程桌面连接工具重定向的打印机连接
- 虚拟打印机 (包括 Microsoft 共享传真和 Microsoft XPS 文档编写器)

使用 Windows 映像获取 (WIA) 驱动程序安装的所有扫描仪都显示在 "设备和打印机" 视图中。 此视图中仅显示即插即用或 Pnp-x 连接的扫描仪。

通过即插即用或 Pnp-x 连接到计算机的多功能打印机 (MFPs) 将以单个复合设备的形式显示在 "设备和打印机" 视图中, 而不是作为单独的打印机和扫描仪设备。 仅通过 TCP/IP 连接到计算机的网络 MFPs 被识别为单独的打印和扫描设备。 制造商仍可提供自定义设备体验, 包括自定义图标和设备暂存页, 但 "设备和打印机" 视图会将 MFP 中的打印机和扫描仪功能显示为单独的设备。

仅当安装了 MFP 中的打印机和扫描仪功能时, MFP 才会显示在 "设备和打印机" 视图中。 如果只安装了打印机功能, 则此函数将以独立打印机的形式出现在视图中。 如果只安装了扫描器功能, 则此函数显示为独立扫描程序。

"设备和打印机" 用户界面将 Microsoft 共享传真驱动程序创建的传真队列视为打印队列。 可用于打印队列的所有快捷菜单和命令栏菜单都适用于这些队列。

如果合作伙伴传真驱动程序在后台处理程序中显示为打印机, 则设备和打印机用户界面会将它们视为打印队列。 接口为其提供打印机快捷菜单、命令栏菜单和通用打印机图标。

如果某个 MFP 有一个枚举为打印队列的传真队列, 它将作为 MFP 的一部分出现。

如果某个 MFP 有一个不作为打印队列进行枚举的传真功能, 则只有当可以找到传真功能设备实例的设备容器 ID 时, "设备和打印机" 用户界面才能将传真功能标识为 MFP 的一部分。 制造商必须提供自定义元数据来指定此类传真设备的任务。 有关容器 Id 的详细信息, 请参阅[在 MFPs 中标识设备函数](identifying-device-functions-in-mfps.md)。

设备制造商可以为打印机、扫描仪和 MFPs 创作设备阶段。 本地连接的打印机 (例如具有 USB 连接的打印机) 和网络连接的打印机都可以进行自定义的设备体验。

## <a name="device-experience-in-devices-and-printers"></a>设备和打印机中的设备体验

如果制造商未为打印机、扫描仪或 MFP 设备提供自定义 Device Stage 元数据包, 则所有打印机和扫描仪都将仍显示在 "设备和打印机" 视图中。 "设备和打印机" 用户界面为设备提供默认设备体验。 默认设备体验不包括设备的设备暂存页面。

如下图所示, 在 "设备和打印机" 视图中右键单击某个设备时显示的设备图标和快捷菜单对于具有自定义设备体验的设备与具有默认设备的设备是不同的回声. 在此示例中, 该设备是一个本地连接的 MFP。

![默认设备体验和自定义设备体验的快捷菜单](images/devicestage004.png)

对于默认体验 (显示在图的左侧), 设备由通用打印机图标表示。 对于自定义体验, 如图右侧所示, 设备由制造商提供的自定义图标表示。 

对于自定义体验, 快捷菜单中的默认操作为**打开状态**。 选择 "**打开**" 将打开 "设备阶段" 页。 **在新窗口中打开在**新窗口中打开 "设备阶段"。 

对于默认体验, 设备没有关联的 "设备阶段" 页, 快捷菜单不包含 "**打开**" 选项。 选择 "**查看打印内容**" 选项将打开打印队列。

## <a name="device-stage-custom-experience"></a>设备阶段自定义体验

通过设备阶段, 制造商可以轻松地将其产品和企业品牌扩展到桌面。 以下屏幕截图显示了典型的品牌设备阶段自定义体验。

![品牌设备阶段自定义体验](images/devicestage005.jpg)

制造商自定义设备体验。 他们可以包括自己的任务 (启动应用程序、下载软件、访问产品手册、更新固件、购买附件)、提供各种设备状态, 并随时更新体验来反映其最新产品/服务。 

可以为设备的特定型号创建设备阶段体验。 根据你的产品策略, 你可以选择为整行设备创建常规设备体验, 或将每个体验修改为每个设备型号的颜色。

设备阶段体验通过 Microsoft 服务器分布到设备元数据包中的 Windows 客户端。 自定义设备体验的任何更新都将在 Microsoft 服务器上提供, 如果找到, 则会下载到 Windows, 并会自动安装。 如果用户在使用设备阶段, 则该界面将提供立即升级的选项。 否则, 将在下一次使用设备阶段时应用此更新。

还可以使用制造商的安装应用程序来分发设备阶段体验。
