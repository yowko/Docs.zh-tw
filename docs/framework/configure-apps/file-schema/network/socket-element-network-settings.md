---
title: "&lt;socket&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#socket"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<socket> 項目"
  - "socket 項目"
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;socket&gt; 項目 (網路設定)
指定通訊端操作是否使用完成通訊埠。  
  
## 語法  
  
```  
  
      <socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel ="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/socket>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**說明**|  
|------------|------------|  
|`alwaysUseCompletionPortsForAccept`|指出通訊端是否應該永遠使用完成通訊埠用於接受方法呼叫。  預設值是 `false`。|  
|`alwaysUseCompletionPortsForConnect`|指出通訊端是否應該永遠使用完成通訊埠用於連接方法呼叫。  預設值是 `false`。|  
|`ipProtectionLevel`|指定通訊端所使用的預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>。  預設值取決於 Windows 的版本。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
 `alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與透過 <xref:System.Net.Sockets?displayProperty=fullName> 中的類別來使用完成通訊埠有關的預設行為。  但是建議您針對高效能的伺服器應用程式使用完成通訊埠。  
  
 `alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性的預設值為 **false**。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> 可用來從適用的組態檔中取得 `alwaysUseCompletionPortsForAccept` 屬性的目前值。  <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> 可用來從適用的組態檔中取得 `alwaysUseCompletionPortsForConnect` 屬性的目前值。  
  
 `ipProtectionLevel` 屬性會指定預設的 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> 供通訊端使用。  <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> 屬性允許將 IPv6 通訊端限制在指定的範圍，例如含有同一個連結本機或站台本機前置詞的位址。  此選項可讓應用程式在 IPv6 通訊端上設置存取限制。  這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。  這個選項可放大或縮小接聽通訊端的範圍，根據需要啟用公用和私用使用者的無限制存取，或視需要限制成僅可存取相同的站台。  
  
 此 `ipProtectionLevel` 屬性設定只會影響初始的傳入流量：  
  
-   在通訊端上接聽連入連線的 TCP 伺服器。  
  
-   在通訊端上接收封包的 UDP 應用程式。  
  
 這個組態設定不會影響已經建立的 TCP 連線 \(雙向的流量均無限制\)，也不會影響傳送 UDP 封包的應用程式。  
  
 `ipProtectionLevel` 屬性設定的可能值會與 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> 列舉中指定的已定義保護層級對應，如下所示：  
  
|||  
|-|-|  
|**屬性值**|**說明**|  
|EdgeRestricted|IP 保護層級有臨界限制。  這個值將由設計在整個網際網路上操作的應用程式所使用。  此項設定不允許使用 Windows Teredo 實作來進行網路位址轉譯 \(NAT\) 周遊。  這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。  在 Windows Server 2003 和 Windows XP 環境下，通訊端 IP 保護層級的預設值有臨界限制。|  
|Restricted|IP 保護層級有限制。  這個值將由未實作網際網路案例的內部網路應用程式所使用。  這些應用程式通常不會就網路攻擊測試進行測試或是採取強化。  這個設定會將接收傳輸限制於僅連結和本機之間。|  
|不受限|IP 保護層級不受限制。  這個值將由設計在整個網際網路上操作的應用程式使用，包括發揮已內建在 Windows 之 IPv6 NAT 周遊功能的應用程式 \(例如 Teredo\)。  這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。  在 Windows Server 2008 R2 和 Windows Vista 環境下，通訊端 IP 保護層級的預設值不受任何限制。|  
|Unspecified|IP 保護層級尚未指定。  在 Windows 7 和 Windows Server 2008 R2 環境下，通訊端 IP 保護層級的預設值尚未指定。|  
  
 `ipProtectionLevel` 屬性的預設值為 **Unspecified**。  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> 屬性可用來從適用的組態檔中取得 `ipProtectionLevel` 屬性的目前值。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例示範如何指定應該使用的完成通訊埠，以及預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName> 不應該受到限制。  
  
```  
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
  
## 請參閱  
 <xref:System.Net?displayProperty=fullName>   
 <xref:System.Net.Configuration.SocketElement?displayProperty=fullName>   
 <xref:System.Net.Sockets?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)