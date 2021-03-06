---
title: 获取能量源标识（功能索引 3）
description: 此函数返回有关能量源的标识信息，这些信息可以是托管主机还是设备管理的。
ms.assetid: E1589FD0-5D03-42EF-8078-0AE53CFB1ACA
ms.localizationpriority: medium
ms.date: 10/17/2018
ms.openlocfilehash: 655fa98a8906617af6c9c4db92a2d7563078366c
ms.sourcegitcommit: 2f37e8de9759164804a3b1c7f5c9e497a607539b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83851335"
---
# <a name="get-energy-source-identification-function-index-3"></a>获取能量源标识（功能索引 3）


此函数返回有关能量源的标识信息，这些信息可以是托管主机还是设备管理的。

> [!NOTE]
> 标有星号（）的所有寄存器 \* 都是在可通过字节寻址的可处理电源接口规范中定义的寄存器。



## <a name="span-idinputspanspan-idinputspanspan-idinputspaninput"></a><span id="Input"></span><span id="input"></span><span id="INPUT"></span>送


### <a name="span-idargs3spanspan-idargs3spanspan-idargs3spanargs3"></a><span id="Args3"></span><span id="args3"></span><span id="ARGS3"></span>Args3

无。

## <a name="span-idoutputspanspan-idoutputspanspan-idoutputspanoutput"></a><span id="Output"></span><span id="output"></span><span id="OUTPUT"></span>输出


<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">字节长度</th>
<th align="left">字节偏移量</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>状态</strong></td>
<td align="left">4</td>
<td align="left">0</td>
<td align="left"><p>请参阅<a href="-dsm-interface-for-byte-addressable-energy-backed-function-class--function-interface-1-.md" data-raw-source="[_DSM Method Output](-dsm-interface-for-byte-addressable-energy-backed-function-class--function-interface-1-.md)">_DSM 方法输出</a>获取详细信息。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>能源源策略</strong></td>
<td align="left">1</td>
<td align="left">4</td>
<td align="left"><p>有关该模块支持的能源源策略的信息。</p>
<p>* Byte 0 – <em>ENERGY_SOURCE_POLICY</em> （0，0x14）</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>设备托管的 ES 标识</strong></td>
<td align="left">11</td>
<td align="left">5</td>
<td align="left">&gt; [!Note]<br/><p>&gt;仅当当前 ES 策略是设备管理的（即，设置了 SET_ES_POLICY_STATUS 的第2位（0，0x70））时，此字段才包含有效数据。 对于所有其他 ES 策略，此字段应为0。</p>

<p>有关信息，请参阅设备托管的 ES 标识。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>主机托管的 ES 标识</strong></td>
<td align="left">3</td>
<td align="left">16</td>
<td align="left">&gt; [!Note]<br/><p>&gt;仅当当前 ES 策略为主机管理（即，设置了 SET_ES_POLICY_STATUS 的第3位（0，0x70））时，此字段才包含有效数据。 对于所有其他 ES 策略，此字段应为0。</p>

<p>有关信息，请参阅托管的 ES 标识。</p></td>
</tr>
</tbody>
</table>



### <a name="span-iddevice_managed_es_identificationspanspan-iddevice_managed_es_identificationspanspan-iddevice_managed_es_identificationspandevice-managed-es-identification"></a><span id="Device_Managed_ES_Identification"></span><span id="device_managed_es_identification"></span><span id="DEVICE_MANAGED_ES_IDENTIFICATION"></span>设备托管的 ES 标识

如果 ES 策略值为0，则设备托管的 "ES 标识" 字段有效并且具有以下字段：

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">字节长度</th>
<th align="left">字节偏移量</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>ES 硬件修订</strong></td>
<td align="left">2</td>
<td align="left">5</td>
<td align="left"><p>ES 硬件修订。</p>
<p><em>Byte 0 – <em>ES_HWREV</em> （1，0x04）</p>
<p>字节 1-保留。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>ES 固件版本</strong></td>
<td align="left">2</td>
<td align="left">7</td>
<td align="left"><p>ES 固件版本。</p>
<p></em>Byte 0 – <em>ES_FWREV0</em> （1，0x06）</p>
<p><em>Byte 1 – <em>ES_FWREV1</em> （1，0x07）</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>ES 运行状况检查频率</strong></td>
<td align="left">1</td>
<td align="left">9</td>
<td align="left"><p>模块的 ES 运行状况评估的当前频率。</p>
<p></em>Byte 0 – <em>AUTO_ES_HEALTH_CHECK_FREQUENCY</em> （0，0xA9）</p></td>
</tr>
<tr class="even">
<td align="left"><strong>ES 计费超时</strong></td>
<td align="left">2</td>
<td align="left">10</td>
<td align="left"><p>ES 时间的最差情况（秒）。 该值应大于0。</p>
<p><em>Byte 0 – <em>ES_CHARGE_TIMEOUT0</em> （1，0x10）</p>
<p></em>Byte 1 – <em>ES_CHARGE_TIMEOUT1</em> （1，0x11）</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>ES 最低运行温度</strong></td>
<td align="left">1</td>
<td align="left">12</td>
<td align="left"><p>ES 的最小运行温度（摄氏度）。 支持的最小值应为0。</p>
<p><em>Byte 0 – <em>MIN_ES_OPERATING_TEMP</em> （1，0x12）</p></td>
</tr>
<tr class="even">
<td align="left"><strong>ES 最高运行温度</strong></td>
<td align="left">1</td>
<td align="left">13</td>
<td align="left"><p>ES 的最高运行温度（以摄氏度为单位）。</p>
<p></em>Byte 0 – <em>MAX_ES_OPERATING_TEMP</em> （1，0x13）</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>ES 属性</strong></td>
<td align="left">1</td>
<td align="left">14</td>
<td align="left"><p>与 ES 相关的属性。</p>
<p><em>Byte 0 – <em>ES_ATTRIBUTES</em> （1，0x14）</p></td>
</tr>
<tr class="even">
<td align="left"><strong>ES 技术</strong></td>
<td align="left">1</td>
<td align="left">15</td>
<td align="left"><p>ES 中使用的技术。</p>
<p></em>Byte 0 – <em>ES_TECH</em> （1，0x15）</p></td>
</tr>
</tbody>
</table>



### <a name="span-idhost_managed_es_identificationspanspan-idhost_managed_es_identificationspanspan-idhost_managed_es_identificationspanhost-managed-es-identification"></a><span id="Host_Managed_ES_Identification"></span><span id="host_managed_es_identification"></span><span id="HOST_MANAGED_ES_IDENTIFICATION"></span>主机托管的 ES 标识

如果 ES 策略值为1，则 "主机托管的 ES 标识" 字段有效并且具有以下字段：

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">字段</th>
<th align="left">字节长度</th>
<th align="left">字节偏移量</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>ES 运行状况检查频率</strong></td>
<td align="left">1</td>
<td align="left">16</td>
<td align="left"><p>平台的 ES 运行状况评估的当前频率。</p>
<p><em>Byte 0 – <em>AUTO_ES_HEALTH_FREQUENCY</em> （0，0xA9）。</p></td>
</tr>
<tr class="even">
<td align="left"><strong>ES 属性</strong></td>
<td align="left">1</td>
<td align="left">17</td>
<td align="left"><p>托管电源源的属性。</p>
<p></em>Byte 0 – <em>HOST_MANAGED_ES_ATTRIBUTES</em> （2，0x82）</p></td>
</tr>
<tr class="odd">
<td align="left"><strong>ES 技术</strong></td>
<td align="left">1</td>
<td align="left">18</td>
<td align="left"><p>位</p>
<ul>
<li><p>[0]：未定义</p></li>
<li><p>[1]： Supercapacitor</p></li>
<li><p>[2]：电池</p></li>
<li><p>[3]：混合电容器</p></li>
<li><p>[7:4] 保留</p></li>
</ul></td>
</tr>
</tbody>
</table>



## <a name="span-idrelated_topicsspanrelated-topics"></a><span id="related_topics"></span>相关主题


[\_用于字节寻址的支持能源的函数类的 DSM 接口（Function Interface 1）](-dsm-interface-for-byte-addressable-energy-backed-function-class--function-interface-1-.md)










