---
title: 覆寫服務的身分識別以進行驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 3df1f2490f8636d52ac75fad2469adadec2a57da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>覆寫服務的身分識別以進行驗證
一般來說，您不需要在服務上設定身分識別，因為選擇用戶端認證類型，即表示服務中繼資料中公開的身分識別類型。 例如，下列組態程式碼會使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)項目和設定`clientCredentialType`屬性設定為 Windows。  
  
  
  
 下列 Web 服務描述語言 (WSDL) 片段會顯示端點先前定義的身分識別。 在此範例中，服務自我裝載的服務特定使用者帳戶以執行 (username@contoso.com)，因此使用者主要名稱 (UPN) 識別包含帳戶名稱。 UPN 在 Windows 網域中也稱為使用者登入名稱。  
  
  
  
 範例應用程式，示範身分識別設定，請參閱[服務身分識別範例](../../../../docs/framework/wcf/samples/service-identity-sample.md)。 如需服務身分識別的詳細資訊，請參閱[服務識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 驗證和身分識別  
 根據預設，當服務設定為使用 Windows 認證， [\<識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)包含項目[ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md)或[ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) WSDL 中不會產生元素。 如果服務在執行`LocalSystem`， `LocalService`，或`NetworkService`帳戶、 服務主要名稱 (SPN) 產生的表單中的預設`host/` \< *hostname*> 因為這些帳戶可以存取電腦的 SPN 資料。 如果服務正在執行不同的帳戶，Windows Communication Foundation (WCF) 格式產生 UPN 的\< *username*>@<*domainName* `>`. 這種情況發生的原因是 Kerberos 驗證需要對用戶端提供 UPN 或 SPN，才能驗證服務。  
  
 您也可以使用 Setspn.exe 工具，以服務的帳戶在網域中登錄其他 SPN。 您接著就可以使用 SPN 做為服務的身分識別。 若要下載此工具，請參閱[Windows 2000 Resource Kit Tool: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752)。 如需此工具的詳細資訊，請參閱[Setspn 概觀](http://go.microsoft.com/fwlink/?LinkId=61374)。  
  
> [!NOTE]
>  若不進行交涉而使用 Windows 認證類型，服務的使用者帳戶必須可以存取透過 Active Directory 網域登錄的 SPN。 您可以透過下列方法完成這項作業：  
  
-   使用 NetworkService 或 LocalSystem 帳戶執行服務。 因為那些帳戶存取的電腦會在電腦加入 Active Directory 網域時所建立的 SPN，WCF 自動服務的中繼資料 (WSDL) 內產生適當的 SPN 項目內的服務端點。  
  
-   使用任意的 Active Directory 網域帳戶來執行服務。 在這個情況下，請建立該網域帳戶的 SPN，您可使用 Setspn.exe 公用程式工具來進行。 一旦您建立的服務帳戶的 SPN 時，設定以將該 SPN 發行至服務的用戶端，透過它的中繼資料 (WSDL) 的 WCF。 不論是透過應用程式組態檔或程式碼，均可設定公開端點的端點身分識別以完成此作業。  
  
 Spn 的詳細資訊、 Kerberos 通訊協定和 Active Directory 的內容，請參閱[補充 Windows 的 Kerberos 技術](http://go.microsoft.com/fwlink/?LinkId=88330)。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN 或 UPN 等於空字串時  
 如果您設定 SPN 或 UPN 等於空字串，那麼會發生一些不同的狀況，依使用的安全性層級和驗證模式而定：  
  
-   如果您使用傳輸層級安全性，就會選擇 NT LanMan (NTLM) 驗證。  
  
-   如果您使用訊息層級安全性，驗證可能會失敗，依驗證模式而定：  
  
-   如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `false`，則驗證失敗。  
  
-   如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `true`，則若 UPN 為空時驗證失敗，而若 SPN 為空時驗證成功。  
  
-   如果您正在直接使用 Kerberos (也就是「單次」)，則驗證失敗。  
  
### <a name="using-the-identity-element-in-configuration"></a>使用\<識別 > 組態中的項目  
 如果您在先前對 Certificate`,` 顯示的繫結中變更用戶端認證類型，則產生的 WSDL 會包含 Base64 序列化 X.509 憑證，這個憑證可用於身分識別值，其值如以下程式碼所示。 這是 Windows 以外所有用戶端認證類型的預設值。  
  
  
  
 您可以使用組態中的 <`identity`> 項目或在程式碼中設定身分識別，變更預設服務身分識別的值或變更身分識別的類型。 下列組態程式碼會以 `contoso.com` 這個值來設定網域名稱系統 (DNS) 身分識別。  
  
  
  
### <a name="setting-identity-programmatically"></a>以程式設計方式設定身分識別  
 您的服務並沒有明確指定身分識別，因為 WCF 自動決定。 不過，WCF 可讓您識別端點上指定，如果所需。 下列程式碼會新增具有特定 DNS 身分識別的新服務端點。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立自訂用戶端身分識別驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
