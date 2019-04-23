---
title: 設定網際網路應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: ddc4717c873e65311a8502e66f3edaf39dd89ff9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133798"
---
# <a name="configuring-internet-applications"></a>設定網際網路應用程式
[\<system.Net> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 組態項目包含應用程式的網路組態資訊。 使用 [\<system.Net> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 項目，您可以設定 Proxy 伺服器、設定連線管理參數，以及在應用程式中包含自訂驗證和要求模組。  
  
 [\<defaultProxy> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 項目定義 `GlobalProxySelection` 類別所傳回的 Proxy 伺服器。 任何未將其專屬 <xref:System.Net.HttpWebRequest.Proxy%2A> 屬性設定為特定值的 <xref:System.Net.HttpWebRequest> 都會使用預設 Proxy。 除了設定 Proxy 位址之外，您還可以建立將不會使用 Proxy 的伺服器位址清單，以及指出不應該將 Proxy 用於本機位址。  
  
 請務必注意，Microsoft Internet Explorer 設定是與組態設定一起使用，但優先使用後者。  
  
 下列範例會將預設 Proxy 伺服器位址設定為 `http://proxyserver`、指出不應該將 Proxy 用作本機位址，以及指定對 contoso.com 網域所在伺服器的所有要求都應該略過 Proxy。  
  
```xml  
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
  
 使用 [\<connectionManagement> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) 項目，以設定可對特定伺服器或所有其他伺服器進行的持續連線數目。 下列範例會設定應用程式使用兩個與 `www.contoso.com` 伺服器的持續連線、四個 IP 位址為 192.168.1.2 之伺服器的持續連線，以及一個與所有其他伺服器的持續連線。  
  
```xml  
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
  
 自訂驗證模組是使用 [\<authenticationModules> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) 項目所設定。 自訂驗證模組必須實作 <xref:System.Net.IAuthenticationModule> 介面。  
  
 下列範例設定自訂驗證模組。  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 您可以使用 [\<webRequestModules> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) 項目，設定您的應用程式使用自訂通訊協定特定模組要求來自網際網路資源的資訊。 指定的模組必須實作 <xref:System.Net.IWebRequestCreate> 介面。 您可以在組態檔中指定自訂模組來覆寫預設 HTTP、HTTPS 和檔案要求模組，如下列範例所示。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)
- [網路設定結構描述](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<system.Net> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
