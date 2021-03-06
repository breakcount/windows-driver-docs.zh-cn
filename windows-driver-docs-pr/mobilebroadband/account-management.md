---
title: 帐户管理
description: 帐户管理
ms.assetid: 8201a4ac-1344-4a96-b0d5-d4ba8123c4dd
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 1b643d19e6d12539aed83d1e280a47e50ea38219
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89212573"
---
# <a name="account-management"></a>帐户管理


用户购买订阅后，可以执行以下任务：

-   **查看当前数据使用情况** 用户可以查看他们当前的数据使用情况，并了解他们的计费周期 (或会话结束日期) 以便对其数据使用做出适当的决策。

-   **管理帐户设置** 用户可以查看并安全地管理其支付和帐户详细信息 (例如密码、电子邮件地址和) 的自动付款信息。

-   **支付帐单** 用户可以使用 UWP 应用支付定期或一次性帐单。

帐户管理功能显示订阅服务器与操作员之间的关系。 可以使用它来创建可将服务与竞争对手的服务区分开来的品牌体验。

设计注意事项包括：

-   将**数据使用组合为本地和后端信息**为了尽可能减少后端服务器上的负载，Windows 提供了本地数据使用 API，你可以使用它来合并后端数据使用。 可以定期从后端获取使用情况信息，并将其与本地数据使用关联起来。

-   **使用数据使用定期更新 Windows** Windows 10 旨在智能地在按流量计费的网络上运行。 这可以节省大量网络容量，因为 Windows 和 UWP 应用可以使用移动宽带网络来实现重要的流量。 若要更准确地了解应用程序的详细信息 (例如，数据限制和使用情况) ，Windows 需要定期提供正确的信息。 应用可以使用数据使用情况 Api 来设置此信息。

    ![帐户概述](images/mb-fig2-accountoverview.png)

## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>相关主题


[移动宽带应用方案]()

 

