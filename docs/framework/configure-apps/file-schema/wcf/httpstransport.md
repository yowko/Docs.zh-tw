---
title: '&lt;httpsTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: 14ba18b195fc83d2518aaa39f0fdc69098611a83
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150613"
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
指定 HTTP 傳輸，以傳輸自訂繫結的 SOAP 訊息。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<httpsTransport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                ...
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|allowCookies|布林值，指定用戶端是否接受 Cookie 並在未來要求時傳播 Cookie。 預設為 `false`。<br /><br /> 當您與使用 Cookie 的 ASMX Web 服務互動時，可以使用這個屬性。 如此一來，從伺服器傳回的 Cookie 就一定會自動複製到該服務未來所有的用戶端要求。|  
|authenticationScheme|指定通訊協定，用於驗證由 HTTP 接聽程式處理的用戶端要求。 有效值包括以下的值：<br /><br /> 摘要：指定摘要式驗證。<br />-Negotiate:會與用戶端決定驗證配置來進行交涉。 如果用戶端和伺服器都支援 Kerberos，就使用它，否則使用 NTLM。<br />-Ntlm:指定 NTLM 驗證。<br />-基本：指定基本驗證。<br />匿名：指定匿名驗證。<br /><br /> 預設值為 Anonymous。 此屬性的型別為 <xref:System.Net.AuthenticationSchemes>。 這個屬性只可以設定一次。|  
|bypassProxyOnLocal|布林值，指出本機位址是否略過 Proxy 伺服器。 預設為 `false`。<br /><br /> 本機位址是位於本機 LAN 或內部網路上的位址。<br /><br /> Windows Communication Foundation (WCF) 一律忽略 proxy，如果服務位址開頭 `http://localhost` 。<br /><br /> 如果您希望用戶端在與相同電腦上的服務進行交談時通過 Proxy，應使用主機名稱而非 localhost。|  
|hostnameComparisonMode|指定用於剖析 URI 的 HTTP 主機名稱比較模式。 有效值為：<br /><br /> -StrongWildcard: （"+"） 符合指定的配置、 連接埠和相對 URI 的內容中所有可能的主機名稱。<br />-完全： 無萬用字元。<br />-WeakWildcard: ("\*") 比對所有可能的主機名稱中指定的配置、 連接埠和相對 UIR 都未明確符合或透過強式萬用字元機制的內容。<br /><br /> 預設為 StrongWildcard。 此屬性的型別為 `System.ServiceModel.HostnameComparison`。|  
|manualAddressing|布林值，讓使用者能夠控制訊息定址。 這個屬性通常用於路由器案例，其中應用程式會決定要將訊息傳送到其中一個目的端。<br /><br /> 設定為 `true` 時，通道會假設訊息已經定址，並且不會加入任何其他的資訊。 接著使用者可個別定址每一個訊息。<br /><br /> 設定為 `false` 時，預設的 Windows Communication Foundation (WCF) 定址機制會自動為所有訊息建立位址。<br /><br /> 預設為 `false`。|  
|maxBufferPoolSize|正整數，指定緩衝集區的大小上限。 預設值為 524288。<br /><br /> WCF 有許多組件會使用緩衝區。 每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。 有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區， 因此可以避免建立及終結緩衝區的負荷。|  
|maxBufferSize|正整數，指定緩衝區的大小上限。 預設為 524288。|  
|maxReceivedMessageSize|正整數，指定可接收的可允許訊息大小上限。 預設值為 65536。|  
|proxyAddress|指定 HTTP Proxy 位址的 URI。 如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。 預設為 `null`。|  
|proxyAuthenticationScheme|指定通訊協定，用於驗證由 HTTP Proxy 處理的用戶端要求。 有效值包括以下的值：<br /><br /> -None:未執行驗證。<br />摘要：指定摘要式驗證。<br />-Negotiate:會與用戶端決定驗證配置來進行交涉。 如果用戶端和伺服器都支援 Kerberos，就使用它，否則使用 NTLM。<br />-Ntlm:指定 NTLM 驗證。<br />-基本：指定基本驗證。<br />匿名：指定匿名驗證。<br />-IntegratedWindowsAuthentication:指定 Windows 驗證。<br /><br /> 預設值為 Anonymous。 此屬性的型別為 <xref:System.Net.AuthenticationSchemes>。|  
|realm|字串，指定在 Proxy/伺服器上使用的領域。 預設為空字串。<br /><br /> 伺服器使用領域來分割受保護的資源。 每個分割都可以有自己的驗證配置和 (或) 授權資料庫。 領域只限於基本和摘要式驗證使用。 當用戶端成功驗證之後，驗證對指定領域中的所有資源都有效。 領域的詳細說明，請參閱在 RFC 2617 [IETF 網站](https://www.ietf.org)。|  
|requireClientCertificate|布林值，指定伺服器是否需要用戶端提供用戶端憑證做為 HTTPS 信號交換的一部分。 預設為 `false`。|  
|transferMode|指定訊息是否要經過緩衝處理或資料流處理，或為要求或回應。 有效值包括以下的值：<br /><br /> 緩衝處理：要求和回應訊息會進行緩衝處理。<br />資料流：串流處理的要求和回應訊息。<br />-StreamedRequest:資料流處理要求訊息，緩衝處理回應訊息。<br />-StreamedResponse:緩衝處理要求訊息，資料流處理回應訊息。<br /><br /> 預設為 Buffered。 此屬性的型別為 <xref:System.ServiceModel.TransferMode>。|  
|unsafeConnectionNtlmAuthentication|布林值，指定是否已在伺服器啟用「不安全的連線共用」。 預設為 `false`。 如果已啟用，NTLM 驗證會在各 TCP 連線上執行一次。|  
|useDefaultWebProxy|布林值，指定是否使用整部機器 Proxy 設定而非使用者特定設定。 預設為 `true`。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 `httpsTransport` 項目是建立自訂繫結時的起點，此繫結會實作 HTTPS 傳輸通訊協定。 HTTPS 是用於安全互通性目的的主要傳輸。 藉由 Windows Communication Foundation (WCF) 以確保與其他 Web 服務堆疊互通時，會支援 HTTPS。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.HttpsTransportElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [傳輸](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [選擇傳輸](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
