---
title: 覆寫服務的身分識別以進行驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: eed8a1edaae5fab03ad9e78d29803676debd1b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796920"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>覆寫服務的身分識別以進行驗證
一般來說，您不需要在服務上設定身分識別，因為選擇用戶端認證類型，即表示服務中繼資料中公開的身分識別類型。 例如，下列設定程式碼會使用[ \<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) `clientCredentialType`元素，並將屬性設為 Windows。  

 下列 Web 服務描述語言 (WSDL) 片段會顯示端點先前定義的身分識別。 在此範例中，服務會在特定使用者帳戶（username@contoso.com）下以自我裝載服務的形式執行，因此使用者主要名稱（UPN）身分識別會包含帳戶名稱。 UPN 在 Windows 網域中也稱為使用者登入名稱。  

 如需示範身分識別設定的範例應用程式，請參閱[服務識別範例](../samples/service-identity-sample.md)。 如需服務識別的詳細資訊，請參閱[服務身分識別和驗證](../feature-details/service-identity-and-authentication.md)。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 驗證和身分識別  
 根據預設，當服務設定為使用 Windows 認證時， [ \<](../../configure-apps/file-schema/wcf/identity.md)包含[ \<userPrincipalName >](../../configure-apps/file-schema/wcf/userprincipalname.md)或[ \<servicePrincipalName >](../../configure-apps/file-schema/wcf/serviceprincipalname.md)元素的身分識別 > 元素為在 WSDL 中產生。 `LocalSystem`如果服務是在、 `NetworkService` `LocalService`或帳戶之下執行，預設`host/` \<會以*主機名稱*的形式產生服務主體名稱（SPN） > 因為這些帳戶可存取電腦的 SPN 資料。 如果服務是在不同的帳戶下執行，Windows Communication Foundation （WCF）會以使用者*名稱*>@< *domainName* `>`的格式\<產生 UPN。 這種情況發生的原因是 Kerberos 驗證需要對用戶端提供 UPN 或 SPN，才能驗證服務。  
  
 您也可以使用 Setspn.exe 工具，以服務的帳戶在網域中登錄其他 SPN。 您接著就可以使用 SPN 做為服務的身分識別。 若要下載此工具， [請參閱 Windows 2000 資源套件工具：](https://go.microsoft.com/fwlink/?LinkId=91752)Setspn。 如需此工具的詳細資訊，請參閱[Setspn 總覽](https://go.microsoft.com/fwlink/?LinkId=61374)。  
  
> [!NOTE]
> 若不進行交涉而使用 Windows 認證類型，服務的使用者帳戶必須可以存取透過 Active Directory 網域登錄的 SPN。 您可以透過下列方法完成這項作業：  
  
- 使用 NetworkService 或 LocalSystem 帳戶執行服務。 因為這些帳戶可以存取電腦加入 Active Directory 網域時所建立的電腦 SPN，所以 WCF 會自動在服務的中繼資料（WSDL）中的服務端點內產生適當的 SPN 元素。  
  
- 使用任意的 Active Directory 網域帳戶來執行服務。 在這個情況下，請建立該網域帳戶的 SPN，您可使用 Setspn.exe 公用程式工具來進行。 建立服務帳戶的 SPN 之後，請將 WCF 設定為透過其中繼資料（WSDL）將該 SPN 發行至服務的用戶端。 不論是透過應用程式組態檔或程式碼，均可設定公開端點的端點身分識別以完成此作業。  
  
 如需 Spn、Kerberos 通訊協定和 Active Directory 的詳細資訊，請參閱[Windows 的 Kerberos 技術補充](https://go.microsoft.com/fwlink/?LinkId=88330)。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN 或 UPN 等於空字串時  
 如果您設定 SPN 或 UPN 等於空字串，那麼會發生一些不同的狀況，依使用的安全性層級和驗證模式而定：  
  
- 如果您使用傳輸層級安全性，就會選擇 NT LanMan (NTLM) 驗證。  
  
- 如果您使用訊息層級安全性，驗證可能會失敗，依驗證模式而定：  
  
- 如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `false`，則驗證失敗。  
  
- 如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `true`，則若 UPN 為空時驗證失敗，而若 SPN 為空時驗證成功。  
  
- 如果您正在直接使用 Kerberos (也就是「單次」)，則驗證失敗。  
  
### <a name="using-the-identity-element-in-configuration"></a>使用 Configuration \<中的身分識別 > 元素  
 如果您在先前對 Certificate`,` 顯示的繫結中變更用戶端認證類型，則產生的 WSDL 會包含 Base64 序列化 X.509 憑證，這個憑證可用於身分識別值，其值如以下程式碼所示。 這是 Windows 以外所有用戶端認證類型的預設值。  

 您可以使用 [設定] 中的 [<`identity`>] 專案或在程式碼中設定身分識別，變更預設服務身分識別的值或變更身分識別的類型。 下列組態程式碼會以 `contoso.com` 這個值來設定網域名稱系統 (DNS) 身分識別。  

### <a name="setting-identity-programmatically"></a>以程式設計方式設定身分識別  
 您的服務不需要明確指定身分識別，因為 WCF 會自動加以判斷。 不過，WCF 可讓您指定端點上的身分識別（如有需要）。 下列程式碼會新增具有特定 DNS 身分識別的新服務端點。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [如何：建立自訂用戶端身分識別驗證器](how-to-create-a-custom-client-identity-verifier.md)
- [服務身分識別和驗證](../feature-details/service-identity-and-authentication.md)
