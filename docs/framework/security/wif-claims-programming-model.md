---
title: "WIF 宣告程式設計模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6d7059c5209dc95ce68f28e0f32db929e7c97271
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wif-claims-programming-model"></a>WIF 宣告程式設計模型
ASP.NET 和 Windows Communication Foundation (WCF) 的開發人員通常會使用身分識別和 IPrincipal 介面來處理使用者的身分識別資訊。 在 .NET 4.5 中，Windows Identity Foundation (WIF) 已經過整合，使得目前任何主體一律都存在宣告，如下圖所示：  
  
 ![WIF 宣告程式設計模型](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 在 .NET 4.5 中，System.Security.Claims 包含新的 ClaimsPrincipal 和 ClaimsIdentity 類別 (請參閱上圖)。 .NET 中所有的主體現在是衍生自 ClaimsPrincipal。 所有內建的身分識別類別 (例如適用於 ASP.NET 的 FormsIdentity 和 WindowsIdentity) 目前則是衍生自 ClaimsIdentity。 同樣地，所有內建的主體類別 (例如 GenericPrincipal 和 WindowsPrincipal) 也衍生自 ClaimsPrincipal。  
  
 宣告是以 <xref:System.Security.Claims.Claim> 類別表示。 此類別具有下列重要屬性：  
  
-   <xref:System.Security.Claims.Claim.Type%2A> 代表宣告的類型，通常是 URI。 例如，電子郵件地址宣告是以 `http://schemas.microsoft.com/ws/2008/06/identity/claims/email` 表示。  
  
-   <xref:System.Security.Claims.Claim.Value%2A> 包含宣告的值，並以字串表示。 例如，電子郵件地址宣告可用 "someone@contoso.com" 表示。  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A> 代表宣告值的類型，通常是 URI。 例如，字串類型會以 `http://www.w3.org/2001/XMLSchema#string` 表示。 實值型別必須是根據 XML 結構描述的 QName。 值的格式必須是 `namespace#format`，才能啟用 WIF 來輸出有效的 QName 值。 如果命名空間不是妥善定義的命名空間，所產生的 XML 可能無法驗證結構描述，因為該命名空間沒有已發佈的 XSD 檔案。 預設的實值型別是 `http://www.w3.org/2001/XMLSchema#string`。 如需您可以安全使用的已知實值型別，請參閱 [http://www.w3.org/2001/XMLSchema](http://go.microsoft.com/fwlink/?LinkId=209155)。  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A> 是發出宣告的安全性權杖服務 (STS) 的識別碼。 這可用 STS 的 URL 或代表 STS 的名稱來表示，例如 `https://sts1.contoso.com/sts`。  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A> 是最初發出宣告之 STS 的識別碼 (不論鏈結中有多少個 STS)。 其表示方式如同 <xref:System.Security.Claims.Claim.Issuer%2A>。  
  
-   <xref:System.Security.Claims.Claim.Subject%2A> 是所要檢查其身分識別的主題。 它包含 <xref:System.Security.Claims.ClaimsIdentity>。  
  
-   <xref:System.Security.Claims.Claim.Properties%2A> 是一種字典，可讓開發人員提供要與其他屬性一同在網路上傳輸的應用程式特定資料，並且可用於自訂驗證。  
  
## <a name="identity-delegation"></a>識別委派  
 <xref:System.Security.Claims.ClaimsIdentity> 的重要屬性是 <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>。 此屬性可在多層式系統中啟用認證的委派，而多層式系統中的中介層將作為要對後端服務提出要求的用戶端。  
  
### <a name="accessing-claims-through-threadcurrentprincipal"></a>透過 Thread.CurrentPrincipal 存取宣告  
 若要存取目前使用者在 RP 應用程式中的一組宣告，請使用 `Thread.CurrentPrincipal`。  
  
 下列程式碼範例會示範如何使用這個方法來取得 System.Security.Claims.ClaimsIdentity：  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
```  
  
 如需詳細資訊，請參閱<xref:System.Security.Claims>。  
  
### <a name="role-claim-type"></a>角色宣告類型  
 設定 RP 應用程式的一部分是要判斷您的角色宣告類型為何。 System.Security.Claims.ClaimsPrincipal.IsInRole(System.String) 會使用這個宣告類型。 預設的宣告類型是 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`。  
  
### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Windows Identity Foundation 從不同權杖類型擷取的宣告  
 WIF 支援數個立即可用之驗證機制的組合。 下表列出 WIF 從不同權杖類型擷取的宣告。  
  
|語彙基元類型|產生的宣告|對應至 Windows 存取權杖|  
|-|-|-|  
|SAML 1.1|1.來自 System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal、System.IdentityModel.Protocols.WSTrust.RequestSecurityToken、System.IdentityModel.Scope) 的所有宣告。<br />2.包含確認索引鍵之 XML 序列化的 `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` 宣告 (此權杖包含證明權杖時)。<br />3.來自 Issuer 元素的 `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` 宣告。<br />4.AuthenticationMethod 和 AuthenticationInstant 宣告 (權杖包含驗證陳述式時)。|除了＜SAML 1.1＞中所列的宣告之外 (不包含 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` 類型的宣告)，還會加入 Windows 驗證相關宣告，身分識別將以 WindowsClaimsIdentity 表示。|  
|SAML 2.0|與＜SAML 1.1＞相同。|與＜SAML 1.1 對應到 Windows 帳戶＞相同。|  
|X509|1.含有來自 X509 憑證的下列 X500 辨別名稱屬性的宣告：emailName、dnsName、SimpleName、UpnName、UrlName、thumbprin、RsaKey (這可以使用 RSACryptoServiceProvider.ExportParameters 方法從 X509Certificate2.PublicKey.Key 屬性擷取)、DsaKey (這可以使用 DSACryptoServiceProvider.ExportParameters 方法從 X509Certificate2.PublicKey.Key 屬性擷取)、SerialNumber。<br />2.含有值 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509` AuthenticationMethod 宣告。 含有 XmlSchema DateTime 格式的憑證驗證時間值的 AuthenticationInstant 宣告。|1.它會使用 Windows 帳戶的完整網域名稱作為 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` 宣告值。 。<br />2.來自 X509 憑證的宣告未對應到 Windows，但已透過將憑證對應到 Windows 取得來自 Windows 帳戶的宣告。|  
|UPN|1.宣告類似於 Windows 驗證章節中的宣告。<br />2.含有值 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password` AuthenticationMethod 宣告。 含有 XmlSchema DateTime 格式的密碼驗證時間值的 AuthenticationInstant 宣告。||  
|Windows (Kerberos 或 NTLM)|1.從存取權杖產生的宣告，例如：PrimarySID、DenyOnlyPrimarySID、PrimaryGroupSID、DenyOnlyPrimaryGroupSID、GroupSID、DenyOnlySID 和 Name<br />2.含有值 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows` 的 AuthenticationMethod。 含有 XMLSchema DateTime 格式的 Windows 存取權杖建立時間值的 AuthenticationInstant。||  
|RSA 金鑰組|1.含有值 RSAKeyValue 的 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` 宣告。<br />2.含有值 `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature` 的 AuthenticationMethod 宣告。 含有 XMLSchema DateTime 格式的 RSA 金鑰驗證 (也就是驗證簽章) 時間值的 AuthenticationInstant 宣告。||  
  
|驗證類型|"AuthenticationMethod" 宣告中發出的 URI|  
|-|-|  
|密碼|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|未指定|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|
