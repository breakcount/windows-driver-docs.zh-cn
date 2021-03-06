---
title: 示例 I/O 请求 - 概述
description: 示例 I/O 请求 - 概述
ms.assetid: ffc9030e-4b03-4899-88a0-ed6ffd79fd58
keywords:
- 打开文件对象
- 命名的文件对象 WDK 内核
- 文件对象 WDK 内核
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: d44dbffe7ca156f9341cdc7e8416379d45e344ae
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63361866"
---
# <a name="example-io-request---an-overview"></a>示例 I/O 请求 - 概述





下图显示了一个子系统打开一个表示代表应用程序的数据文件的文件对象时，会发生什么情况的概述。

![说明打开文件对象的关系图](images/2opendev.png)

1.  子系统调用 I/O 系统服务，以打开一个命名的文件。

2.  I/O 管理器调用对象管理器来查找命名的文件，并以帮助其解决任何用于文件对象的符号链接。 它还调用安全引用监视器检查子系统具有正确的访问权限，以打开该文件对象。

3.  如果卷未装载，I/O 管理器暂时挂起打开请求并调用一个或多个文件系统，直到其中一个将文件对象识别为内容它已存储在一个文件系统使用的大容量存储设备上。 文件系统已装入卷，I/O 管理器将恢复请求。

4.  I/O 管理器分配内存并初始化 IRP 打开请求。 驱动程序，打开相当于"创建"请求。

5.  I/O 管理器调用文件系统驱动程序，并向其传递 IRP。 文件系统驱动程序访问其在 IRP 来确定哪些操作，它必须执行、 检查参数，确定在缓存中，为所请求的文件时的 I/O 堆栈位置，并且如果没有，请设置较低的下一步驱动程序的 I/O 堆栈中的位置。

6.  这两个驱动程序处理 IRP，并完成请求的 I/O 操作，调用内核模式下支持例程提供通过 I/O 管理器和其他系统组件 （不在上图中所示）。

7.  驱动程序返回 IRP 到 I/O 管理器与 I/O 状态块中设置，以指示所请求的操作是否成功或失败的原因。

8.  因此，它可以通过受保护的子系统的状态信息返回到原始调用方，I/O 管理器从 IRP，获取的 I/O 状态。

9.  I/O 管理器释放已完成的 IRP。

10. 如果打开操作成功，I/O 管理器对子系统返回的文件对象的句柄。 如果出现错误，则对子系统返回相应的状态。

子系统子系统已成功打开的文件对象来表示一台设备或卷的数据文件后，使用返回的句柄来标识设备 I/O 操作 （通常读取、 写入或设备 I/O 控制的后续请求中的文件对象请求）。 若要使此类请求，该子系统调用 I/O 系统服务。 I/O 管理器将这些请求路由为 Irp 发送到合适的驱动程序。

 

 




