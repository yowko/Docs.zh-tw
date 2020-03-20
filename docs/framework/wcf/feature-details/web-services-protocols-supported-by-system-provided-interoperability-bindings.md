---
title: 系統提供的互通性繫結所支援的 Web 服務通訊協定
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: a1e67401a09370a46bc7a3e8546c95467bc18b67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184138"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>系統提供的互通性繫結所支援的 Web 服務通訊協定
Windows 通信基礎 （WCF） 旨在與支援一組稱為 Web 服務規範的規範的 Web 服務進行交互操作。 為了簡化互通性最佳實踐的服務配置，WCF 引入了三個可交互操作的系統提供的綁定：<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>和<xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>。 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 為了與結構化資訊標準 （OASIS） 組織的標準進行互通性，WCF 包括一個可交互操作的系統提供的綁定： <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>。 對於中繼資料發佈，WCF 包括兩個可交互操作的系統提供的綁定[\<：mexHttp綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)和[\<mexHttps綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)。 本主題列出系統提供之繫結支援的規格。  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding、wsHttpBinding、ws2007HttpBinding 和 wsDualHttpBinding 繫結支援的 Web 服務通訊協定  
  
### <a name="all-bindings"></a>所有繫結  
 [ \<基本HTTPBinding>，wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，和[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)綁定支援以下協定。  
  
> [!NOTE]
> 如需用於發行中繼資料之繫結的詳細資訊，請參閱本主題中稍後的「系統提供之中繼資料繫結」一節。  
  
|類別|通訊協定|規格和用法|  
|--------------|--------------|-----------------------------|  
|傳輸|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`、`WSHttpBinding` 和 `WS2007HttpBinding` 使用 HTTP 和 HTTPS 傳輸。|  
|Messaging (傳訊)|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`、`wsHttpBinding` 和 `ws2007HttpBinding` 支援訊息傳輸最佳化機制 (MTOM)。 預設不使用。 若要使用 MTOM，請將 `messageEncoding` 屬性設為 `"Mtom"`。<br /><br /> 範例：<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|中繼資料|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF 使用 Web 服務描述語言 （WSDL） 來描述服務。|  
|中繼資料|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF 使用 WS-策略規範以及特定于域的斷言來描述服務要求和功能。|  
|中繼資料|WS-Policy 1.5|[WS-Policy 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF 使用 WS-策略規範以及特定于域的斷言來描述服務要求和功能。|  
|中繼資料|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF 實現 WS-策略附件，以在 Web 服務描述語言 （WSDL） 中的各種作用域中附加策略運算式。|  
|中繼資料|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF 實現 WS-中繼資料交換以檢索 XML 架構、WSDL 和 WS-Policy。|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|類別|通訊協定|規格和用法|  
|--------------|--------------|-----------------------------|  
|Messaging (傳訊)|SOAP 1.1|[SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> 為了與 Basic Profile 1.1 保持一致，`basicHttpBinding` 項目實作 SOAP 1.1 訊息通訊協定。|  
|安全性|WSS SOAP 訊息安全性 1.0|[WSS SOAP 訊息安全性 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> 為了與 Basic Security Profile 保持一致，`basicHttpBinding` 項目實作 Web 服務安全性 (WSS) SOAP 訊息安全性 1.0 規格，以用於使用者名稱/密碼和 X.509 型的安全性。<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|安全性|WSS SOAP 訊息安全性 UsernameToken 設定檔 1.0|[WSS SOAP 訊息安全性 UsernameToken 設定檔 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|安全性|WSS SOAP 訊息安全 X.509 憑證權杖設定檔 1.0|[WSS SOAP 訊息安全 X.509 憑證權杖設定檔 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding、ws2007HttpBinding 和 wsDualHttpBinding  
  
|類別|通訊協定|規格和用法|  
|--------------|--------------|-----------------------------|  
|Messaging (傳訊)|SOAP 1.2|[門](https://www.w3.org/TR/soap12-part0/)<br /><br /> [訊息架構](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [附加 (包括 HTTP 繫結)](https://www.w3.org/TR/soap12-part2/)|  
|Messaging (傳訊)|WS-定址 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web 服務定址 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`、`ws2007HttpBinding` 和 `wsDualHttpBinding` 會實作全球資訊網協會 (W3C) WS-Addressing 建議，以啟用非同步訊息、訊息相互關聯和傳輸中性的定址機制。<br /><br /> 雖然 WS-* 規格允許 WS-Addressing 標頭加密，但是 WCF 並不提供這項支援。|  
|Messaging (傳訊)|WS-Addressing 1.0 - 中繼資料|[WS 定址 1.0 中繼資料](https://www.w3.org/2007/05/addressing/metadata/)通過在 ServiceMetadata 行為中設置策略版本來啟用對此協定的支援 - 策略版本設置為 1.2（預設值），wsdl 描述項合 WS-定址 wsdl，策略版本設置為 1.5，wsdl 描述項合 ws 定址中繼資料。<br /><br /> 雖然 WS-* 規格允許 WS-Addressing 標頭加密，但是 WCF 並不提供這項支援。|  
|安全性|WSS SOAP 訊息安全性 1.0|[WSS SOAP 訊息安全性 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> `securityMode` 屬性設為 "wsSecurityOverHttp" (預設值) 且使用 `wsSecurity` 子項目設定參數時使用。<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|安全性|WSS SOAP 訊息安全使用者名權杖設定檔 1.1|[WSS SOAP 訊息安全性 UsernameToken 設定檔 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> `wsSecurity` 項目的 `authenticationMode` 屬性設為 "Username" 時使用。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|安全性|WSS SOAP 訊息安全性 X.509 憑證權杖設定檔 1.1|[WSS SOAP 訊息安全性 X.509 憑證權杖設定檔 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> 用於在 `wsSecurity` 項目的 `authenticationMode` 屬性設為 "Username"、"Certificate" 或 "None" 時保護訊息。 此外，當 `wsSecurity` 項目的 `authenticationMode` 屬性設為 "Certificate" 時，請使用此規格進行用戶端驗證。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|安全性|WSS SOAP 訊息安全性 Kerberos 權杖設定檔 1.1|[WSS SOAP 訊息安全 Kerberos 權杖設定檔 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> 用於在 `wsSecurity` 項目的 `authenticationMode` 屬性設為 "Windows" 時進行驗證和保護訊息。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|安全性|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> 用於當 `security/@mode` 屬性設為 "Message"，且 `message/@establishSecurityContext` 屬性設為 "true" (預設值) 時提供安全的工作階段。|  
|安全性|WS-Trust|[WS-信任](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> WS-SecureConversation (請參閱前述) 所使用。|  
|可信賴傳訊|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> 當繫結設定為使用 `reliableSession` 時使用。<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|交易|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> 用於交易管理員之間的通訊。 WCF 用戶端和服務始終使用本地交易管理員。|  
|交易|WS-Coordination|[WS-Coordination](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> 用於當 `flowTransactions` 屬性設為 "Allowed" 或 "Required" 時流動異動內容。<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding 和 ws2007FederationHttpBinding  
 [ \<引入 wsFederatHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)和[\<ws2007 聯邦HTTPBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)元素是為了支援聯合方案，其中協力廠商發出用於驗證用戶端的權杖。 除了 `wsHttpBinding` 使用的通訊協定外，`wsFederationHttpBinding` 還使用：  
  
- `WS-Trust`，進行權杖發行。  
  
- WSS 安全性判斷提示標記語言 (SAML) 權杖設定檔 1.0 和 1.1，適用於最常見的發行權杖格式。  
  
 範例：  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 有關詳細資訊，請參閱[聯合](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
## <a name="system-provided-metadata-bindings"></a>系統提供之中繼資料繫結  
 下表說明系統提供之互通中繼資料繫結所支援的通訊協定，該繫結由 <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> 類別公開。  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 mexHttp綁定>綁定支援以下協定。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) 有關使用此綁定的詳細資訊，請參閱[發佈中繼資料](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)。  
  
|類別|通訊協定|規格和用法|  
|--------------|--------------|-----------------------------|  
|傳輸|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Messaging (傳訊)|SOAP 1.2|[門](https://www.w3.org/TR/soap12-part0/)<br /><br /> [訊息架構](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [附加 (包括 HTTP 繫結)](https://www.w3.org/TR/soap12-part2/)|  
|Messaging (傳訊)|WS-定址 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web 服務定址 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|中繼資料|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF 實現 WS-中繼資料交換以檢索 XML 架構、WSDL 和 WS-Policy。|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttps綁定>支援以下協定。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) 有關使用此綁定的詳細資訊，請參閱[發佈中繼資料](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)。  
  
|類別|通訊協定|規格和用法|  
|--------------|--------------|-----------------------------|  
|傳輸|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> 已啟用傳輸安全性。|  
|Messaging (傳訊)|SOAP 1.2|[門](https://www.w3.org/TR/soap12-part0/)<br /><br /> [訊息架構](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [附加 (包括 HTTP 繫結)](https://www.w3.org/TR/soap12-part2/)|  
|Messaging (傳訊)|WS-定址 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web 服務定址 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|中繼資料|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF 實現 WS-中繼資料交換以檢索 XML 架構、WSDL 和 WS-Policy。|  
  
## <a name="see-also"></a>另請參閱

- [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<基本HTTP綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttp綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttp綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttps綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttp 綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
