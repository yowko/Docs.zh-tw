---
title: <socket> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ec2c8388411e24940041dc9dcb7f6a6755e89805
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697579"
---
# <a name="socket-element-network-settings"></a>@no__t 0socket > 元素（網路設定）
指定通訊端作業是否使用完成埠。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<socket >**  
  
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
|`alwaysUseCompletionPortsForAccept`|指出通訊端是否應一律使用完成埠來接受方法呼叫。 預設值為 `false`。|  
|`alwaysUseCompletionPortsForConnect`|指出通訊端是否應一律使用完成埠來進行 Connect 方法呼叫。 預設值為 `false`。|  
|`ipProtectionLevel`|指定要用於通訊端的預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>。 預設值取決於 Windows 的版本。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**目**|**描述**|  
|-----------------|---------------------|  
|[設置](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  
 `alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。 建議將完成埠用於高效能伺服器應用程式。  
  
 @No__t-0 和 @no__t 1 屬性的預設值為**false**。  
  
 @No__t-0 可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。 @No__t-0 可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。  
  
 @No__t-0 屬性會指定要用於通訊端的預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>。 @No__t-0 屬性可讓 IPv6 通訊端的限制設定為指定的範圍，例如具有相同連結本機或網站本機首碼的位址。 此選項可讓應用程式在 IPv6 通訊端上放置存取限制。 這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。 此選項會擴大或縮小接聽通訊端的範圍，並在適當時啟用公用和私用使用者的無限制存取，或視需要限制只有相同網站的存取權。  
  
 這個 `ipProtectionLevel` 屬性設定只會影響初始傳入流量：  
  
- 一台 TCP 伺服器，接聽通訊端上的連入連線。  
  
- 在通訊端上接收封包的 UDP 應用程式。  
  
 此設定不會影響已建立的 TCP 連線（雙向流量不受限制），也不會影響傳送 UDP 封包的應用程式。  
  
 @No__t-0 屬性設定的可能值會對應至 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 列舉中所指定的已定義保護層級，如下所示：  
  
|**屬性值**|**描述**|  
|-|-|  
|EdgeRestricted|IP 保護層級為 [edge 限制]。 此值適用于設計為跨網際網路運作的應用程式。 此設定不允許使用 Windows Teredo 執行來進行網路位址轉譯（NAT）遍歷。 這些應用程式可能會略過 IPv4 防火牆，因此應用程式必須針對在開啟的埠上導向的網際網路攻擊進行強化。 在 Windows Server 2003 和 Windows XP 上，通訊端上 IP 保護層級的預設值是 [edge 限制]。|  
|約束|IP 保護層級受到限制。 不會執行網際網路案例的內部網路應用程式會使用此值。 這些應用程式通常不會針對網際網路風格的攻擊進行測試或強化。 此設定會將接收到的流量限制為僅限連結-本機。|  
|無限制的|IP 保護層級不受限制。 此值適用于設計為跨網際網路運作的應用程式，包括利用 Windows 內建的 IPv6 NAT 遍歷功能的應用程式（例如 Teredo）。 這些應用程式可能會略過 IPv4 防火牆，因此應用程式必須針對在開啟的埠上導向的網際網路攻擊進行強化。 在 Windows Server 2008 R2 和 Windows Vista 上，通訊端上 IP 保護層級的預設值是 [不受限制]。|  
|未指定|未指定 IP 保護等級。 在 Windows 7 和 Windows Server 2008 R2 上，未指定通訊端上 IP 保護層級的預設值。|  
  
 **未指定**`ipProtectionLevel` 屬性的預設值。  
  
 @No__t-0 屬性可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。  
  
## <a name="configuration-files"></a>組態檔  
 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定應該使用完成埠，以及預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 應該不受限制。  
  
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

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
