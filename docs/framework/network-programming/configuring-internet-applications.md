---
title: "設定網際網路應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "下載網際網路資源，預設的 Proxy"
  - "傳送資料，預設的 Proxy"
  - "接收資料，預設的 Proxy"
  - "下載網際網路資源，設定網際網路應用程式"
  - "特定通訊協定的模組"
  - "自訂驗證模組"
  - "接收資料，設定網際網路應用程式"
  - "組態設定 [.NET Framework]，網際網路應用程式"
  - "從網際網路要求資料，設定網際網路應用程式"
  - "從網際網路要求資料，預設的 Proxy"
  - "回應網際網路要求，預設的 Proxy"
  - "網際網路，設定網際網路應用程式"
  - "回應網際網路要求，設定網際網路應用程式"
  - "預設的 Proxy"
  - "網路資源，預設的 Proxy"
  - "傳送資料，設定網際網路應用程式"
  - "網路資源，設定網際網路應用程式"
  - "網際網路，預設的 Proxy"
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 設定網際網路應用程式
[\<system.net\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 組態項目包含應用程式的網路組態資訊。  使用 [\<system.net\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 項目，您可以在應用程式中設定 Proxy 伺服器，將連結管理參數，並將自訂驗證和要求模組。  
  
 [\<defaultProxy\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 項目定義 `GlobalProxySelection` 類別傳回的 Proxy 伺服器。  所有 <xref:System.Net.HttpWebRequest> 沒有自己的 <xref:System.Net.HttpWebRequest.Proxy%2A> 屬性設為的特定值使用預設的 Proxy。  除了設定 Proxy 位址以外，您也可以建立不使用 Proxy 伺服器的位址清單，然後，您可以指示不應該為本機位址使用 Proxy。  
  
 請注意， Microsoft Internet Explorer 管理員設定合併組態設定是很重要的，使用後一個採用的優先順序。  
  
 下列範例會將預設 Proxy 伺服器的位址為 http:\/\/proxyserver，指示不應該為本機位址使用 Proxy，並指定要將 contoso.com 網域中所有伺服器的要求應該略過 Proxy。  
  
```  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 使用 [\<connectionManagement\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) 項目配置可以建置至特定伺服器或其他伺服器持續連線數目。  下列範例會設定應用程式使用 www.contoso.com 伺服器的兩個持續性連線，與伺服器的四個持續性連線與 IP 位址 192.168.1.2 和其他伺服器控制項的永續性 \(Persistent\) 連接。  
  
```  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 自訂驗證模組所設定 [\<authenticationModules\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) 項目。  自訂驗證模組必須實作介面 <xref:System.Net.IAuthenticationModule> 。  
  
 下列範例設定自訂的驗證模組。  
  
```  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 您可以使用 [\<webRequestModules\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) 項目將應用程式設定為使用自訂通訊協定專屬模組從網際網路資源要求的資訊。  指定的模組必須實作介面 <xref:System.Net.IWebRequestCreate> 。  您可以指定自己的自訂模組會覆寫預設的 HTTP、HTTPS 和檔案要求模組在組態檔中，如下列範例所示。  
  
```  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## 請參閱  
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)   
 [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<system.net\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)