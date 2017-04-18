---
title: "WIF 宣告程式設計模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# WIF 宣告程式設計模型
ASP。NET 與 Windows 通訊資格的開發人員經常使用的 IIdentity 和 IPrincipal 介面，用於處理使用者的識別資訊。  單元。NET 4.5、 Windows 識別基礎 \(WIF\) 已經整合的宣告會立即永遠存在任何主體，如下圖所示：  
  
 ![WIF 宣告程式設計模型](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 單元。NET 4.5 System.Security.Claims 包含了新的 ClaimsPrincipal 和 ClaimsIdentity 類別 \(請參閱上方圖表\)。  在中的所有原則。NET 現在是衍生自 ClaimsPrincipal。  所有內建識別類別，如 asp 的 FormsIdentity。NET，並且兩者現在是衍生自 ClaimsIdentity。  同樣地，所有內建的主要類別，如 GenericPrincipal 和 WindowsPrincipal 是衍生自 ClaimsPrincipal。  
  
 宣告由<xref:System.Security.Claims.Claim>類別。  這個類別包含下列資訊的格式：  
  
-   <xref:System.Security.Claims.Claim.Type%2A>表示型別宣告的通常是 URI。  例如，電子郵件地址宣告表示為`http://schemas.microsoft.com/ws/2008/06/identity/claims/email`。  
  
-   <xref:System.Security.Claims.Claim.Value%2A>包含宣告的值，表示為字串。  例如，電子郵件地址可以表示為"someone@contoso.com"。  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A>表示宣告值的型別，通常是 URI。  例如，string 型別表示為`http://www.w3.org/2001/XMLSchema#string`。  實值型別必須是根據 XML 結構描述來 QName。  值的格式應該是`namespace#format`啟用輸出 QName 有效值的 WIF。  如果命名空間不是完整定義的命名空間，產生的 XML 可能無法結構描述驗證，因為不是該命名空間的已發行的 XSD 檔案。  預設實值型別是`http://www.w3.org/2001/XMLSchema#string`。  請參閱[http:\/\/www.w3.org\/2001\/XMLSchema](http://go.microsoft.com/fwlink/?LinkId=209155)給熟知的實值型別，您可以使用 \[安全地。  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A>為安全性權杖服務 \(STS\) 發出宣告的識別項。  這可以表示為 URL 的 STS 或名稱，例如表示 STS， `https://sts1.contoso.com/sts`。  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A>是鏈結中初次發行的宣告，不論多少 Sts STS 的識別項。  這就像是表示<xref:System.Security.Claims.Claim.Issuer%2A>。  
  
-   <xref:System.Security.Claims.Claim.Subject%2A>為正在檢查識別主體。  它包含 <xref:System.Security.Claims.ClaimsIdentity>。  
  
-   <xref:System.Security.Claims.Claim.Properties%2A>是字典，其可讓開發人員提供要加上其他屬性，在網路上傳輸的應用程式專屬資料，並可用於自訂驗證。  
  
## 識別委派  
 有一個重要的特性<xref:System.Security.Claims.ClaimsIdentity>是<xref:System.Security.Claims.ClaimsIdentity.Actor%2A>。  這個屬性允許在多層系統中的中介層會做為對後端服務進行要求的用戶端的認證的委派優點。  
  
### 通常透過存取宣告  
 若要存取目前的使用者組 RP 應用程式中的宣告，請使用`Thread.CurrentPrincipal`。  
  
 下列程式碼範例會示範這個方法，以取得 System.Security.Claims.ClaimsIdentity 的使用方式：  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
```  
  
 如需詳細資訊，請參閱 <xref:System.Security.Claims>。  
  
### 角色的宣告類型  
 設定資源點數應用程式的一部份是要判斷您的角色宣告型別應該是。  System.Security.Claims.ClaimsPrincipal.IsInRole\(System.String\) 會使用此宣告類型。  預設的宣告型別是`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`。  
  
### 展開的 Windows 識別基礎，從不同的語彙基元型別宣告  
 WIF 支援現成的驗證機制的多種組合。  下表列出的宣告，WIF 會從不同的語彙基元型別中擷取。  
  
||||  
|-|-|-|  
|語彙基元型別|產生的宣告|對應到 Windows 存取權仗|  
|SAML 1.1|1.  從 System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity\(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope\) 的所有宣告。<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey`如果經常在權杖包含證明權杖會包含確認機碼的 XML 序列化的宣告。<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername`說從簽發者的項目。<br />4.  AuthenticationMethod 和 AuthenticationInstant 宣告，如果經常在權杖包含驗證陳述式。|除了宣告中，列在"SAML 1.1"，除了宣告型別的`http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`，會加入宣告，並且識別無法由 WindowsClaimsIdentity 相關的 Windows 驗證。|  
|SAML 2.0|"SAML 1.1"相同。|"SAML 1.1 對應到 Windows 帳戶"相同。|  
|X509|1.  宣告與 x500 辨別名稱、 emailName、 dnsName，SimpleName、 UpnName、 UrlName，憑證指紋 \(這可擷取使用 RSACryptoServiceProvider.ExportParameters 方法，在 \[X509Certificate2.PublicKey.Key\] 屬性\) 的 RsaKey、 DsaKey \(這可擷取使用 DSACryptoServiceProvider.ExportParameters 方法，在 \[X509Certificate2.PublicKey.Key\] 屬性\)，因此整個 x509 序號屬性憑證。<br />2.  值主張 AuthenticationMethod `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`。  AuthenticationInstant 宣告，且值為 XmlSchema 的日期時間格式時驗證憑證的時間。|1.  它會使用 Windows 帳戶完整的網域名稱，做為`http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`宣告值。  .<br />2.  X509 憑證未對應到 Windows 中，從宣告和宣告從 windows 帳戶，藉由將憑證對應到 Windows。|  
|UPN|1.  宣告是類似於 \[Windows 驗證\] 區段中的宣告。<br />2.  值主張 AuthenticationMethod `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`。  當密碼已確認 XmlSchema 日期時間格式的情況下，值 AuthenticationInstant 主張。||  
|Windows \(Kerberos 或 「 NTLM\)|1.  例如，產生存取權杖中的宣告： PrimarySID，DenyOnlyPrimarySID，PrimaryGroupSID，DenyOnlyPrimaryGroupSID，GroupSID，DenyOnlySID，和名稱<br />2.  值的 AuthenticationMethod `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`。  XMLSchema 日期時間格式中建立 Windows 存取語彙基元時的情況下，值 AuthenticationInstant。||  
|RSA 金鑰組|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa`的 RSAKeyValue 值宣告。<br />2.  AuthenticationMethod 宣告，值`http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`。  AuthenticationInstant 主張的 RSA 金鑰已驗證時的時間值 \(也就是簽章\) 的 XMLSchema 日期時間格式。||  
  
|||  
|-|-|  
|驗證類型|"AuthenticationMethod"宣告中所發出的 URI|  
|密碼|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Unspecified|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|