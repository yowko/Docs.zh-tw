---
title: HOW TO：設定本機簽發者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 5bddab91fed0f8267804cdf8506c9a632c50d174
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837124"
---
# <a name="how-to-configure-a-local-issuer"></a>HOW TO：設定本機簽發者
本主題會說明如何將用戶端設定成使用已發行權杖的本機簽發者。  
  
 通常，當用戶端與聯合服務進行通訊時，服務都會指定特定安全性權杖服務的位址，該服務預期會發出用戶端要用來向聯合服務驗證自己的權杖。 在某些情況下，用戶端可能會設定為使用*本機簽發者*。  
  
 Windows Communication Foundation (WCF) 的聯合繫結的簽發者位址的情況下使用本機簽發者 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或`null`。 在這種情況下，您必須設定包含本機簽發者位址的 <xref:System.ServiceModel.Description.ClientCredentials>，以及用來與該簽發者進行通訊的繫結。  
  
> [!NOTE]
>  如果<xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>屬性`ClientCredentials`類別設定為`true`、 未指定本機簽發者位址，及所指定的簽發者位址[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或其他聯合繫結是 `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ， `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` ，或者是`null`，然後 Windows[!INCLUDE[infocard](../../../../includes/infocard-md.md)]就使用簽發者。  
  
### <a name="to-configure-the-local-issuer-in-code"></a>透過程式碼來設定本機簽發者  
  
1.  建立型別為 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 的變數  
  
2.  將此變數設為從 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 類別的 `ClientCredentials` 屬性傳回的執行個體 (Instance)。 該執行個體會由用戶端 (繼承自 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>) 的 <xref:System.ServiceModel.ClientBase%601> 屬性，或是 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 的 <xref:System.ServiceModel.ChannelFactory> 屬性傳回：  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> 屬性設定為 <xref:System.ServiceModel.EndpointAddress> 的新執行個體，其本機簽發者位址會當做建構函式 (Constructor) 的引數。  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     或者，建立新的 <xref:System.Uri> 執行個體做為該建構函式的引數。  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders`參數是陣列<xref:System.ServiceModel.Channels.AddressHeader>執行個體，如所示。  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  設定本機簽發者使用的繫結<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>屬性。  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  選擇性。 將本機簽發者的已設定端點行為新增到 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> 屬性所傳回的集合，即可新增該行為。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>透過組態來設定本機簽發者  
  
1.  建立[ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)的子系的項目[ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)是本身的子系的項目[ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)是端點行為中的項目。  
  
2.  將 `address` 屬性設定為將接受權杖要求之本機簽發者的位址。  
  
3.  將 `binding` 和 `bindingConfiguration` 屬性設定為會參考當與本機簽發者端點進行通訊時所使用之適當繫結的值。  
  
4.  選擇性。 設定[\<身分識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)的子系的項目 <`localIssuer`> 項目，並指定本機簽發者的身分識別資訊。  
  
5.  選擇性。 設定[\<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)的子系的項目 <`localIssuer`> 項目，並指定正確定址本機簽發者所需的其他標頭。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請注意，如果已指定特定繫結的簽發者位址和繫結，這時使用該繫結的端點就不會使用該本機簽發者。 預期一定要使用該本機簽發者的用戶端應該要確定自己沒有使用這類繫結，否則它們就會修改繫結，進而使得簽發者位址成為 `null`。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定同盟服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [如何：建立同盟用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [如何：建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
