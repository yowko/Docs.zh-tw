---
title: "HOW TO：建立 WSFederationHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3314519e89a78f188d78a5e5af641d7c87ee1c46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>HOW TO：建立 WSFederationHttpBinding
在[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]、<xref:System.ServiceModel.WSFederationHttpBinding>類別 ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)組態中) 會提供一個機制來公開聯合的服務。 也就是，要求用戶端使用由安全性權杖服務發出的安全性權杖進行驗證的一種服務。 這個主題會表示如何在程式碼和組態中設定 <xref:System.ServiceModel.WSFederationHttpBinding>。 一旦建立了繫結，就可以設定端點以使用該繫結。  
  
 以下將粗略說明基本步驟：  
  
1.  選取安全性模式。 <xref:System.ServiceModel.WSFederationHttpBinding> 支援 `Message`，而這會在訊息層級中提供端對端安全性 (甚至於在多重躍點中)；也支援 `TransportWithMessageCredential`，而這會在用戶端和服務可直接透過 HTTPS 連線的狀況下提供較好的效能。  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.WSFederationHttpBinding> 也支援 `None` 做為安全性模式。 這個模式並不安全，主要目的僅用於偵錯。 如果服務端點部署與<xref:System.ServiceModel.WSFederationHttpBinding>以及其安全性模式設為`None`、 產生的用戶端繫結 (由產生[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) 是 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 使用的安全性模式`None`。  
  
     和其他系統提供的繫結不一樣，在您使用 `WSFederationHttpBinding` 時不需要選取用戶端認證類型。 這是因為用戶端認證類型一律為已發行的權杖。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會從指定的簽發者取得權杖，並對服務呈現該權杖以驗證用戶端。  
  
2.  在聯合用戶端上，請將 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> 屬性設定為安全性權杖服務的 URL。 將 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> 設定為繫結，以用來與安全性權杖服務進行通訊。  
  
3.  選擇項。 將 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> 屬性設定成權杖型別統一資源識別元 (URI)。 在聯合服務上，指定服務預期的權杖型別。 在聯合用戶端上，指定用戶端從安全性權杖服務中所要求的權杖型別。  
  
     如果沒有指定權杖型別，用戶端會產生不具權杖型別 URI 的 WS-Trust 要求安全性權杖 (Request Security Token，RST)，而根據預設，服務會預期使用安全性判斷提示標記語言 (Security Assertions Markup Language，SAML) 1.1 權杖來進行用戶端驗證。  
  
     SAML 1.1 權杖的 URI 為 "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"。  
  
4.  選擇項。 在聯合服務上，請將 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> 屬性設定為安全性權杖服務的中繼資料 URL。 中繼資料端點可讓服務的用戶端選取適當的繫結/端點組 (如果已將服務設定為發行中繼資料)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]發行中繼資料，請參閱[發行中繼資料](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)。  
  
 您也可以設定其他屬性，包括在發行的權杖中當做證明金鑰使用的金鑰類型、在用戶端和服務之間使用的演算法套件、是否交涉或明確指定服務認證、服務預期發行的權杖要包含的任何特定宣告，以及必須新增至要求 (這些是用戶端傳送至安全性權杖服務的要求) 的其他 XML 項目。  
  
> [!NOTE]
>  只有當 `NegotiateServiceCredential` 設定為 `SecurityMode`，`Message` 屬性才有關聯。 如果 `SecurityMode` 設定為 `TransportWithMessageCredential`，則會忽略 `NegotiateServiceCredential` 屬性。  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>在程式碼中設定 WSFederationHttpBinding  
  
1.  建立 <xref:System.ServiceModel.WSFederationHttpBinding> 的執行個體。  
  
2.  依需求將 <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.WSFederationHttpSecurityMode> 或 <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>。 如果以外的演算法套件<xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A>是必要項目，設定<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A>屬性與值取自<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。  
  
3.  適當地設定 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性。  
  
4.  設定<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>屬性<xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey`或。`AsymmetricKey` 視需要而定。  
  
5.  將 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> 屬性設定為適當值。 如果未設定值，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預設為 "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"，而這表示 SAML 1.1 權杖。  
  
6.  如果未指定本機簽發者，則在用戶端上為必要項；在服務上則為選擇項。 建立其中包含安全性權杖服務之位址和身分識別資訊的 <xref:System.ServiceModel.EndpointAddress>，並將 <xref:System.ServiceModel.EndpointAddress> 執行個體指派給 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> 屬性。  
  
7.  如果未指定本機簽發者，則在用戶端上為必要項；在服務上則不要使用。 建立<xref:System.ServiceModel.Channels.Binding>如`SecurityTokenService`並指派<xref:System.ServiceModel.Channels.Binding>執行個體<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>屬性。  
  
8.  在用戶端上不要使用，在服務上則為選擇項。 對安全性權杖服務的中繼資料建立 <xref:System.ServiceModel.EndpointAddress> 執行個體，並將它指派給 `IssuerMetadataAddress` 屬性。  
  
9. 在用戶端和服務上都是選擇項。 建立一或多個 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> 執行個體，並將這些執行個體新增至 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> 屬性所傳回的集合。  
  
10. 在用戶端和服務上都是選擇項。 建立一或多個 <xref:System.Xml.XmlElement> 執行個體，並將這些執行個體新增至 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> 屬性所傳回的集合。  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a>在組態中建立聯合端點  
  
1.  建立[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)做為子系[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)應用程式組態檔中的項目。  
  
2.  建立[\<繫結 >](../../../../docs/framework/misc/binding.md)做為子系的項目[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)並設定`name`屬性設為適當值。  
  
3.  建立`<security>`做為子系的項目[\<繫結 >](../../../../docs/framework/misc/binding.md)項目。  
  
4.  依照需求，將 `mode` 項目上的 `<security>` 屬性設定為 `Message` 或 `TransportWithMessageCredential` 的值。  
  
5.  建立 `<message>` 項目做為 `<security>` 項目的子項。  
  
6.  選擇項。 以適當的值設定 `algorithmSuite` 項目上的 `<message>` 屬性。 預設為 `Basic256`。  
  
7.  選擇項。 如果需要非對稱證明金鑰，請將 `issuedKeyType` 項目的 `<message>` 屬性設定為 `AsymmetricKey`。 預設為 `SymmetricKey`。  
  
8.  選擇項。 設定 `issuedTokenType` 項目上的 `<message>` 屬性。  
  
9. 如果未指定本機簽發者，則在用戶端上為必要項；在服務上則為選擇項。 建立 `<issuer>` 項目以做為 `<message>` 項目的子項。  
  
10. 將 `address` 屬性設定為 `<issuer>` 項目，並指定安全性權杖服務會接受權杖要求的位址。  
  
11. 選擇項。 加入 `<identity>` 子項目，並指定安全性權杖服務的識別。  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
13. 如果未指定本機簽發者，則在用戶端上為必要項；在服務上則不要使用。 建立[\<繫結 >](../../../../docs/framework/misc/binding.md)可用來與安全性權杖服務通訊的繫結區段中的項目。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立繫結，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
14. 藉由設定 `binding` 項目的 `bindingConfiguration` 和 `<issuer>` 屬性，指定在前面的步驟中所建立的繫結。  
  
15. 在用戶端上不要使用，在服務上則為選擇項。 建立 `<issuerMetadata>` 項目以做為 <`message`> 項目的子項。 接著，在 `address` 項目的 `<issuerMetadata>` 屬性上，指定安全性權杖服務要發行其中繼資料的位址。 您也可以選擇性地新增 `<identity>` 子項目，並指定安全性權杖服務的身分識別。  
  
16. 在用戶端和服務上都是選擇項。 新增 `<claimTypeRequirements>` 項目以做為 `<message>` 項目的子項。 指定必要和選擇性宣告服務依賴加[\<新增 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)項目`<claimTypeRequirements>`項目和指定的宣告型別`claimType`屬性。 透過設定 `isOptional` 屬性，指定提供的宣告為必要項或選擇項。  
  
## <a name="example"></a>範例  
 下列程式碼範例會顯示以命令方式設定 `WSFederationHttpBinding` 的程式碼。  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [同盟](../../../../docs/framework/wcf/feature-details/federation.md)  
 [聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [如何： 停用安全工作階段在 WSFederationHttpBinding 上](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
