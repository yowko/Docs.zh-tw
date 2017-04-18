---
title: "&lt;proxy&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<proxy> 項目"
  - "proxy 項目"
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;proxy&gt; 項目 (網路設定)
定義 Proxy 伺服器。  
  
## 語法  
  
```  
  
      <proxy   
  autoDetect="true|false|unspecified"    
  bypassonlocal="true|false|unspecified"   
  proxyaddress="uriString"  
  scriptLocation="uriString"   
  usesystemdefault="true|false|unspecified "   
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`autoDetect`|指定是否自動偵測 Proxy。  預設值是 `unspecified`。|  
|`bypassonlocal`|指定是否略過本機資源的 Proxy。  本機資源包括本機伺服器 \(http:\/\/localhost、http:\/\/loopback 或 http:\/\/127.0.0.1\) 和不帶有句號的 URI \(http:\/\/webserver\)。  預設值是 `unspecified`。|  
|`proxyaddress`|指定要使用的 Proxy URI。|  
|`scriptLocation`|指定組態指令碼的位置。|  
|`usesystemdefault`|指定是否要使用 Internet Explorer Proxy 設定值。  如果設定為 `true`，後續的屬性就會覆寫 Internet Explorer Proxy 設定值。  預設值是 `unspecified`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|設定超文字傳輸協定 \(HTTP\) Proxy 伺服器。|  
  
## 文字值  
  
## 備註  
 `proxy` 項目會定義應用程式的 Proxy 伺服器。  如果組態檔中遺失此項目，.NET Framework 就會使用 Internet Explorer 中的 Proxy 設定值。  
  
 `proxyaddress` 屬性的值必須是語式正確 \(Well\-Formed\) 的 Uniform Resource Indicator \(URI\)。  
  
 `scriptLocation` 屬性是指自動偵測 Proxy 組態指令碼。  如果已在 Internet Explorer 中選取 \[**使用自動組態指令碼**\] 選項，<xref:System.Net.WebProxy> 類別將會嘗試尋找組態指令碼 \(通常叫做 Wpad.dat\)。  
  
 針對要由 .NET Framework 1.1 版移轉至 2.0 版的應用程式使用 `usesystemdefault` 屬性。  
  
 如果 `proxyaddress` 屬性指定無效的預設 Proxy，則會擲回例外狀況。  例外狀況上的 <xref:System.Exception.InnerException%2A> 屬性應該會有造成錯誤之根目錄的詳細資訊。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例會使用 Internet Explorer Proxy 的預設值，指定 Proxy 位址，並且略過本機存取的 Proxy。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)