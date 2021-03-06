---
title: 筛选数据
description: 为了优化数据吞吐量和电池寿命，传感器设备必须对数据更新事件应用筛选条件，以便仅在需要时才引发这些事件。
ms.assetid: EDABA09D-2C46-4546-9429-CF6DEFBF69C4
keywords:
- 更改敏感度
- 传感器更改敏感度
- 阈值
- 传感器阈值
- CS
- 当前报表间隔
- 传感器当前报表间隔
- CRI
- 数据更新事件
- 传感器事件
- 传感器事件
- 筛选数据
- 数据筛选
ms.date: 07/20/2018
ms.localizationpriority: medium
ms.openlocfilehash: fba833d045b6b7896de33a379f104205b82e4de2
ms.sourcegitcommit: 937974aa9bbe0262a7ffe9631593fab48c4e7492
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2020
ms.locfileid: "90010471"
---
# <a name="filtering-data"></a>筛选数据


为了优化数据吞吐量，传感器设备必须对数据更新事件应用筛选条件，以便仅在需要时才会引发这些事件。 此筛选将导致 CPU 使用率降低 (因为传感器的吞吐量降低) 并且传感器和 CPU)  (能耗更少。

有两个 (的值或属性) 支持传感器设备的筛选条件。 第一个是 (CRI) 的当前报表间隔，第二个是 (CS 的更改敏感度，也称为阈值) 。 这两个属性都可以由传感器 Win32 应用程序设置。

当前报表间隔是客户端希望在有意义的更改时接收的数据更新之间的最短时间（以毫秒为单位）。 更改敏感度是 (或百分比) 用于指定有意义的更改的值。

因此，在 60000 (或一分钟) ，天气工作站应用程序可以为温度传感器 (CRI) 指定当前报表间隔。 温度传感器需要 (相对于百分比) 的更改敏感度值。 例如，如果此温度传感器返回摄氏温度，而更改敏感度值温度为2.0，则此特定传感器将仅在以下情况下引发数据更新事件2.0：温度增加或降低，超出请求的报表间隔 (，即一分钟) 。

环境光线传感器 (ALS) 是需要以百分比形式指定更改敏感度的传感器的示例。 例如，如果 Illuminance 的更改敏感度值为2.0，此传感器会将值解释为百分比，并且仅当 LUX 值已删除或增加2% 时才会引发数据更新事件。

## <a name="terminologies-related-to-filtering-criteria"></a>与筛选条件相关的术语

| 术语 | 含义 |
|------|---------|
| 当前报表间隔 (CRI)  | 以毫秒为单位表示的速率 (频率) （以毫秒为单位），当发生有意义的更改时，客户端希望接收数据更新。<br><br>此字段表示为事件间的最短时间段（如果发生了有意义的更改） (检测到的传感器现象) 。 根据出现有意义的更改，该时间段会有所不同，但绝不会短于这一阶段。<br><br>此值为每个传感器。|
|  (CS) 更改敏感度 | 构成有意义变化的度量现象的变化。 这可以表示为线性量 (例如，.05 G 表示加速感应器读取) 或 (5% 5%) 的非线性量。<br><br>此值为每个传感器数据字段。|
| 有效的当前报表间隔 (E-CRI)  | 在任意给定时间点计算并由设备驱动程序用于筛选数据更新事件传递的 RI 值（基于：<ul><li>如果任何) ，客户端 (设置 RI 值</li><li>设备 (作为默认行为由驱动程序实现的默认 RI) </li><li>硬件遵守请求的 RI 的能力</li></ul><br>此值为每个传感器。|
|  (E-CS) 有效的更改敏感度 | 在任意给定时间点计算并由设备驱动程序用于筛选数据更新事件传递的 CS 值：<ul><li>如果任何) ，则由客户端设置的 CS 值 (</li><li>设备 (作为默认行为由驱动程序实现的默认 CS) </li><li>硬件遵守请求的 CS 的能力</li></ul><br>此值为每个传感器数据字段。|

## <a name="change-sensitivity"></a>更改敏感度
此文档的 " [传感器阈值](sensor-thresholds-v2.md) " 部分涵盖了每个传感器可能的更改敏感度值的完整列表。

## <a name="current-report-interval-recommended-defaults"></a>当前报表间隔推荐的默认值
下表列出了建议的当前报表间隔 (CRI) 默认值。

| 传感器类型               | 推荐的默认报表间隔  |
|---------------------------|--------------------------------------|
| 加速计             | 100                                  |
| 活动检测        | 5000                                 |
| 环境光线传感器      | 1000                                 |
| 气压计                 | 1000                                 |
| 自定义传感器             | 不可用                                  |
| 地磁方向   | 100                                  |
| 重力向量            | 100                                  |
| 陀螺测试仪                 | 100                                  |
| 线性加速感应      | 100                                  |
| 磁力计              | 100                                  |
| 方向               | 50                                   |
| 步程计                 | 1000                                 |
| 邻近帮助                 | 100*                                 |
| 相对方向      | 100                                  |
| 简单设备方向 | 200*                                 |

 ( * ) 邻近性和简单的设备方向传感器不能按固定间隔报告采样读数。 相反，当读取发生更改时，这些传感器应向类扩展报告数据。 这些传感器的报告间隔值表示传感器报告示例读取所需的最长时间。

## <a name="change-sensitivity-recommended-defaults"></a>更改敏感度建议的默认值
下表列出了 (CS) 默认值建议的更改敏感度。

|  传感器类型              | 建议的默认更改敏感度 |
|---------------------------|----------------------------------------|
| 加速计             | 0.02 G                                 |
| 活动检测        | 0 (未订阅任何活动)              |
| 环境光线传感器      | 25% lux 更改                         |
| 气压计                 | 0.001 bar                              |
| 自定义传感器             | 不可用                                    |
| 地磁方向   | 10.0 度                           |
| 重力向量            | 10.0 度                           |
| 陀螺测试仪                 | 每秒0.50 度                |
| 线性加速感应      | 0.02 G                                 |
| 磁力计              | 5.0 microtesla                         |
| 方向               | 10.0 度                           |
| 步程计                 | 10000步骤                            |
| 邻近帮助                 | 邻近更改时                    |
| 相对方向      | 10.0 度                           |
| 简单设备方向 | 根据方向更改                  |

## <a name="effective-current-report-interval-cri-and-change-sensitivity-cs"></a>有效的当前报表间隔 (CRI) 并 (CS 的更改敏感度) 

多个应用程序可将当前报表间隔设置 (CRI) ，并为给定传感器 (CS) 属性设置更改敏感度。 当应用程序配置存在冲突时 (例如两个应用程序请求不同的更改敏感度值或不同的报表间隔) ，则传感器类扩展会确定要发送到驱动程序的最相关的 CS 和 CRI。 传感器类扩展提供给驱动程序的 CS 和 CRI 值称为) 有效的当前报表间隔 (E-CRI 和 (E-CS) 的有效的更改敏感度。

以下函数由传感器类扩展调用、启动/停止传感器、报告示例读取或设置 CRI 和电子商务。

| 相关事件          | 事件处理程序活动                                           |
|----------------------------|--------------------------------------------------------------------|
| EvtSensorStart             | 启动传感器                                                  |
| EvtSensorStop              | 停止传感器                                                   |
| EvtSensorSetDataInterval   | 设置当前报表间隔                                    |
| EvtSensorGetDataInterval   | 获取当前报表间隔                                    |
| EvtSensorSetDataThresholds | 设置当前更改敏感度 (阈值) 值              |
| EvtSensorGetDataThresholds | 获取当前的更改敏感度 (阈值) 值              |
| SensorsCxSensorDataReady   | 驱动程序报告对传感器类扩展的示例读取 |

## <a name="filtering-data-update-events-by-evaluating-the-effective-cri-and-cs-values-e-cri-e-cs"></a>通过评估有效的 CRI 和 CS 值 (E-CRI，E-CS) 来筛选数据更新事件

设置当前的 CRI 和 E-CS 值后，传感器设备将使用这些值来筛选引发到连接的客户端应用程序的事件。 将这些值与 "当前" 数据值 (") " 和 " () 的以前数据值之间的差异进行比较。 如果在等于或大于 E-CRI 的时间段内超过了 E-CS 值，则应引发数据事件。 这种情况的唯一例外是，本文档后面部分介绍的初始示例读取内容。

使用当前的 CRI 和当前的 E-CS 值作为要引发的事件的筛选条件来筛选事件。 这些筛选值与当前数据值与以前的数据值之间的差异进行比较，以确定何时应通过调用 SensorsCxSensorDataReady 来引发事件。 如果已超出 (E-CS) 的量阈值等于或大于 (E-CRI) 的时间阈值，则仅引发数据事件。 建议在获取了初始值以便客户端可以接收正确的通知时，在驱动程序启动时引发数据事件。 此外，此实现不应比请求的报表间隔更频繁地唤醒 CPU，以节省电源。

下图演示了如何评估原始传感器数据的时间筛选，以便确定何时应引发数据事件。

![时间筛选的传感器数据](images/cri-cs.png)

在上图中，关系图下半部分的红色数据表示原始传感器数据。 绿线表示将返回到数据轮询的客户端的数据 (多种方法来实现此行为) 并且 "<font color="red">__X__</font>" 值表示触发数据事件的时间。 蓝线是电子 CS 边界 (+/-E-CS 相对于) 的最后一个数据事件值的阈值。

通过实现此事件筛选逻辑，可大大减少更新的数据事件数，并且当传感器数据发生有意义的更改时，应用程序仍会收到通知。

## <a name="streaming"></a>流式处理

流式处理是一种允许传感器驱动程序定期报告采样读数的模式。 应用程序可以使用此模式来接收常量数据流。

### <a name="general-case"></a>常规情况

传感器（除了下面所述的传感器）必须在每个 CRI 中报告一个示例读取，前提是类扩展将所有传感器 CS 值设置为0。

### <a name="exceptions"></a>异常

* 如果 PKEY_SensorData_SubscribedActivityStates 设置为0，则活动检测传感器不能报告任何活动更改。 当传感器类扩展要求传感器进行流式处理时，它会将 PKEY_SensorData_ActivityStream 设置为 TRUE。
* 邻近感应传感器和简单设备方向不能支持流式处理。
* 邻近感应传感器只能在接近检测状态更改 (检测到检测到检测到未检测到之间，反之亦然，反之亦然) ，反之亦然。
* 简单设备定向传感器只能在设备的方向发生更改时报告示例，但必须遵循初始示例读数例外。

## <a name="initial-sample-reading"></a>初始示例读取

当传感器驱动程序通过调用 EvtSensorStart 启动时，驱动程序必须在传感器硬件准备好发送有效数据后，通过对 SensorsCxSensorDataReady 的调用报告一个传感器示例。 初始示例读取必须发送到类扩展，而不考虑报表间隔或更改敏感度设置。 应用程序使用初始示例作为示例读取比较的基础。
此规则适用于所有传感器。


## <a name="device-runtime-optimizations-for-data-filtering"></a>用于数据筛选的设备运行时优化

本部分介绍开发传感器驱动程序时应考虑的几个运行时优化。

### <a name="support-interrupts"></a>支持中断

驱动程序应依赖于中断，而不是轮询设备。 这将导致性能和电源管理的改进。 这些改进包括以下各项。

1.  你的设备可以根据当前的更改敏感度和报表间隔输入较低的电源状态。
2.  使用中断将减少驱动程序和传感器固件中不必要的代码执行。
3.  使用中断将减少总线活动。

**注意**：如果驱动程序依赖于中断，但驱动程序中存在当前报表间隔和更改敏感性逻辑，则驱动程序可能会在数据更新之间收到大量的中断。 因此，在当前报表间隔过期之前，驱动程序可能需要禁用 (或屏蔽) 中断。


### <a name="move-change-sensitivity-support-to-the-device"></a>将更改敏感度支持移到设备

如果传感器硬件或固件支持阈值检测，则应使用此功能来支持更改敏感度。 通过将支持转移到设备，然后响应相应的中断，可减少驱动程序的处理开销。

### <a name="move-report-interval-support-to-the-devices"></a>将报表间隔支持移动到设备

如果传感器硬件或固件支持报表间隔的概念，则应使用此功能。

如果你的传感器不提供本机报表间隔支持，请考虑对当前报表间隔的子集禁用中断。 然后，在此时间过后，检索当前设备数据。

## <a name="related-topics"></a>相关主题
[传感器地理位置驱动程序示例](../gnss/sensors-geolocation-driver-sample.md)