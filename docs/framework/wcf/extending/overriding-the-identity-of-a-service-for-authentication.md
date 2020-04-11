---
title: 覆寫服務的身分識別以進行驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: e7273c1e140e52eb37a30b6cabeb9e9a83a6fa2d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121564"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>重寫服務識別以進行身份驗證

一般來說，您不需要在服務上設定身分識別，因為選擇用戶端認證類型，即表示服務中繼資料中公開的身分識別類型。 例如,以下配置代碼使用[\<wsHding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)`clientCredentialType`元素並將 屬性設置到 Windows。  

 下列 Web 服務描述語言 (WSDL) 片段會顯示端點先前定義的身分識別。 在此示例中,服務作為自託管服務在特定使用者帳戶(username@contoso.com) 下運行,因此用戶主體名稱 (UPN) 標識包含帳戶名稱。 UPN 在 Windows 網域中也稱為使用者登入名稱。  

 有關展示識別設定的範例應用程式,請參考[服務識別範例](../samples/service-identity-sample.md)。 有關服務識別的詳細資訊,請參閱[服務識別和身份驗證](../feature-details/service-identity-and-authentication.md)。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 驗證和身分識別  
 默認情況下,當服務配置為使用 Windows 認證時,在 WSDL 中生成包含[\<使用者主體名稱>](../../configure-apps/file-schema/wcf/userprincipalname.md)[\<或服務主體名稱>](../../configure-apps/file-schema/wcf/serviceprincipalname.md)元素的[\<標識>](../../configure-apps/file-schema/wcf/identity.md)元素。 如果服務`LocalSystem`在`LocalService`、`NetworkService`或帳戶下運行,則預設情況下`host/`\<以*主機名*>形式生成服务主体名称 (SPN),因為這些帳戶有權存取電腦的 SPN 資料。 如果服務在不同的帳戶下運行,Windows 通信基金會 (WCF)\<會以*使用者名*>@<*功能變數名稱*`>`的形式生成 UPN。 這種情況發生的原因是 Kerberos 驗證需要對用戶端提供 UPN 或 SPN，才能驗證服務。  
  
 您還可以使用[Setpn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN)工具在域中使用服務的帳戶註冊其他 SPN。 您接著就可以使用 SPN 做為服務的身分識別。 有關該工具的詳細資訊,請參閱[Setpn 概述](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))。  
  
> [!NOTE]
> 若不進行交涉而使用 Windows 認證類型，服務的使用者帳戶必須可以存取透過 Active Directory 網域登錄的 SPN。 您可以透過下列方法完成這項作業：  
  
- 使用 NetworkService 或 LocalSystem 帳戶執行服務。 由於這些帳戶有權訪問電腦加入 Active Directory 功能時建立的電腦 SPN,因此 WCF 會自動在服務的中繼資料 (WSDL) 中的服務終結點內生成正確的 SPN 元素。  
  
- 使用任意的 Active Directory 網域帳戶來執行服務。 在這個情況下，請建立該網域帳戶的 SPN，您可使用 Setspn.exe 公用程式工具來進行。 為服務的帳戶創建 SPN 後,將 WCF 配置為通過其元數據 (WSDL) 將該 SPN 發佈到服務的用戶端。 不論是透過應用程式組態檔或程式碼，均可設定公開端點的端點身分識別以完成此作業。  
  
 有關 SPN、Kerberos 協定與活動目錄的詳細資訊,請參閱[Windows 的 Kerberos 技術補充](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10))。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>SPN 或 UPN 等於空字串時  
 如果您設定 SPN 或 UPN 等於空字串，那麼會發生一些不同的狀況，依使用的安全性層級和驗證模式而定：  
  
- 如果您使用傳輸層級安全性，就會選擇 NT LanMan (NTLM) 驗證。  
  
- 如果您使用訊息層級安全性，驗證可能會失敗，依驗證模式而定：  
  
- 如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `false`，則驗證失敗。  
  
- 如果您正在使用 `spnego` 模式並且將 `AllowNtlm` 屬性設定為 `true`，則若 UPN 為空時驗證失敗，而若 SPN 為空時驗證成功。  
  
- 如果您正在直接使用 Kerberos (也就是「單次」)，則驗證失敗。  
  
### <a name="using-the-identity-element-in-configuration"></a>在\<設定中使用識別>元素  
 如果您在先前對 Certificate`,` 顯示的繫結中變更用戶端認證類型，則產生的 WSDL 會包含 Base64 序列化 X.509 憑證，這個憑證可用於身分識別值，其值如以下程式碼所示。 這是 Windows 以外所有用戶端認證類型的預設值。  

 您可以透過在設定中使用<>`identity`元素或在代碼中設置標識來更改預設服務標識的值或更改標識的類型。 下列組態程式碼會以 `contoso.com` 這個值來設定網域名稱系統 (DNS) 身分識別。  

### <a name="setting-identity-programmatically"></a>以程式設計方式設定身分識別  
 服務不必顯式指定標識,因為 WCF 會自動確定它。 但是,如果需要,WCF 允許您在終結點上指定標識。 下列程式碼會新增具有特定 DNS 身分識別的新服務端點。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：建立自訂用戶端身分識別驗證器](how-to-create-a-custom-client-identity-verifier.md)
- [服務身分識別和驗證](../feature-details/service-identity-and-authentication.md)
