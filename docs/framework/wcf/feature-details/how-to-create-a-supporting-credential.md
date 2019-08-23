---
title: 作法：建立支援的認證
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968904"
---
# <a name="how-to-create-a-supporting-credential"></a>作法：建立支援的認證
您可能具有需要多個認證的自訂安全性配置。 例如，服務對用戶端的要求可能不只是提供使用者名稱和密碼，可能也要提供可證明用戶端已超過 18 歲的認證。 第二個認證是*支援的認證*。 本主題說明如何在 Windows Communication Foundation (WCF) 用戶端中執行這類認證。  
  
> [!NOTE]
> 支援認證的規格為 WS-SecurityPolicy 規格的一部分。 如需詳細資訊, 請參閱[Web 服務安全性規格](https://go.microsoft.com/fwlink/?LinkId=88537)。  
  
## <a name="supporting-tokens"></a>支援權杖  
 簡單地說, 當您使用訊息安全性時, 一律會使用*主要認證*來保護訊息安全 (例如, x.509 憑證或 Kerberos 票證)。  
  
 如規格所定義, 安全性系結會使用*權杖*來保護訊息交換。 *權杖*是安全性認證的標記法。  
  
 安全性繫結會使用安全性繫結原則中識別的主要權杖來建立簽章。 此簽章稱為「訊息簽章」 ( *message signature*)。  
  
 您也可以指定其他權杖，以擴大與訊息簽章相關聯的權杖所提供的宣告。  
  
## <a name="endorsing-signing-and-encrypting"></a>簽署 (Endorsing)、簽署 (Signing) 和加密  
 支援的認證會導致在訊息內傳輸*支援的權杖*。 WS-SecurityPolicy 規格定義了四種可將支援權杖附加至訊息的方法，如下表所述。  
  
|用途|描述|  
|-------------|-----------------|  
|簽署人|支援權杖包含在安全性標頭中，而且是由訊息簽章進行簽署。|  
|簽署|*簽署權杖*會簽署訊息簽章。|  
|已簽署 (Signed) 和簽署 (Endorsing)|已簽署的簽署權杖會簽署從訊息簽章產生的整個 `ds:Signature` 項目，而這些權杖本身就是由該訊息簽章所簽署；也就是說，這兩個權杖 (用於訊息簽章的權杖和已簽署的簽署權杖) 會彼此進行簽署。|  
|已簽署和加密|已簽署的加密支援權杖是出現在 `wsse:SecurityHeader` 時，也會進行加密的已簽署支援權杖。|  
  
## <a name="programming-supporting-credentials"></a>程式設計的支援認證  
 若要建立使用支援權杖的服務, 您必須建立[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。 (如需詳細資訊, [請參閱如何:使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)建立自訂系結。)  
  
 建立自訂繫結的第一個步驟為建立安全性繫結項目，可以是下列三種類型的其中之一：  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 繼承自 <xref:System.ServiceModel.Channels.SecurityBindingElement> 的所有類別，可包含四個相關的屬性：  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>範圍  
 支援認證中有兩個範圍：  
  
- 支援*權杖的端點*支援端點的所有作業。 這也就是支援權杖所表示的認證，可以在每次叫用端點作業時使用此認證。  
  
- *支援權杖*的作業僅支援特定的端點作業。  
  
 如屬性名稱所指出，支援認證可以為必要項目或選用項目。 也就是說，如果在出現支援認證時使用該認證 (雖然不需要該認證)，在沒有出現該認證時驗證也不會失敗。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>建立包含支援認證的自訂繫結  
  
1. 建立安全性繫結項目。 底下的範例會使用 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 驗證模式建立 `UserNameForCertificate`。 請使用 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> 方法。  
  
2. 將支援參數新增至適當屬性 (`Endorsing`、`Signed`、`SignedEncrypted` 或 `SignedEndorsed`) 所傳回的類型集合。 <xref:System.ServiceModel.Security.Tokens> 命名空間中的類型包含常用類型，例如 <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會建立 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的執行個體，並將 <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> 類別的執行個體新增至所傳回的簽署屬性集合。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 SecurityBindingElement 建立自訂系結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
