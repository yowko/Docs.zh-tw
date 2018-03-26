---
title: 從 WSE 3.0 Web 服務移轉至 WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7e7187eb6ed444ba2c28aa301ce4b3b16129030
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>從 WSE 3.0 Web 服務移轉至 WCF
從 WSE 3.0 Web 服務移轉至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的好處，包括更好的效能、對其他傳輸、其他安全案例，以及 WS-* 規格的支援。 從 WSE 3.0 移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 Web 服務可以感受到 200% 到 400% 的效能提升。 如需有關所支援的傳輸[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。 如需所支援的案例的清單[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 如需所支援的規格的清單[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[Web 服務通訊協定互通性手冊](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)。  
  
 下列各節將提供指南，說明如何將 WSE 3.0 Web 服務的特定功能移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
## <a name="general"></a>一般  
 WSE 3.0 與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式包含連線層級的互通性與一般的用語集。 WSE 3.0 與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式根據同時支援的 WS-* 規格可以在連線層級上互通。 一旦開發出 WSE 3.0 或 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式，會產生一般的用語集，例如 WSE 中的通行安全性判斷提示名稱以及驗證模式。  
  
 儘管 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和 ASP.NET 或 WSE 3.0 程式設計模型之間有許多類似之處，其本質仍然不同。 如需詳細資訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]程式設計模型，請參閱[基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)。  
  
> [!NOTE]
>  將 WSE Web 服務移轉至 WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具可以用來產生用戶端。 然而，該用戶端同時內含可用來做為 WCF 服務起點的介面與類別。 產生的介面會將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用到合約成員 (同時將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設為 `*`)。 當 WSE 用戶端呼叫 Web 服務使用這項設定時，會擲回下列例外狀況： **Web.Services3.ResponseProcessingException: WSE910： 回應訊息，在處理期間發生錯誤，您可以找到內部錯誤例外狀況**。 若要緩解這個情況，請將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性 (Property) 設為非 `null` 值，例如 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`。  
  
## <a name="security"></a>安全性  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>使用原則檔來保護安全的 WSE 3.0 Web 服務  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務可以使用組態檔來保護服務安全，且該機制與 WSE 3.0 原則檔類似。 在 WSE 3.0 中，當您使用原則檔來保護 Web 服務安全時，可以使用通行安全性判斷提示或自訂原則判斷提示來進行。 通行安全性判斷提示會緊密對應至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性繫結項目的驗證模式。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式與 WSE 3.0 通行安全性判斷提示不只名稱上相同或類似，它們還會使用相同的認證類型來保護訊息安全。 例如，WSE 3.0 中的 `usernameForCertificate` 通行安全性判斷提示會對應至 `UsernameForCertificate` 中的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式。 下列程式碼範例示範在 WSE 3.0 中使用 `usernameForCertificate` 通行安全性判斷提示的最小原則如何在自訂繫結中對應至 `UsernameForCertificate` 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式。  
  
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
  
 若要將原則檔中指定的 WSE 3.0 Web 服務安全性設定移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，必須在組態檔中建立自訂繫結，並將通行安全性判斷提示設為相等的驗證模式。 另外，自訂繫結必須設定為使用 August 2004 WS-Addressing 規格，以便 WSE 3.0 用戶端與服務進行通訊。 當移轉的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務不需要與 WSE 3.0 用戶端進行通訊，而且只須維護安全性同位時，請考慮使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 系統定義繫結 (包含適當的安全性設定)，而不要建立自訂繫結。  
  
 下表將列出 WSE 3.0 原則檔與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中相等的自訂繫結之間的對應。  
  
|WSE 3.0 組合安全性判斷提示|WCF 自訂繫結組態|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 如需有關如何在 WCF 中建立自訂繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>使用應用程式程式碼來保護安全的 WSE 3.0 Web 服務  
 不管使用的是 WSE 3.0 或 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，都可以在應用程式程式碼中 (不用透過組態檔) 指定安全性需求。 在 WSE 3.0 中，您可以建立衍生自 `Policy` 類別的類別，然後呼叫 `Add` 方法來新增需求以達到這個目的。 如需有關程式碼中指定的安全性需求的詳細資訊，請參閱[How to： 安全 Web 服務沒有使用原則檔](http://go.microsoft.com/fwlink/?LinkId=73747)。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，若要指定程式碼中的安全性需求，請建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別的執行個體，然後將 <xref:System.ServiceModel.Channels.SecurityBindingElement> 執行個體新增到 <xref:System.ServiceModel.Channels.BindingElementCollection>。 安全性判斷提示需求可透過 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的靜態驗證模式協助程式方法來加以設定。 如需詳細資訊，指定在程式碼中使用的安全性需求的相關[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[如何： 自訂繫結使用 SecurityBindingElement 建立](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)和[How to： 建立為 SecurityBindingElement指定驗證模式](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 自訂原則判斷提示  
 在 WSE 3.0 中，有兩種自訂原則判斷提示類型：分別是用來保護 SOAP 訊息安全的原則判斷提示，以及無法保護 SOAP 訊息安全的原則判斷提示。 用來保護 SOAP 訊息安全的原則判斷提示係衍生自 WSE 3.0 `SecurityPolicyAssertion` 類別，且在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，概念上等同於 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別。  
  
 很重要的一點就是，WSE 3.0 通行安全性判斷提示是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式的子集。 如果您已在 WSE 3.0 中建立自訂原則判斷提示，可能會有相等的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式。 例如，WSE 3.0 不會提供等同於 `UsernameOverTransport` 通行安全性判斷提示的 CertificateOverTransport 安全性判斷提示，但會使用 X.509 憑證來執行用戶端驗證。 如果您已經為此案例定義自訂的原則判斷提示，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會直接進行移轉。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會針對此案例定義驗證模式，方便您利用靜態驗證模式協助程式方法來設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
 如果沒有等同於用來保護 SOAP 訊息安全之自訂原則判斷提示的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 驗證模式，則請從 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 或 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 類別衍生一個類別並指定相等的繫結項目。 如需詳細資訊，請參閱[How to： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
 若要轉換不保護 SOAP 訊息的自訂原則判斷提示，請參閱[篩選](../../../../docs/framework/wcf/feature-details/filtering.md)和範例[自訂訊息攔截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 自訂安全性權杖  
 用於建立自訂權杖的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 程式設計模型與 WSE 3.0 不同。 如需有關在 WSE 中建立自訂權杖的詳細資訊，請參閱[建立自訂安全性權杖](http://go.microsoft.com/fwlink/?LinkID=73750)。 如需建立自訂權杖的詳細資訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 自訂權杖管理員  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中用來建立自訂權杖管理員的程式設計模型與 WSE 3.0 不同。 如需有關如何建立自訂權杖管理員和其他元件所需的自訂安全性權杖的詳細資訊，請參閱[How to： 建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
> [!NOTE]
>  如果您已經建立自訂 `UsernameToken` 安全性權杖管理員，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可提供您較簡易的機制讓您輕鬆指定驗證邏輯，而不用建立自訂安全性權杖管理員。 如需詳細資訊，請參閱[How to： 使用自訂使用者名稱和密碼驗證程式](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>使用 MTOM 編碼 SOAP 訊息的 WSE 3.0 Web 服務  
 與 WSE 3 應用程式一樣，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式也可以在組態中指定 MTOM 訊息編碼。 若要移轉這個設定，加入[ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)服務的繫結。 下列程式碼範例將示範如何在 WSE 3.0 中為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中相等的服務指定 MTOM 編碼。  
  
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
 根據預設，使用 TCP 傳輸來傳送 SOAP 訊息的 WSE 3.0 用戶端與 Web 服務無法與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端和 Web 服務互通。 這種不相容情況是因為 TCP 通訊協定中使用的框架處理方式差異以及效能因素所導致。 然而，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例說明了如何實作可與 WSE 3.0 互通的自訂 TCP 工作階段。 如需有關這個範例的詳細資訊，請參閱[傳輸： WSE 3.0 TCP 互通性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)。  
  
 若要指定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]應用程式會使用 TCP 傳輸，請使用[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
### <a name="custom-transport"></a>自訂傳輸  
 WSE 3.0 自訂傳輸在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的對等即為通道延伸。 如需有關建立通道擴充功能的詳細資訊，請參閱[擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [如何：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [如何：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
