---
title: 從 WSE 3.0 Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 5f615af0340a68e43a184465ff99637e5e5e06c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965335"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>從 WSE 3.0 Web 服務移轉至 WCF
將 WSE 3.0 Web 服務遷移至 Windows Communication Foundation (WCF) 的優點包括提升的效能, 以及其他傳輸、額外的安全性案例和 WS-* 規格的支援。 從 WSE 3.0 遷移至 WCF 的 Web 服務, 最高可享有 200% 到 400% 的效能改進。 如需 WCF 支援之傳輸的詳細資訊, 請參閱[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。 如需 WCF 支援的案例清單, 請參閱[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 如需 WCF 支援的規格清單, 請參閱[Web 服務通訊協定互通性指南](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)。  
  
 下列各節提供如何將 WSE 3.0 Web 服務的特定功能遷移至 WCF 的指引。  
  
## <a name="general"></a>一般  
 WSE 3.0 和 WCF 應用程式包含連線層級互通性和一組常用的術語。 WSE 3.0 和 WCF 應用程式都是以其所支援的 WS-* 規格集合為基礎的網路層級互通性。 當 WSE 3.0 或 WCF 應用程式開發時, 會有一組常見的術語, 例如 WSE 中的全包式安全性判斷提示名稱和驗證模式。  
  
 雖然 WCF 和 ASP.NET 或 WSE 3.0 程式設計模型之間有許多類似的層面, 但它們是不同的。 如需 WCF 程式設計模型的詳細資訊, 請參閱[基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)。  
  
> [!NOTE]
> 若要將 WSE Web 服務遷移至 WCF, 您可以使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來產生用戶端。 然而，該用戶端同時內含可用來做為 WCF 服務起點的介面與類別。 產生的介面會將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用到合約成員 (同時將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設為 `*`)。 當 WSE 用戶端使用此設定呼叫 Web 服務時, 會擲回下列例外狀況:**Web.Services3.ResponseProcessingException:WSE910:處理回應訊息期間發生錯誤, 您可以在內部例外**狀況中找到錯誤。 若要緩解這個情況，請將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性 (Property) 設為非 `null` 值，例如 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`。  
  
## <a name="security"></a>安全性  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>使用原則檔來保護安全的 WSE 3.0 Web 服務  
 WCF 服務可以使用設定檔來保護服務, 而且該機制類似于 WSE 3.0 原則檔案。 在 WSE 3.0 中，當您使用原則檔來保護 Web 服務安全時，可以使用通行安全性判斷提示或自訂原則判斷提示來進行。 全包式安全性判斷提示會緊密對應至 WCF 安全性繫結項目的驗證模式。 WCF 驗證模式和 WSE 3.0 通行安全性判斷提示不只會命名相同或類似, 它們會使用相同的認證類型來保護訊息的安全。 比方說, WSE `usernameForCertificate` 3.0 中的「全包式」安全性判斷提示`UsernameForCertificate`會對應到 WCF 中的驗證模式。 下列程式碼範例示範在 WSE 3.0 中使用`usernameForCertificate` 「全包式」安全性判斷提示的最小原則, 如何對應`UsernameForCertificate`至自訂系結中 WCF 的驗證模式。  
  
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
  
 若要將原則檔中指定的 WSE 3.0 Web 服務安全性設定遷移至 WCF, 必須在設定檔案中建立自訂系結, 而且必須將通行安全性判斷提示設為其對等的驗證模式。 另外，自訂繫結必須設定為使用 August 2004 WS-Addressing 規格，以便 WSE 3.0 用戶端與服務進行通訊。 當遷移的 WCF 服務不需要與 WSE 3.0 用戶端通訊, 而且必須只維護安全性同位時, 請考慮使用 WCF 系統定義的系結搭配適當的安全性設定, 而不是建立自訂系結。  
  
 下表列出 WSE 3.0 原則檔案與 WCF 中對等的自訂系結之間的對應。  
  
|WSE 3.0 組合安全性判斷提示|WCF 自訂繫結組態|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 如需在 WCF 中建立自訂系結的詳細資訊, 請參閱[自訂](../../../../docs/framework/wcf/extending/custom-bindings.md)系結。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>使用應用程式程式碼來保護安全的 WSE 3.0 Web 服務  
 無論使用的是 WSE 3.0 或 WCF, 都可以在應用程式代碼中指定安全性需求, 而不是在設定中。 在 WSE 3.0 中，您可以建立衍生自 `Policy` 類別的類別，然後呼叫 `Add` 方法來新增需求以達到這個目的。 如需在程式碼中指定安全性需求的詳細資訊[, 請參閱如何:保護 Web 服務](https://go.microsoft.com/fwlink/?LinkId=73747), 而不使用原則檔案。 在 WCF 中, 若要在程式碼中指定安全性需求, 請<xref:System.ServiceModel.Channels.BindingElementCollection>建立類別的實例, 並將<xref:System.ServiceModel.Channels.SecurityBindingElement>的實例<xref:System.ServiceModel.Channels.BindingElementCollection>加入至。 安全性判斷提示需求可透過 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的靜態驗證模式協助程式方法來加以設定。 如需使用 WCF 在程式碼中指定安全性需求的詳細[資訊, 請參閱如何:使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)建立自訂系結和[如何:為指定的驗證模式](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)建立 SecurityBindingElement。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 自訂原則判斷提示  
 在 WSE 3.0 中，有兩種自訂原則判斷提示類型：分別是用來保護 SOAP 訊息安全的原則判斷提示，以及無法保護 SOAP 訊息安全的原則判斷提示。 保護 SOAP 訊息從 WSE 3.0 `SecurityPolicyAssertion`類別衍生的原則判斷提示, 以及 WCF 中對等的概念<xref:System.ServiceModel.Channels.SecurityBindingElement>是類別。  
  
 值得注意的一點是, WSE 3.0 全包式安全性判斷提示是 WCF 驗證模式的子集。 如果您已在 WSE 3.0 中建立自訂原則判斷提示, 可能會有對等的 WCF 驗證模式。 例如，WSE 3.0 不會提供等同於 `UsernameOverTransport` 通行安全性判斷提示的 CertificateOverTransport 安全性判斷提示，但會使用 X.509 憑證來執行用戶端驗證。 如果您已針對此案例定義自己的自訂原則判斷提示, WCF 可讓您直接進行遷移。 WCF 會定義此案例的驗證模式, 因此您可以利用靜態驗證模式 helper 方法來設定 WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
 當沒有等同于可保護 SOAP 訊息安全之自訂原則判斷提示的 WCF 驗證模式時, 請從<xref:System.ServiceModel.Channels.TransportSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>或<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF 類別衍生類別, 並指定相等的繫結項目。 如需詳細資訊, [請參閱如何:使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)建立自訂系結。  
  
 若要轉換不保護 SOAP 訊息的自訂原則判斷提示, 請參閱[篩選](../../../../docs/framework/wcf/feature-details/filtering.md)和範例[自訂訊息攔截](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)器。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 自訂安全性權杖  
 用來建立自訂權杖的 WCF 程式設計模型與 WSE 3.0 不同。 如需在 WSE 中建立自訂權杖的詳細資訊, 請參閱[建立自訂安全性權杖](https://go.microsoft.com/fwlink/?LinkID=73750)。 如需在 WCF 中建立自訂權杖的詳細[資訊, 請參閱如何:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 自訂權杖管理員  
 在 WCF 中建立自訂權杖管理員的程式設計模型與 WSE 3.0 不同。 如需如何建立自訂權杖管理員和自訂安全性權杖所需之其他元件的詳細資訊, 請參閱[如何:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
> [!NOTE]
> 如果您已建立自訂`UsernameToken`安全性權杖管理員, WCF 會提供更簡單的機制來指定驗證邏輯, 而不是建立自訂安全性權杖管理員。 如需詳細資訊, [請參閱如何:使用自訂使用者名稱和密碼驗證](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)程式。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>使用 MTOM 編碼 SOAP 訊息的 WSE 3.0 Web 服務  
 就像 WSE 3 應用程式一樣, WCF 應用程式也可以在設定中指定 MTOM 訊息編碼。 若要遷移此設定, 請將[ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)新增至服務的系結。 下列程式碼範例示範如何在 WSE 3.0 中為 WCF 中對等的服務指定 MTOM 編碼。  
  
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
 當您使用 WSE 訊息 API 來直接存取於用戶端與 Web 服務之間進行通訊的 XML 時，可以將應用程式轉換為使用 "Plain Old XML" (POX)。 如需 POX 的詳細資訊, 請參閱[與 POX 應用程式的互通性](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)。 如需 WSE 訊息 API 的詳細資訊, 請參閱[使用 WSE 訊息 Api 傳送和接收 SOAP 訊息](https://go.microsoft.com/fwlink/?LinkID=73755)。  
  
## <a name="transports"></a>傳輸  
  
### <a name="tcp"></a>TCP  
 根據預設, 使用 TCP 傳輸來傳送 SOAP 訊息的 WSE 3.0 用戶端和 Web 服務不會與 WCF 用戶端和 Web 服務相交互操作。 這種不相容情況是因為 TCP 通訊協定中使用的框架處理方式差異以及效能因素所導致。 不過, WCF 範例會詳細說明如何執行與 WSE 3.0 交互操作的自訂 TCP 會話。 如需此範例的詳細資訊[, 請參閱 Transport:WSE 3.0 TCP 互](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)操作性。  
  
 若要指定 WCF 應用程式使用 TCP 傳輸, 請使用[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
### <a name="custom-transport"></a>自訂傳輸  
 在 WCF 中, 對等的 WSE 3.0 自訂傳輸是通道延伸模組。 如需建立通道擴充功能的詳細資訊, 請參閱[擴充通道層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="see-also"></a>另請參閱

- [基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [如何：使用 SecurityBindingElement 建立自訂系結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [如何：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
