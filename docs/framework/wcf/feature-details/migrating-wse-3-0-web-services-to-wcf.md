---
title: 從 WSE 3.0 Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: fea56d5737b47dabd5632477b7daed23fcfaf249
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>從 WSE 3.0 Web 服務移轉至 WCF
WSE 3.0 Web 服務移轉到 Windows Communication Foundation (WCF) 的優點包括改善的效能和的支援其他傳輸、 其他安全案例，以及 WS-* 規格。 從 WSE 3.0 移轉至 WCF Web 服務可以感受到 200%到 400%的效能改進。 如需 WCF 支援的傳輸的詳細資訊，請參閱[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。 如需 WCF 支援的案例，請參閱[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 如需 WCF 支援的規格的清單，請參閱[Web 服務通訊協定互通性手冊](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)。  
  
 下列各節提供如何將 WSE 3.0 Web 服務的特定功能移轉至 WCF 的指引。  
  
## <a name="general"></a>一般  
 WSE 3.0 與 WCF 應用程式包含連線層級的互通性與一般的用語集。 WSE 3.0 與 WCF 應用程式是網路層級互通根據設定的 WS-* 規格，同時支援。 在 WSE 3.0 或 WCF 應用程式開發時沒有一組常用的術語，例如 WSE 和驗證模式中的通行安全性判斷提示的名稱。  
  
 雖然有許多類似之間 WCF 和 ASP.NET 或 WSE 3.0 程式設計模型，它們是不同。 如需有關 WCF 程式設計模型的詳細資訊，請參閱[基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)。  
  
> [!NOTE]
>  將 WSE Web 服務移轉至 WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具可以用來產生用戶端。 然而，該用戶端同時內含可用來做為 WCF 服務起點的介面與類別。 產生的介面會將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用到合約成員 (同時將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設為 `*`)。 當 WSE 用戶端呼叫 Web 服務使用這項設定時，會擲回下列例外狀況： **Web.Services3.ResponseProcessingException: WSE910： 回應訊息，在處理期間發生錯誤，您可以找到內部錯誤例外狀況**。 若要緩解這個情況，請將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性 (Property) 設為非 `null` 值，例如 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`。  
  
## <a name="security"></a>安全性  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>使用原則檔來保護安全的 WSE 3.0 Web 服務  
 WCF 服務可以使用組態檔來保護服務，且該機制與 WSE 3.0 原則檔類似。 在 WSE 3.0 中，當您使用原則檔來保護 Web 服務安全時，可以使用通行安全性判斷提示或自訂原則判斷提示來進行。 通行安全性判斷提示會緊密地對應至 WCF 的安全性繫結項目的驗證模式。 不只 WCF 驗證模式和 WSE 3.0 通行安全性判斷提示名稱相同，或同樣地，它們所保護的訊息使用相同的認證類型。 比方說，`usernameForCertificate`在 WSE 3.0 通行安全性判斷提示對應至`UsernameForCertificate`WCF 中的驗證模式。 下列程式碼範例示範使用最小原則如何`usernameForCertificate`在 WSE 3.0 通行安全性判斷提示對應至`UsernameForCertificate`在 WCF 自訂繫結中的驗證模式。  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 若要移轉至 WCF 的原則檔中指定的 WSE 3.0 Web 服務安全性設定，必須建立自訂繫結組態檔中，並將通行安全性判斷提示必須設為其相等的驗證模式。 另外，自訂繫結必須設定為使用 August 2004 WS-Addressing 規格，以便 WSE 3.0 用戶端與服務進行通訊。 當移轉的 WCF 服務不需要與 WSE 3.0 用戶端通訊，而且只須維護安全性同位檢查時，請考慮使用適當的安全性設定，而不是建立自訂繫結的 WCF 系統定義繫結。  
  
 下表將列出 WSE 3.0 原則檔和 WCF 中相等的自訂繫結之間的對應。  
  
|WSE 3.0 組合安全性判斷提示|WCF 自訂繫結組態|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 如需有關如何在 WCF 中建立自訂繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>使用應用程式程式碼來保護安全的 WSE 3.0 Web 服務  
 是否使用 WSE 3.0 或 WCF，安全性需求可以指定應用程式程式碼，而不是在組態中。 在 WSE 3.0 中，您可以建立衍生自 `Policy` 類別的類別，然後呼叫 `Add` 方法來新增需求以達到這個目的。 如需有關程式碼中指定的安全性需求的詳細資訊，請參閱[How to： 安全 Web 服務沒有使用原則檔](http://go.microsoft.com/fwlink/?LinkId=73747)。 在 WCF 中，若要在程式碼中指定安全性需求，建立的執行個體<xref:System.ServiceModel.Channels.BindingElementCollection>類別，然後將執行個體<xref:System.ServiceModel.Channels.SecurityBindingElement>至<xref:System.ServiceModel.Channels.BindingElementCollection>。 安全性判斷提示需求可透過 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的靜態驗證模式協助程式方法來加以設定。 如需有關使用 WCF 程式碼中指定安全性需求的詳細資訊，請參閱[How to: 自訂繫結使用 SecurityBindingElement 建立](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)和[How to: 指定建立 SecurityBindingElement驗證模式](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 自訂原則判斷提示  
 在 WSE 3.0 中，有兩種自訂原則判斷提示類型：分別是用來保護 SOAP 訊息安全的原則判斷提示，以及無法保護 SOAP 訊息安全的原則判斷提示。 保護 SOAP 訊息安全的原則判斷提示衍生自 WSE 3.0`SecurityPolicyAssertion`類別和概念上的等同於在 WCF 中是<xref:System.ServiceModel.Channels.SecurityBindingElement>類別。  
  
 要注意的重點是，WSE 3.0 通行安全性判斷提示是 WCF 驗證模式的子集。 如果您已在 WSE 3.0 中建立自訂原則判斷提示，可能是相等的 WCF 驗證模式。 例如，WSE 3.0 不會提供等同於 `UsernameOverTransport` 通行安全性判斷提示的 CertificateOverTransport 安全性判斷提示，但會使用 X.509 憑證來執行用戶端驗證。 如果您已經定義自己的自訂原則判斷提示，此案例中，WCF 將會直接移轉。 WCF 定義此案例中，驗證模式，因此您可以利用靜態驗證模式協助程式方法，若要設定 WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
 當不相等來保護 SOAP 訊息安全之自訂原則判斷提示的 WCF 驗證模式時，衍生自<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>，<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>或<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF 類別，並指定相等的繫結項目。 如需詳細資訊，請參閱[How to： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
 若要轉換不保護 SOAP 訊息的自訂原則判斷提示，請參閱[篩選](../../../../docs/framework/wcf/feature-details/filtering.md)和範例[自訂訊息攔截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 自訂安全性權杖  
 建立自訂權杖的 WCF 程式設計模型是與 WSE 3.0 不同。 如需有關在 WSE 中建立自訂權杖的詳細資訊，請參閱[建立自訂安全性權杖](http://go.microsoft.com/fwlink/?LinkID=73750)。 如需有關在 WCF 中建立自訂權杖的詳細資訊，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 自訂權杖管理員  
 建立自訂權杖管理員的程式設計模型是在 WCF 中與 WSE 3.0 不同。 如需有關如何建立自訂權杖管理員和其他元件所需的自訂安全性權杖的詳細資訊，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
> [!NOTE]
>  如果您已經建立自訂`UsernameToken`安全性權杖管理員，WCF 會提供機制讓您輕鬆指定驗證邏輯，而不用建立自訂安全性權杖管理員。 如需詳細資訊，請參閱[How to： 使用自訂使用者名稱和密碼驗證程式](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>使用 MTOM 編碼 SOAP 訊息的 WSE 3.0 Web 服務  
 就像 WSE 3 應用程式的 WCF 應用程式可以指定 MTOM 訊息編碼組態中。 若要移轉這個設定，加入[ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)服務的繫結。 下列程式碼範例示範如何指定 MTOM 編碼在 WSE 3.0 服務在 WCF 中的相等。  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>訊息  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>使用 WSE 訊息 API 的 WSE 3.0 應用程式  
 當您使用 WSE 訊息 API 來直接存取於用戶端與 Web 服務之間進行通訊的 XML 時，可以將應用程式轉換為使用 "Plain Old XML" (POX)。 如需 POX 的詳細資訊，請參閱[與 POX 應用程式的互通性](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)。 如需 WSE 訊息 API 的詳細資訊，請參閱[傳送和接收 SOAP 訊息使用 WSE 訊息 API](http://go.microsoft.com/fwlink/?LinkID=73755)。  
  
## <a name="transports"></a>傳輸  
  
### <a name="tcp"></a>TCP  
 根據預設，WSE 3.0 用戶端和 Web 服務傳送 SOAP 訊息使用 TCP 傳輸的不會與 WCF 用戶端和 Web 服務互通。 這種不相容情況是因為 TCP 通訊協定中使用的框架處理方式差異以及效能因素所導致。 不過，WCF 範例詳細說明如何實作可與 WSE 3.0 互通的自訂 TCP 工作階段。 如需有關這個範例的詳細資訊，請參閱[傳輸： WSE 3.0 TCP 互通性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)。  
  
 若要指定 WCF 應用程式使用 TCP 傳輸，請使用[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
### <a name="custom-transport"></a>自訂傳輸  
 WSE 3.0 自訂傳輸在 WCF 中的對等即為通道延伸。 如需有關建立通道擴充功能的詳細資訊，請參閱[擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [如何：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [如何：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
