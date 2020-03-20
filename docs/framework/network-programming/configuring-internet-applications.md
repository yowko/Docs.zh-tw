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
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048637"
---
# <a name="configuring-internet-applications"></a>設定網際網路應用程式
[ \<system.Net>元素（網路設置）](../configure-apps/file-schema/network/system-net-element-network-settings.md)配置元素包含應用程式的網路設定資訊。 使用[\<system.Net>元素（網路設置）](../configure-apps/file-schema/network/system-net-element-network-settings.md)元素，可以設置代理伺服器、設置連接管理參數，並在應用程式中包括自訂身份驗證和請求模組。  
  
 [預設代理>元素（網路設置）元素定義類返回的代理伺服器。 \< ](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) `GlobalProxySelection` 任何未將其專屬 <xref:System.Net.HttpWebRequest.Proxy%2A> 屬性設定為特定值的 <xref:System.Net.HttpWebRequest> 都會使用預設 Proxy。 除了設定 Proxy 位址之外，您還可以建立將不會使用 Proxy 的伺服器位址清單，以及指出不應該將 Proxy 用於本機位址。  
  
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
  
 使用[\<連接管理>元素（網路設置）](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)元素配置可連接到特定伺服器或所有其他伺服器的持久連接數。 下列範例會設定應用程式使用兩個與 `www.contoso.com` 伺服器的持續連線、四個 IP 位址為 192.168.1.2 之伺服器的持續連線，以及一個與所有其他伺服器的持續連線。  
  
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
  
 自訂身份驗證模組配置了[\<身份驗證模組>元素（網路設置）](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)元素。 自訂驗證模組必須實作 <xref:System.Net.IAuthenticationModule> 介面。  
  
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
  
 您可以使用[\<WebRequestModule>元素（網路設置）](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)元素來配置應用程式，以便使用特定于協定的自訂模組從 Internet 資源請求資訊。 指定的模組必須實作 <xref:System.Net.IWebRequestCreate> 介面。 您可以在組態檔中指定自訂模組來覆寫預設 HTTP、HTTPS 和檔案要求模組，如下列範例所示。  
  
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

- [.NET 框架中的網路程式設計](index.md)
- [網路設置架構](../configure-apps/file-schema/network/index.md)
- [\<system.Net>元素（網路設置）](../configure-apps/file-schema/network/system-net-element-network-settings.md)
