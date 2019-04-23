---
title: 宣告與權杖
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 223b86310d90c877df15a99c90a0a72ea780734a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076259"
---
# <a name="claims-and-tokens"></a>宣告與權杖
本主題說明 Windows Communication Foundation (WCF) 從它所支援的預設權杖所建立的各種宣告類型。  
  
 您可以使用 <xref:System.IdentityModel.Claims.ClaimSet> 和 <xref:System.IdentityModel.Claims.Claim> 類別來檢查用戶端認證的宣告。 `ClaimSet` 包含 `Claim` 物件的集合。 每個 `Claim` 都具有下列重要的成員：  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 屬性會傳回指定所要建立之宣告類型的統一資源識別元 (URI)。 例如，宣告類型可能的情況下，URI 的憑證指紋`http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`。  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> 屬性會傳回指定宣告權限的 URI。 預先定義的權限可以在 <xref:System.IdentityModel.Claims.Rights> 類別中找到 (<xref:System.IdentityModel.Claims.Rights.Identity%2A>、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>)。  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> 屬性會傳回與宣告相關聯的資源。  
  
 每個 <xref:System.IdentityModel.Claims.ClaimSet> 也都有 <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> 屬性，此屬性表示 <xref:System.IdentityModel.Claims.ClaimSet> 的 `Issuer`。  
  
## <a name="windows-accounts"></a>Windows 帳戶  
 當用戶端認證對應至 Windows 使用者帳戶時，產生的 <xref:System.IdentityModel.Claims.ClaimSet> 具有下列值：  
  
-   `Issuer` 是 <xref:System.IdentityModel.Claims.ClaimSet> 類別的靜態 Windows 屬性所傳回的值。  
  
-   此集合中的宣告為：  
  
    -   具有安全識別項 (SID) 之 <xref:System.IdentityModel.Claims.Claim> 值的 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `Identity` 屬性值，以及傳回實際 SID 值的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。 SID 是網域控制站發出至每個使用者的唯一值。 SID 可用來識別與 Windows 安全性互動的使用者。  
  
    -   具有 SID 之 <xref:System.IdentityModel.Claims.Claim> 值的 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `PossessProperty`，以及 SID 值的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   具有 <xref:System.IdentityModel.Claims.Claim> 之 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 的 <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `PossessProperty`，以及包含使用者名稱之字串 (例如，"MYMACHINE\Bob") 的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   其他 SID 宣告，這些宣告具有使用者所屬之各種群組的 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>。  
  
## <a name="certificates"></a>憑證  
 當用戶端認證是憑證時，產生的 <xref:System.IdentityModel.Claims.ClaimSet> 具有下列值：  
  
-   如果是自動發行的憑證，`Issuer` 就是 <xref:System.IdentityModel.Claims.ClaimSet> 本身。 <xref:System.IdentityModel.Claims.ClaimSet> 會傳回 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 的 <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `Identity`，以及 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 值，此值表示包含憑證指紋的 <xref:System.Byte> 陣列。  
  
-   如果是由憑證授權單位發出的憑證，簽發者就是 `ClaimSet`，表示憑證授權單位的憑證。  
  
-   此集合中的 `Claims` 包括：  
  
    -   具有 Thumbprint 之 `Claim` 的 `ClaimType`、PossessProperty 的 `Right`，以及 `Resource`，表示包含憑證指紋的位元組陣列。  
  
    -   各種類型的其他 PossessProperty 宣告，包括 X500DistinguishedName、Dns、Name、Upn 和 Rsa，表示憑證的各種屬性。 Rsa 宣告的資源是與憑證相關聯的公開金鑰。**附註**用戶端認證類型所在的憑證，服務對應至 Windows 帳戶，兩個`ClaimSet`物件所產生。 第一個包含與 Windows 帳戶相關的所有宣告，第二個則包含與憑證相關的所有宣告。  
  
## <a name="user-namepassword"></a>使用者名稱/密碼  
 當用戶端認證是未對應至 Windows 帳戶的使用者名稱/密碼 (或對等用法) 時，產生的 `ClaimSet` 會由 <xref:System.IdentityModel.Claims.ClaimSet.System%2A> 類別的靜態 `ClaimSet` 屬性發出。 `ClaimSet`包含`Identity`宣告的型別<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>的資源是使用者名稱用戶端提供。 對應的宣告具有 `Right` 的`PossessProperty`。  
  
## <a name="rsa-keys"></a>RSA 金鑰  
 使用未與憑證相關聯的 RSA 金鑰時，產生`ClaimSet`自我發行，並且包含`Identity`宣告的型別<xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>資源是 RSA 金鑰。 對應的宣告具有 `Right` 的`PossessProperty`。  
  
## <a name="saml"></a>SAML  
 當用戶端使用安全性判斷提示標記語言 (SAML) 權杖進行驗證時，產生的 `ClaimSet` 會由簽署 SAML 權杖的實體發出，通常是所發出 SAML 權杖之安全性權杖服務 (STS) 的憑證。 `ClaimSet` 包含 SAML 權杖中的各種宣告。 如果 SAML 權杖包含具有非 `SamlSubject` 名稱的 `null`，則會建立具有 `Identity` 型別的 <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> 宣告和 <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> 的資源型別。  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>身分識別宣告和 ServiceSecurityContext.IsAnonymous  
 如果沒有任何`ClaimSet`從用戶端認證產生的物件包含具有宣告`Right`的`Identity,`則<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>屬性會傳回`true`。 如果出現一或多個這類的宣告，則 `IsAnonymous` 屬性會傳回 `false`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
