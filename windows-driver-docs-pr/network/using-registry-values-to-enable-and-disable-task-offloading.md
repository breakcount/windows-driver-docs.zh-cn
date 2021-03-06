---
title: 使用注册表值启用和禁用任务卸载
description: 使用注册表值启用和禁用任务卸载
ms.assetid: 32efd685-365c-4347-9599-fe429569d35b
keywords:
- 任务卸载 WDK TCP/IP 传输，注册表值
- 注册表 WDK TCP/IP 卸载
- 任务卸载 WDK TCP/IP 传输，启用服务
- 任务卸载 WDK TCP/IP 传输，禁用服务
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: f9a71b50a9f0502c6e7fceb3473d8f18b20ed7b4
ms.sourcegitcommit: f500ea2fbfd3e849eb82ee67d011443bff3e2b4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2020
ms.locfileid: "89207403"
---
# <a name="using-registry-values-to-enable-and-disable-task-offloading"></a>使用注册表值启用和禁用任务卸载





调试驱动程序的任务卸载功能时，您可能会发现使用注册表项设置启用或禁用任务卸载服务很有用。 你可以在 INF 文件和注册表中定义标准化关键字。 有关标准化关键字的详细信息，请参阅 [网络设备的标准化 INF 关键字](standardized-inf-keywords-for-network-devices.md)。

任务卸载关键字属于以下两个组之一：粒度关键字或分组关键字。 *精细关键字* 提供每个卸载功能的关键字--传输层差异、IP 协议差异。 *分组关键字* 在传输层提供组合关键字功能。

精细关键字定义如下：

<a href="" id="-ipchecksumoffloadipv4"></a>**\*IPChecksumOffloadIPv4**  
描述设备是启用还是禁用了 IPv4 校验和的计算。

<a href="" id="-tcpchecksumoffloadipv4"></a>**\*TCPChecksumOffloadIPv4**  
描述设备是启用还是禁用了对 IPv4 数据包的 TCP 校验和的计算。

<a href="" id="-tcpchecksumoffloadipv6"></a>**\*TCPChecksumOffloadIPv6**  
描述设备是启用还是禁用了对 IPv6 数据包的 TCP 校验和的计算。

<a href="" id="-udpchecksumoffloadipv4"></a>**\*UDPChecksumOffloadIPv4**  
描述设备是启用还是禁用了对 IPv4 数据包的 UDP 校验和的计算。

<a href="" id="-udpchecksumoffloadipv6"></a>**\*UDPChecksumOffloadIPv6**  
描述设备是启用还是禁用了对 IPv6 数据包的 UDP 校验和的计算。

<a href="" id="-lsov1ipv4"></a>**\*LsoV1IPv4**  
描述设备是启用还是禁用了在大型发送卸载版本 1 (LSOv1) 的情况上对大型 TCP 数据包的分段。

<a href="" id="-lsov2ipv4"></a>**\*LsoV2IPv4**  
描述设备是启用还是禁用了在大型发送卸载版本 2 (LSOv2) 的情况通过 IPv4 对大 TCP 数据包的分段。

<a href="" id="-lsov2ipv6"></a>**\*LsoV2IPv6**  
描述设备是启用还是禁用了通过 IPv6 将大 TCP 数据包分段用于大规模发送卸载版本 2 (LSOv2) 。

<a href="" id="-ipsecoffloadv1ipv4"></a>**\*IPsecOffloadV1IPv4**  
描述设备是启用还是禁用了通过 IPv4 计算 IPsec 标头。

<a href="" id="-ipsecoffloadv2"></a>**\*IPsecOffloadV2**  
介绍设备启用还是禁用 IPsec 卸载版本 2 (IPsecOV2) 。 IPsecOV2 提供了对大量发送卸载版本 2 (LSOv2) 的其他加密算法、IPv6 和共存支持。

<a href="" id="-ipsecoffloadv2ipv4"></a>**\*IPsecOffloadV2IPv4**  
描述设备是启用还是禁用 IPsecOV2 仅适用于 IPv4。

下表描述了可用于配置卸载服务的精细关键字。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">SubkeyName</th>
<th align="left">ParamDesc</th>
<th align="left">值</th>
<th align="left">EnumDesc</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><em>IPChecksumOffloadIPv4</strong></p></td>
<td align="left"><p>IPv4 校验和卸载</p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Rx & Tx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>TCPChecksumOffloadIPv4</strong></p></td>
<td align="left"><p>TCP 校验和卸载 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Rx & Tx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><em>TCPChecksumOffloadIPv6</strong></p></td>
<td align="left"><p>TCP 校验和卸载 (IPv6) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Rx & Tx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>UDPChecksumOffloadIPv4</strong></p></td>
<td align="left"><p>UDP 校验和卸载 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Rx & Tx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><em>UDPChecksumOffloadIPv6</strong></p></td>
<td align="left"><p>UDP 校验和卸载 (IPv6) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Rx & Tx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>LsoV1IPv4</strong></p></td>
<td align="left"><p>大型发送卸载版本 1 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1 (默认值) </p></td>
<td align="left"><p>已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><em>LsoV2IPv4</strong></p></td>
<td align="left"><p>大型发送卸载 V2 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1 (默认值) </p></td>
<td align="left"><p>已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>LsoV2IPv6</strong></p></td>
<td align="left"><p>大型发送卸载 V2 (IPv6) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1 (默认值) </p></td>
<td align="left"><p>已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong><em>IPsecOffloadV1IPv4</strong></p></td>
<td align="left"><p>IPsec 卸载版本 1 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用身份验证标头</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 ESP</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>身份验证标头已启用 & ESP</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>IPsecOffloadV2</strong></p></td>
<td align="left"><p>IPsec 卸载</p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用身份验证标头</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 ESP</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>身份验证标头已启用 & ESP</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>*IPsecOffloadV2IPv4</strong></p></td>
<td align="left"><p>IPsec 卸载 (仅 IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用身份验证标头</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 ESP</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>身份验证标头已启用 & ESP</p></td>
</tr>
</tbody>
</table>

 

**注意**   INF 文件可以支持在 UI 的 "高级" 属性页中显示的精细关键字。 小型端口驱动程序必须在初始化时读取注册表中的所有精细设置，包括未显示的设置，以注册 NDIS 卸载功能。

 

按如下所示定义分组关键字：

<a href="" id="-tcpudpchecksumoffloadipv4"></a>**\*TCPUDPChecksumOffloadIPv4**  
描述设备是启用还是禁用通过 IPv4 计算 IP、TCP 和 UDP 校验和。

<a href="" id="-tcpudpchecksumoffloadipv6"></a>**\*TCPUDPChecksumOffloadIPv6**  
描述设备是启用还是禁用了对 IPv6 的 TCP 和 UDP 校验和的计算。

下表描述了可用于配置卸载服务的分组关键字。

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">SubkeyName</th>
<th align="left">ParamDesc</th>
<th align="left">值</th>
<th align="left">EnumDesc</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong><em>TCPUDPChecksumOffloadIPv4</strong></p></td>
<td align="left"><p>TCP/UDP 校验和卸载 (IPv4) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Tx & Rx 已启用</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong></em>TCPUDPChecksumOffloadIPv6</strong></p></td>
<td align="left"><p>TCP/UDP 校验和卸载 (IPv6) </p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>已禁用</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>1</p></td>
<td align="left"><p>已启用 Tx</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>2</p></td>
<td align="left"><p>已启用 Rx</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"></td>
<td align="left"><p>3 (默认值) </p></td>
<td align="left"><p>Tx & Rx 已启用</p></td>
</tr>
</tbody>
</table>

 

可以启用的卸载的组合有限制。 例如，如果微型端口适配器支持 LSOV1 或 LSOV2，则微型端口适配器还会计算 IP 和 TCP 校验和。 有关卸载的有效组合的详细信息，请参阅 [合并类型的任务卸载](combining-types-of-task-offloads.md)。

如果使用注册表项设置禁用了任务卸载服务，则协议驱动程序不得)  (OID 发出 [oid \_ 卸载 \_ 封装](./oid-offload-encapsulation.md) 对象标识符。

你可以使用以下注册表值来启用或禁用 TCP/IP 协议的任务卸载：

<a href="" id="hkey-local-machine-system-currentcontrolset-services-tcpip-parameters-disabletaskoffload-------"></a>**HKEY \_ 本地 \_ 计算机 \\ 系统 \\ CurrentControlSet \\ 服务 \\ TCPIP \\ 参数 \\ DisableTaskOffload**   
将此值设置为 one 将禁用 TCP/IP 传输中的所有任务卸载。 如果将此值设置为零，则将启用所有任务卸载。

<a href="" id="hkey-local-machine-system-currentcontrolset-services-ipsec-enabledoffload-------"></a>**HKEY \_ 本地 \_ 计算机 \\ 系统 \\ CurrentControlSet \\ Services \\ Ipsec \\ EnabledOffload**   
如果将此值设置为零，则将禁用从 TCP/IP 传输 (IPsec) 卸载的 Internet 协议安全性。 卸载 TCP/IP 校验和任务、大型发送卸载版本 1 (LSOV1) ，以及大量发送卸载版本 2 (LSOV2) 不受影响。 将此值设置为 one 会启用 IPsec 卸载。

 

