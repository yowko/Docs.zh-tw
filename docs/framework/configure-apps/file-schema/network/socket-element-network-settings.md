---
title: '&lt;通訊端&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fb057ab75c31edd7bbdaf5d5115cda2802d3b057
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203991"
---
# <a name="ltsocketgt-element-network-settings"></a>&lt;通訊端&gt;項目 （網路設定）
指定通訊端作業是否使用完成通訊埠。  
  
 \<configuration>  
\<system.net>  
\<設定 >  
\<通訊端 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|**屬性**|**描述**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|表示通訊端是否應該永遠使用完成通訊埠的接受方法呼叫。 預設值是 `false`。|  
|`alwaysUseCompletionPortsForConnect`|表示通訊端是否應該永遠使用完成通訊埠的連線方法呼叫。 預設值是 `false`。|  
|`ipProtectionLevel`|指定的預設<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>用於通訊端。 預設值取決於 Windows 的版本。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 `alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。 高效能伺服器應用程式的建議完成連接埠。  
  
 預設值`alwaysUseCompletionPortsForAccept`並`alwaysUseCompletionPortsForConnect`屬性是**false**。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>可用來取得目前的值`alwaysUseCompletionPortsForAccept`適用的組態檔中的屬性。 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>可用來取得目前的值`alwaysUseCompletionPortsForConnect`適用的組態檔中的屬性。  
  
 `ipProtectionLevel`屬性會指定預設<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>用於通訊端。 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性在例如地址的相同連結本機或網站本機首碼，可讓您設定在指定的範圍，IPv6 通訊端的限制。 此選項可讓 IPv6 通訊端上的存取限制的應用程式。 這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。 此選項可放大或縮小接聽通訊端，從公用和私用使用者，請在適當時機，或只限相同的站台，視需要存取啟用不受限制的存取範圍。  
  
 這`ipProtectionLevel`屬性設定會影響初始的連入流量：  
  
-   TCP 伺服器接聽的通訊端上的連入連線。  
  
-   接收通訊端上的封包的 UDP 應用程式。  
  
 此組態設定不會影響已經建立的 TCP 連線 （流量不受限制的兩個方向），而且不會影響應用程式會傳送 UDP 封包。  
  
 可能值`ipProtectionLevel`屬性設定中指定的已定義的保護層級對應至<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>列舉型別，如下所示：  
  
|**屬性值**|**描述**|  
|-|-|  
|EdgeRestricted|IP 保護層級有臨界限制。 若要在網際網路上操作所設計的應用程式會使用此值。 此設定不允許使用 Windows Teredo 實作的網路位址轉譯 (NAT) 周遊。 這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式導向的開啟連接埠的網際網路攻擊。 在 Windows Server 2003 和 Windows XP 上，通訊端 IP 保護層級的預設值有臨界限制。|  
|限制|IP 保護層級會受到限制。 未實作網際網路案例的內部網路應用程式會使用此值。 這些應用程式通常未測試或對抗網際網路型攻擊。 此設定會限制只有連結-本機接收的流量。|  
|無限制的|IP 保護層級不受限制。 這個值會由設計在整個網際網路、 包括利用內建的 IPv6 NAT 周遊功能的應用程式運作的應用程式到 Windows (例如 Teredo)。 這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式導向的開啟連接埠的網際網路攻擊。 在 Windows Server 2008 R2 和 Windows Vista 上，通訊端 IP 保護層級的預設值是不受限制的。|  
|未指定|未指定 IP 保護層級。 在 Windows 7 和 Windows Server 2008 R2 上，通訊端 IP 保護層級的預設值是未指定。|  
  
 預設值`ipProtectionLevel`屬性是**Unspecified**。  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可用來取得目前的值`ipProtectionLevel`適用的組態檔中的屬性。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定應該使用完成通訊埠，預設值<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>應該是不受限制。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
