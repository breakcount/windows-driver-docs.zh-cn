---
title: 计时器准确性
description: 系统计时器例程通常允许调用方为计时器指定绝对过期时间或相对过期时间。
ms.assetid: CA29DC02-1AEA-4A13-B2D6-8C8052E21EDB
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: aa928ff01878700ad160d6503ffc4f4db7e5b8a3
ms.sourcegitcommit: e769619bd37e04762c77444e8b4ce9fe86ef09cb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89186699"
---
# <a name="timer-accuracy"></a>计时器准确性


系统计时器例程通常允许调用方为计时器指定绝对过期时间或相对过期时间。 例如，请参阅 [**KeWaitForSingleObject**](/windows-hardware/drivers/ddi/wdm/nf-wdm-kewaitforsingleobject)、 [**KeSetTimer**](/windows-hardware/drivers/ddi/wdm/nf-wdm-kesettimer)或 [**KeDelayExecutionThread**](/windows-hardware/drivers/ddi/wdm/nf-wdm-kedelayexecutionthread)。 操作系统可用于测量过期时间的准确性受系统时钟粒度的限制。

系统时间在系统时钟的每个时钟周期进行更新，并且仅精确到最新计时周期。 如果调用方指定绝对过期时间，则在处理在指定时间之后发生的第一个系统时钟计时周期时，将检测到计时器的过期时间。 因此，计时器的过期时间可能会晚于指定的绝对到期时间。 如果改为指定计时器间隔或相对过期时间，则过期时间可能早于或晚于指定时间的一段时间，具体取决于此时间间隔的开始时间和结束时间在系统时钟计时周期之间的确切位置。 不管是指定了绝对时间还是相对时间，都不会检测到计时器过期时间，直到更晚，因为对其他设备的中断处理延迟了对系统时钟的中断处理。

如果调用方指定了相对过期时间，则计时器例程会将当前系统时钟时间添加到指定的相对过期时间，以计算要用于计时器的绝对到期时间。 因为系统时间只是精确到系统时钟的最晚计时周期，所以，计算出的过期时间可能会早于调用方预期的过期时间。 如果指定的相对过期时间接近于或小于系统时钟周期，则计时器可能会立即过期，且不会延迟。

更准确地支持较短过期时间的一种可能方式是缩短系统时钟计时周期之间的时间，但这样做可能会增加功率消耗。 此外，降低系统时钟周期可能无法可靠地获得更精细的系统时钟粒度，除非可以保证平台中其他设备的中断处理不会延迟系统时钟中断的处理。

从 Windows 8 开始， [**KeDelayExecutionThread**](/windows-hardware/drivers/ddi/wdm/nf-wdm-kedelayexecutionthread) 使用更精确的技术来计算调用方指定的相对过期时间中的绝对过期时间。 首先，为了获得当前系统时间的更精确估计值，例程使用系统性能计数器来测量自上一次系统时钟周期以来所经过的时间。 接下来，例程会将系统时间的更精确估计添加到相对过期时间，以计算绝对过期时间。 此方法计算的绝对过期时间精确到了一个微秒内。 因此，在指定的相对过期时间过去之前，计时器不会过期。 计时器仍可以在超过指定时间之后的系统时钟周期内过期，如果对系统时钟中断的处理延迟为其他设备的中断处理延迟，则可能会在以后过期。

如果在计时器过期之前系统时间发生更改，则相对计时器不会受影响，但系统会调整每个绝对计时器。 相对计时器始终在经过指定的时间单位后过期，而不管系统的绝对时间是多少。 绝对计时器会在特定系统时间过期，因此，系统时间更改会更改绝对计时器的等待持续时间。

 

