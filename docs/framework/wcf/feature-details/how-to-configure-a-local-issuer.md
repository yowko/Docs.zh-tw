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
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601240"
---
# <a name="how-to-configure-a-local-issuer"></a>HOW TO：設定本機簽發者

本主題會說明如何將用戶端設定成使用已發行權杖的本機簽發者。

通常，當用戶端與聯合服務進行通訊時，服務都會指定特定安全性權杖服務的位址，該服務預期會發出用戶端要用來向聯合服務驗證自己的權杖。 在某些情況下，可能會將用戶端設定為使用*本機簽發者*。

在同盟系結的簽發者位址是或的情況下，Windows Communication Foundation （WCF）會使用本機簽發者 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 。 在這種情況下，您必須設定包含本機簽發者位址的 <xref:System.ServiceModel.Description.ClientCredentials>，以及用來與該簽發者進行通訊的繫結。

> [!NOTE]
> 如果 <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> 類別的屬性 `ClientCredentials` 設定為，則 `true` 未指定本機簽發者位址，而或其他同盟系結所指定的簽發者位址 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 為 `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` 、或，則會 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 使用 Windows CardSpace 簽發者。

## <a name="to-configure-the-local-issuer-in-code"></a>透過程式碼來設定本機簽發者

1. 建立型別為 <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 的變數

2. 將此變數設為從 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 類別的 `ClientCredentials` 屬性傳回的執行個體 (Instance)。 該執行個體會由用戶端 (繼承自 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>) 的 <xref:System.ServiceModel.ClientBase%601> 屬性，或是 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 的 <xref:System.ServiceModel.ChannelFactory> 屬性傳回：

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. 將 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> 屬性設定為 <xref:System.ServiceModel.EndpointAddress> 的新執行個體，其本機簽發者位址會當做建構函式 (Constructor) 的引數。

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     或者，建立新的 <xref:System.Uri> 執行個體做為該建構函式的引數。

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders`參數是實例的陣列 <xref:System.ServiceModel.Channels.AddressHeader> ，如下所示。

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. 使用屬性來設定本機簽發者的系結 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> 。

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. 選擇性。 將本機簽發者的已設定端點行為新增到 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> 屬性所傳回的集合，即可新增該行為。

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>透過組態來設定本機簽發者

1. 建立專案 [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) 做為專案的子系 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) ，該專案本身就是 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 端點行為中元素的子系。

2. 將 `address` 屬性設定為將接受權杖要求之本機簽發者的位址。

3. 將 `binding` 和 `bindingConfiguration` 屬性設定為會參考當與本機簽發者端點進行通訊時所使用之適當繫結的值。

4. 選擇性。 將 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 元素設定為 <> 專案的子系 `localIssuer` ，並指定本機簽發者的身分識別資訊。

5. 選擇性。 將 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 元素設定為 <> 專案的子系 `localIssuer` ，並指定必要的其他標頭，以便正確地定址本機簽發者。

## <a name="net-framework-security"></a>.NET Framework 安全性

請注意，如果已指定特定繫結的簽發者位址和繫結，這時使用該繫結的端點就不會使用該本機簽發者。 預期一定要使用該本機簽發者的用戶端應該要確定自己沒有使用這類繫結，否則它們就會修改繫結，進而使得簽發者位址成為 `null`。

## <a name="see-also"></a>請參閱

- [HOW TO：設定聯合服務的認證](how-to-configure-credentials-on-a-federation-service.md)
- [如何：建立同盟用戶端](how-to-create-a-federated-client.md)
- [如何：建立 WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
