---
title: JSON Web 語彙基元處理常式
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 3dc76f3de714fd91d397cc240d02a1a8605fe18b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045324"
---
# <a name="json-web-token-handler"></a>JSON Web 語彙基元處理常式
適用於 Windows Identity Foundation 的 JSON Web 權杖處理常式擴充功能可讓您在應用程式中建立和驗證 JSON Web 權杖 (JWT)。 如同其他內建安全性權杖處理常式一樣，JWT 權杖處理常式可以設定為在 WIF 管線中執行，但是它也可以單獨用來在輕量型應用程式中執行權杖驗證。 使用 OAuth 2.0 承載權杖配置 (例如驗證 Microsoft Azure Active Directory) 時，JWT 權杖處理常式特別有用。  
  
 JWT 權杖處理常式是以 NuGet 套件的形式供您使用。 如需詳細資訊，請參閱[下載 JSON Web 權杖處理常式套件](downloading-the-json-web-token-handler-package.md)。  
  
## <a name="scenarios"></a>案例  
 JWT 權杖處理常式適用於下列重要案例：  
  
- **驗證服務器應用程式中的 JWT 權杖**：在此案例中，名為 Litware 的公司有一個伺服器應用程式，它會使用 WIF 來處理 web 登入要求。 Litware 希望讓此應用程式使用 JWT 權杖進行驗證， 並使用 JWT 權杖處理常式更新應用程式，然後更新應用程式組態，在 WIF 管線中加入 JWT 權杖處理常式。 更新之後，當新的要求進入 WIF 管線時，應用程式隨即使用新處理常式驗證 JWT 權杖並成功驗證。  
  
- **驗證 REST Web 服務中的 JWT 權杖**：在此案例中，名為 Litware 的公司有一個由 Windows Azure Active Directory 保護的 REST web 服務。 傳送至 Web 服務的要求必須由 Microsoft Azure AD 進行驗證，在驗證成功之後，Microsoft Azure AD 隨即發行 JWT 權杖。 Litware 開發了必須存取 Web 服務的用戶端應用程式。 用戶端向 Web 服務提出要求，並附上 Microsoft Azure AD 發行的 JWT 權杖，Web 服務隨即使用 JWT 權杖處理常式進行驗證。 在 JWT 權杖處理常式驗證權杖後，Web 服務隨即將所需資源傳回至用戶端。  
  
## <a name="features"></a>功能  
 JWT 權杖處理常式提供下列功能：  
  
- **驗證 JWT 權杖**：權杖處理常式的驗證邏輯可以輕鬆地驗證 JWT 權杖，這可能是應用程式 WIF 管線的一部分，或是獨立于 WIF 的呼叫。  
  
- **建立 JWT 權杖**：JWT 權杖處理常式可用來為下游服務中的授權建立 JWT 權杖
