---
title: 驗證簽發者名稱登錄
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: aa6a71ced0f9bf969eb6c8800739f629810dd63f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645899"
---
# <a name="validating-issuer-name-registry"></a>驗證簽發者名稱登錄
適用於 Windows Identity Foundation 的驗證簽發者名稱登錄 (Validating Issuer Name Registry，VINR) 可讓多租用戶應用程式確保傳入的權杖是由信任的租用戶和識別提供者發行。 這項功能對使用 Microsoft Azure Active Directory 的多租用戶應用程式特別有用，因為 Microsoft Azure AD 發行的所有權杖都是使用相同的憑證來簽署。 為了區別來自使用相同憑證 (因此具有相同指紋) 之多個租用戶的要求，應用程式必須保存每個租用戶的簽發者名稱，才能執行驗證邏輯。 VINR 不僅提供這項功能，還能讓您加入自訂驗證邏輯，或是將簽發者登錄資料儲存在組態檔以外的位置。 這項擴充功能可以加入至應用程式的 WIF 管線，也可以單獨使用。  
  
 VINR 是以 NuGet 套件的形式供您使用。 如需詳細資訊，請參閱[下載驗證簽發者名稱登錄套件](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md)。  
  
## <a name="scenarios"></a>案例  
 VINR 適用於下列重要案例：  
  
- **驗證權杖，以在多租用戶應用程式中的**:在此案例中，名稱為 Litware 的公司開發使用例如 Windows Azure AD 的身分識別提供者的多租用戶應用程式。 此應用程式有兩種客戶：Contoso 和 Fabrikam。 當 Fabrikam 的使用者要在 Litware 的應用程式中進行驗證時，Microsoft Azure AD 會使用標準憑證來簽署產生的權杖，而且要求會由 Fabrikam 提出。 應用程式必須確定簽發者名稱和權杖都有效，而且必須區分 Microsoft Azure AD 使用相同憑證簽署、但卻是來自 Contoso 的要求。 VINR 可讓 Litware 的應用程式區分和驗證來自多個租用戶 (例如 Contoso 和 Fabrikam) 的要求。  
  
## <a name="features"></a>功能  
 VINR 提供下列功能：  
  
- **簽發者名稱和多租用戶應用程式的權杖驗證**:確認簽發者名稱 （租用戶），以及是否使用識別提供者的有效憑證簽署權杖，藉以驗證傳入的權杖。  
  
- **自訂驗證邏輯和資料存放區擴充性**:提供擴充性讓您插入專屬驗證邏輯，並指定預設組態檔以外的資料存放區。
