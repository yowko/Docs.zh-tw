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
ms.openlocfilehash: b8df32745007b2a145d35b8cfcc4cbd2bd17eb33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201729"
---
# <a name="socket-element-network-settings"></a>\<socket> 項目 (網路設定)

指定通訊端作業是否使用完成埠。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a>Syntax  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|**Attribute**|**說明**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|指出通訊端是否應該一律使用完成接受方法呼叫的埠。 預設值是 `false`。|  
|`alwaysUseCompletionPortsForConnect`|指出通訊端是否應該一律使用完成連接方法呼叫的埠。 預設值是 `false`。|  
|`ipProtectionLevel`|指定要用於 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 通訊端的預設值。 預設值取決於 Windows 版本。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|**Element**|**說明**|  
|-----------------|---------------------|  
|[設定](settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## <a name="remarks"></a>備註  

 `alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。 建議將完成埠用於高效能伺服器應用程式。  
  
 和屬性的預設值 `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` 為 **false**。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>可以用來 `alwaysUseCompletionPortsForAccept` 從適用的設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>可以用來 `alwaysUseCompletionPortsForConnect` 從適用的設定檔案取得屬性的目前值。  
  
 `ipProtectionLevel`屬性會指定要用於 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 通訊端的預設值。 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可將 IPv6 通訊端的限制設定為指定的範圍，例如具有相同連結本機或網站本機前置詞的位址。 此選項可讓應用程式在 IPv6 通訊端上放置存取限制。 這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。 此選項可擴大或縮小接聽通訊端的範圍，並在適當時啟用從公用和私用使用者進行無限制的存取，或僅視需要限制存取相同的網站。  
  
 此 `ipProtectionLevel` 屬性設定只會影響初始連入流量：  
  
- TCP 伺服器，接聽通訊端上的連入連線。  
  
- 在通訊端上接收封包的 UDP 應用程式。  
  
 這項設定不會影響已建立的 TCP 連線， (流量在雙向未受限制的情況下) ，而且不會影響傳送 UDP 封包的應用程式。  
  
 屬性設定的可能值會 `ipProtectionLevel` 對應至列舉中所指定的已定義保護層級，如下所示 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ：  
  
|**屬性值**|**說明**|  
|-|-|  
|EdgeRestricted|IP 保護層級有臨界限制。 這個值將由設計在整個網際網路上操作的應用程式所使用。 此項設定不允許使用 Windows Teredo 實作來進行網路位址轉譯 (NAT) 周遊。 這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。 在 Windows Server 2003 和 Windows XP 環境下，通訊端 IP 保護層級的預設值有臨界限制。|  
|Restricted|IP 保護層級有限制。 這個值將由未實作網際網路案例的內部網路應用程式所使用。 這些應用程式通常不會就網路攻擊測試進行測試或是採取強化。 這個設定會將接收傳輸限制於僅連結和本機之間。|  
|不受限制|IP 保護層級不受限制。 這個值將由設計在整個網際網路上操作的應用程式使用，包括發揮已內建在 Windows 之 IPv6 NAT 周遊功能的應用程式 (例如 Teredo)。 這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。 在 Windows Server 2008 R2 和 Windows Vista 環境下，通訊端 IP 保護層級的預設值不受任何限制。|  
|[未指定]|IP 保護層級尚未指定。 在 Windows 7 和 Windows Server 2008 R2 環境下，通訊端 IP 保護層級的預設值尚未指定。|  
  
 未指定屬性的預設值 `ipProtectionLevel` 。 **Unspecified**  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可以用來從適用的設定檔案取得屬性的目前值 `ipProtectionLevel` 。  
  
## <a name="configuration-files"></a>組態檔  

 此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。  
  
## <a name="example"></a>範例  

 下列範例示範如何指定應使用完成埠，而且預設值 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 應該不受限制。  
  
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
