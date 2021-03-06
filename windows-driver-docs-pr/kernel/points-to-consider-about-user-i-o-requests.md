---
title: 有关用户 I/O 请求的要点
description: 有关用户 I/O 请求的要点
ms.assetid: e8143055-4ad7-4e39-a2f2-64d9e79d33a0
keywords:
- 特定于设备的 i/o 控制代码 WDK 内核
- 专用 i/o 控制代码 WDK 内核
- 分层驱动程序 IRP 处理 WDK 内核
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0be282aa69c65e62bea436b7c10deb004bcefc1d
ms.sourcegitcommit: 7500a03d1d57e95377b0b182a06f6c7dcdd4748e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90107004"
---
# <a name="points-to-consider-about-user-io-requests"></a>有关用户 I/O 请求的要点





设计内核模式驱动程序时，请记住以下几点：

- 驱动程序可以分层，多个驱动程序可以处理 (IRP) 的单个 i/o 请求。

- 驱动程序无法对设备堆栈中的其他驱动程序作出任何假设。 因此，每个驱动程序都应准备好接收来自任何其他驱动程序的请求，并且应处理所有潜在的错误事例。

- 驱动程序在 IRP 的 i/o 状态块中传达请求的 i/o 操作是成功还是失败。 I/o 管理器将请求的 i/o 操作的成功或失败传达给用户模式请求方。

- 驱动程序无需且不应设计为提供特定于应用程序的支持。 受保护的子系统或其特定于子系统的用户模式驱动程序提供此类支持。 此规则有一个例外：依赖于应用程序专用设备的 MS-DOS 应用程序可以要求使用内核模式驱动程序来控制设备和紧密耦合的 Win32 用户模式虚拟设备驱动程序， (VDD) 。 有关 VDDs 的详细信息，请参阅 Windows 驱动程序开发工具包 (DDK) 中的虚拟设备驱动程序文档。  (在 Windows 驱动程序工具包 WDK 之前的 DDK \[ \] 。 ) 

- 新的驱动程序必须与它所替换的任何系统提供的驱动程序一样处理同一 **IRP \_ MJ \_ * XXX*** 组。 \_ \_ \_ 如果目标设备的驱动程序未定义该<strong>IRP \_ MJ \_ * XXX</strong>的入口点，则 i/o 管理器将向目标设备的给定 I/o 请求返回状态 "无效设备请求"<em>。设备驱动程序还必须处理与任何系统提供的驱动程序所取代的 [</em> *IRP \_ MJ \_ 设备 \_ 控制* * 请求相同的 i/o 控制代码](./irp-mj-device-control.md)。 换句话说，新的设备驱动程序不能通过实现比同一设备类型的现有驱动程序更少的功能来 "中断应用程序"。

- 插入到现有驱动程序链中的新中间驱动程序应识别与它视角的驱动程序相同的 **IRP \_ MJ \_ * XXX*** 组。 新驱动程序只需将 Irp 传递到未处理到下一个较低级别驱动程序的请求。 但是，对于其上方和下方的驱动程序，新的中间驱动程序不得 "中断链"，但忘了为新替换的下一级驱动程序处理的 **IRP \_ MJ \_ * XXX*** 请求定义入口点。

- 最低级别的驱动程序只能访问它所发送的任何 IRP 中自己的 i/o 堆栈位置。 更高级别的驱动程序只能访问其自身和下一个较低级别的驱动程序在其发送的 IRP 中的 i/o 堆栈位置。

- 每个驱动程序都将信息传递给更高级别的驱动程序 (最终通过 i/o 管理器向用户模式应用程序传递) ，因为 i/o 管理器将相应的 i/o 堆栈位置作为链中的每个驱动程序完成 IRP。 任何新的驱动程序都尝试实现与特定较高 (或更低) 驱动程序的后门通信，这会损害其可移植性，并与从一个 Windows 平台或版本到下一个版本的其他驱动程序的互操作性。

- 一对驱动程序可以定义一组特定于设备的 (，也称为 *专用*) i/o 控制代码，用于 [**IRP \_ MJ \_ 内部 \_ 设备 \_ 控制**](./irp-mj-internal-device-control.md) 请求，这些请求中的较高可以向下发送到配对的下限。 但是，如果这些驱动程序将在一个 Windows 平台或版本间保持可移植性并可与其他驱动程序互操作，则这两个驱动程序必须遵循上述所有准则。 如果使用专用接口设计一对驱动程序，请考虑小心定义一组 i/o 控制代码。 尽可能使其尽可能常见并设计配对的驱动程序以遵循上述准则，以便 (或其他人) 可以在从一个 Windows 平台或版本迁移到另一个时轻松地重复使用、替换或替换这两个新的驱动程序。

