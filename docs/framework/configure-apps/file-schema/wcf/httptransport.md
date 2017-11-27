---
title: '&lt;httpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6aacdb254b12e5c1b344b43c2fbf2e94681c1f6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
指定 HTTP 傳輸，以傳輸自訂繫結的 SOAP 訊息。  
  
 \<system.serviceModel >  
\<繫結 >  
\<customBinding >  
\<繫結 >  
\<httpTransport >  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
    realm="String"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
        useDefaultWebProxy="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|allowCookies|布林值，指定用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。 預設為 `false`。<br /><br /> 當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。 如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。|  
|authenticationScheme|指定通訊協定，用於驗證由 HTTP 接聽程式處理的用戶端要求。 有效值包括以下的值：<br /><br /> -Digest： 指定摘要式驗證。<br />-Negotiate： 與用戶端決定驗證配置進行交涉。 如果用戶端和伺服器都支援 Kerberos，就使用它，否則使用 NTLM。<br />-Ntlm： 指定 NTLM 驗證。<br />-基本： 指定基本驗證。<br />匿名： 指定匿名驗證。<br /><br /> 預設值為 Anonymous。 此屬性的型別為 <xref:System.Net.AuthenticationSchemes>。 這個屬性只可以設定一次。|  
|bypassProxyOnLocal|布林值，指出本機位址是否略過 Proxy 伺服器。 預設為 `false`。<br /><br /> 本機位址是位於本機 LAN 或內部網路上的位址。<br /><br /> 如果服務位址是以 http://localhost 開頭，[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 一律忽略 Proxy。<br /><br /> 如果您希望用戶端在與相同電腦上的服務進行交談時通過 Proxy，應使用主機名稱而非 localhost。|  
|hostnameComparisonMode|指定用於剖析 URI 的 HTTP 主機名稱比較模式。 有效值為：<br /><br /> -StrongWildcard: （"+"） 比對指定的配置、 連接埠和相對 URI 的內容中所有可能的主機名稱。<br />-完全： 無萬用字元。<br />-WeakWildcard: ("*") 必須符合指定的配置、 連接埠和相對 UIR 有不尚未明確比對或透過強式萬用字元機制的內容中的所有可能主機名稱。<br /><br /> 預設為 StrongWildcard。 此屬性的型別為 `System.ServiceModel.HostnameComparisonMode`。|  
|keepAliveEnabled|布林值，指定是否要與網際網路資源建立持續連線。|  
|maxBufferSize|正整數，指定緩衝區的大小上限。 預設為 524288。|  
|proxyAddress|指定 HTTP Proxy 位址的 URI。 如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。 預設為 `null`。|  
|proxyAuthenticationScheme|指定通訊協定，用於驗證由 HTTP Proxy 處理的用戶端要求。 有效值包括以下的值：<br /><br /> -無： 未執行驗證。<br />-Digest： 指定摘要式驗證。<br />-Negotiate： 與用戶端決定驗證配置進行交涉。 如果用戶端和伺服器都支援 Kerberos，就使用它，否則使用 NTLM。<br />-Ntlm： 指定 NTLM 驗證。<br />-基本： 指定基本驗證。<br />匿名： 指定匿名驗證。<br />-IntegratedWindowsAuthentication： 指定 Windows 驗證。<br /><br /> 預設值為 Anonymous。 此屬性的型別為 <xref:System.Net.AuthenticationSchemes>。|  
|realm|字串，指定在 Proxy/伺服器上使用的領域。 預設為空字串。<br /><br /> 伺服器使用領域來分割受保護的資源。 每個分割都可以有自己的驗證配置和 (或) 授權資料庫。 領域只限於基本和摘要式驗證使用。 當用戶端成功驗證之後，驗證對指定領域中的所有資源都有效。 如需領域的詳細說明，請參閱 RFC 2617，網址為 http://www.ietf.org。|  
|transferMode|指定訊息是否要經過緩衝處理或資料流處理，或為要求或回應。 有效值包括以下的值：<br /><br /> 緩衝： 緩衝要求和回應訊息。<br />資料流： 進行串流的要求和回應訊息。<br />-StreamedRequest： 要求訊息資料流處理，並緩衝處理回應訊息。<br />-StreamedResponse： 緩衝處理要求訊息和回應訊息資料流處理。<br /><br /> 預設為 Buffered。 此屬性的型別為 <xref:System.ServiceModel.TransferMode>。|  
|unsafeConnectionNtlmAuthentication|布林值，指定是否已在伺服器啟用「不安全的連線共用」。 預設為 `false`。 如果已啟用，NTLM 驗證會在各 TCP 連線上執行一次。|  
|useDefaultWebProxy|布林值，指定是否使用整部機器 Proxy 設定而非使用者特定設定。 預設為 `true`。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 `httpTransport` 項目是在建立自訂繫結時的起點，該繫結會實作 HTTP 傳輸通訊協定。 HTTP 是用於互通性目的的主要傳輸。 這個傳輸是由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 支援，可確保與其他非 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Web 服務堆疊之間的互通性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
