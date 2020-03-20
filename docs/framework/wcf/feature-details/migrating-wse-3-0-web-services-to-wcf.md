---
title: 從 WSE 3.0 Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184573"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>從 WSE 3.0 Web 服務移轉至 WCF
將 WSE 3.0 Web 服務遷移到 Windows 通信基礎 （WCF） 的好處包括提高性能並支援其他傳輸、其他安全方案和 WS-* 規範。 從 WSE 3.0 遷移到 WCF 的 Web 服務的性能可高達 200% 到 400%。 有關 WCF 支援的傳輸的詳細資訊，請參閱[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。 有關 WCF 支援的方案的清單，請參閱[常見安全方案](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 有關 WCF 支援的規範的清單，請參閱[Web 服務協定互通性指南](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)。  
  
 以下各節提供有關如何將 WSE 3.0 Web 服務的特定功能遷移到 WCF 的指導。  
  
## <a name="general"></a>一般  
 WSE 3.0 和 WCF 應用程式包括線級互通性和一組通用術語。 WSE 3.0 和 WCF 應用程式基於它們都支援的 WS-* 規範集，可進行線級交互操作。 開發 WSE 3.0 或 WCF 應用程式時，有一組通用的術語，例如 WSE 中交鑰匙安全斷言的名稱和身份驗證模式。  
  
 儘管 WCF 和 ASP.NET 或 WSE 3.0 程式設計模型之間有許多類似的方面，但它們是不同的。 有關 WCF 程式設計模型的詳細資訊，請參閱[基本程式設計生命週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)。  
  
> [!NOTE]
> 要將 WSE Web 服務遷移到 WCF，[可以使用服務模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具生成用戶端。 然而，該用戶端同時內含可用來做為 WCF 服務起點的介面與類別。 產生的介面會將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用到合約成員 (同時將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設為 `*`)。 當 WSE 用戶端使用此設置調用 Web 服務時，將引發以下異常 **：Web.Services3.回應處理異常：WSE910：在處理回應訊息期間發生錯誤，您可以在內部異常中找到錯誤**。 若要緩解這個情況，請將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.OperationContractAttribute> 屬性 (Property) 設為非 `null` 值，例如 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`。  
  
## <a name="security"></a>安全性  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>使用原則檔來保護安全的 WSE 3.0 Web 服務  
 WCF 服務可以使用設定檔來保護服務，該機制類似于 WSE 3.0 策略檔。 在 WSE 3.0 中，當您使用原則檔來保護 Web 服務安全時，可以使用通行安全性判斷提示或自訂原則判斷提示來進行。 交鑰匙安全斷言與 WCF 安全繫結元素的身份驗證模式緊密映射。 WCF 身份驗證模式和 WSE 3.0 交鑰匙安全斷言不僅名稱相同或類似，還使用相同的憑據類型來保護消息。 例如，WSE `usernameForCertificate` 3.0 中的交鑰匙安全斷言映射到 WCF 中的`UsernameForCertificate`身份驗證模式。 以下代碼示例演示了在 WSE 3.0 中使用`usernameForCertificate`交鑰匙安全斷言的最小策略如何映射到自訂`UsernameForCertificate`綁定中的 WCF 中的身份驗證模式。  
  
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
  
 要將策略檔中指定的 WSE 3.0 Web 服務的安全設置遷移到 WCF，必須在設定檔中創建自訂綁定，並且必須將交鑰匙安全斷言設置為等效身份驗證模式。 另外，自訂繫結必須設定為使用 August 2004 WS-Addressing 規格，以便 WSE 3.0 用戶端與服務進行通訊。 當遷移的 WCF 服務不需要與 WSE 3.0 用戶端通信，並且必須僅維護安全同位時，請考慮使用具有適當安全設置的 WCF 系統定義的綁定，而不是創建自訂綁定。  
  
 下表列出了 WSE 3.0 策略檔和 WCF 中的等效自訂綁定之間的映射。  
  
|WSE 3.0 組合安全性判斷提示|WCF 自訂繫結組態|  
|----------------------------------------|--------------------------------------|  
|\<使用者名 超運輸安全/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<相互證書10安全/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<使用者名用於證書安全/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<匿名證書安全/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<克伯羅斯安全/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<相互證書11安全/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 有關在 WCF 中創建自訂綁定的詳細資訊，請參閱[自訂綁定](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>使用應用程式程式碼來保護安全的 WSE 3.0 Web 服務  
 無論使用 WSE 3.0 還是使用 WCF，都可以在應用程式代碼中指定安全要求，而不是在配置中指定。 在 WSE 3.0 中，您可以建立衍生自 `Policy` 類別的類別，然後呼叫 `Add` 方法來新增需求以達到這個目的。 有關在代碼中指定安全要求的詳細資訊，請參閱[：不使用策略檔案保護 Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10))。 在 WCF 中，要在代碼中指定安全要求，請<xref:System.ServiceModel.Channels.BindingElementCollection>創建類的實例，並將<xref:System.ServiceModel.Channels.SecurityBindingElement>的實例<xref:System.ServiceModel.Channels.BindingElementCollection>添加到 。 安全性判斷提示需求可透過 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別的靜態驗證模式協助程式方法來加以設定。 有關使用 WCF 在代碼中指定安全要求的詳細資訊，請參閱[：使用安全繫結元素創建自訂綁定](how-to-create-a-custom-binding-using-the-securitybindingelement.md)以及如何[：為指定的身份驗證模式創建安全繫結元素](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 自訂原則判斷提示  
 在 WSE 3.0 中，有兩種自訂原則判斷提示類型：分別是用來保護 SOAP 訊息安全的原則判斷提示，以及無法保護 SOAP 訊息安全的原則判斷提示。 安全 SOAP 訊息派生自 WSE 3.0`SecurityPolicyAssertion`類和 WCF 中的概念<xref:System.ServiceModel.Channels.SecurityBindingElement>等效項的策略斷言是類。  
  
 需要注意的一個重要點是 WSE 3.0 交鑰匙安全斷言是 WCF 身份驗證模式的子集。 如果在 WSE 3.0 中創建了自訂策略斷言，則可能存在等效的 WCF 身份驗證模式。 例如，WSE 3.0 不會提供等同於 `UsernameOverTransport` 通行安全性判斷提示的 CertificateOverTransport 安全性判斷提示，但會使用 X.509 憑證來執行用戶端驗證。 如果您已為此方案定義了自己的自訂策略斷言，則 WCF 使遷移變得簡單明瞭。 WCF 為此方案定義了身份驗證模式，因此您可以利用靜態身份驗證模式説明器方法配置 WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
 如果沒有 WCF 身份驗證模式等效于保護 SOAP 訊息的自訂策略斷言、從 派生<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>類<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>或<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF 類並指定等效繫結元素。 有關詳細資訊，請參閱[如何：使用安全繫結元素創建自訂綁定](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
 要轉換不保護 SOAP 訊息的自訂策略斷言，請參閱[篩選](../../../../docs/framework/wcf/feature-details/filtering.md)和示例[自訂消息攔截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 自訂安全性權杖  
 用於創建自訂權杖的 WCF 程式設計模型與 WSE 3.0 不同。 有關在 WSE 中創建自訂權杖的詳細資訊，請參閱[創建自訂安全權杖](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10))。 有關在 WCF 中創建自訂權杖的詳細資訊，請參閱[如何：創建自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 自訂權杖管理員  
 在 WCF 中，用於創建自訂權杖管理器的程式設計模型與 WSE 3.0 不同。 有關如何創建自訂權杖管理器和自訂安全權杖所需的其他元件的詳細資訊，請參閱[如何：創建自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
> [!NOTE]
> 如果已創建自訂`UsernameToken`安全權杖管理器，WCF 提供了一種比創建自訂安全權杖管理器更容易指定身份驗證邏輯的機制。 有關詳細資訊，請參閱[操作：使用自訂使用者名和密碼驗證器](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>使用 MTOM 編碼 SOAP 訊息的 WSE 3.0 Web 服務  
 與 WSE 3 應用程式一樣，WCF 應用程式可以在配置中指定 MTOM 消息編碼。 要遷移此設置，>[\<將 mtomMessage 編碼](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)添加到服務的綁定中。 以下代碼示例演示了如何在 WSE 3.0 中為 WCF 中的等效服務指定 MTOM 編碼。  
  
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
  
## <a name="messaging"></a>Messaging (傳訊)  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>使用 WSE 訊息 API 的 WSE 3.0 應用程式  

 當您使用 WSE 訊息 API 來直接存取於用戶端與 Web 服務之間進行通訊的 XML 時，可以將應用程式轉換為使用 "Plain Old XML" (POX)。 有關 POX 的更多詳細資訊，請參閱[與 POX 應用程式的互通性](interoperability-with-pox-applications.md)。 有關 WSE 消息 API 的更多詳細資訊，請參閱[使用 WSE 消息傳遞 API 發送和接收 SOAP 訊息](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10))。  
  
## <a name="transports"></a>傳輸  
  
### <a name="tcp"></a>TCP  
 預設情況下，使用 TCP 傳輸發送 SOAP 訊息的 WSE 3.0 用戶端和 Web 服務不與 WCF 用戶端和 Web 服務交互操作。 這種不相容情況是因為 TCP 通訊協定中使用的框架處理方式差異以及效能因素所導致。 但是，WCF 示例詳細介紹了如何實現與 WSE 3.0 交互的自訂 TCP 會話。 有關此示例的詳細資訊，請參閱[傳輸：WSE 3.0 TCP 互通性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)。  
  
 要指定 WCF 應用程式使用 TCP 傳輸，請使用[\<netTcp 綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
### <a name="custom-transport"></a>自訂傳輸  
 WCF 中的 WSE 3.0 自訂傳輸等效于通道擴展。 有關創建通道擴展的詳細資訊，請參閱[擴展通道圖層](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="see-also"></a>另請參閱

- [基本程式設計週期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [HOW TO：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [HOW TO：為指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
