---
title: 以角色為基礎的安全性
ms.date: 07/15/2020
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET]
- security [.NET], role-based
- permissions [.NET], principals
- authentication [.NET], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
ms.openlocfilehash: a03cda3aac06cc247818ccea5c61c673225d7929
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824131"
---
# <a name="role-based-security"></a>以角色為基礎的安全性

角色通常用在財務和商務應用程式中以強制執行原則。 例如，應用程式可能會根據提出要求的使用者是否為指定角色的成員，而限制正在處理之交易的大小。 職員可能具有授權，可以處理小於指定臨界值的交易，監督員可能有更高的限制，而副總裁可能有再更高的限制 (或根本沒有限制)。 以角色為基礎的安全性也可用於應用程式需要多重許可才能完成動作之時。 這樣的情況可能是採購系統，任何員工可以產生採購要求，但只有採購人員可以將該要求轉換成可以傳送給供應商的訂單。  
  
 .NET 以角色為基礎的安全性可透過建立主體相關資訊來支援授權，而此主體是從關聯的身分識別（可供目前的執行緒使用）所構成。 識別 (以及它協助定義的主體) 可以是根據 Windows 帳戶，或者是與 Windows 帳戶無關的自訂識別。 .NET 應用程式可以根據主體的身分識別或角色成員資格，或兩者進行授權決策。 角色是在安全性方面具有相同權限之主體的命名集 (例如櫃員或經理)。 主體可以是一個或多個角色的成員。 因此，應用程式可以使用角色成員資格，來判斷主體是否已獲授權執行要求的動作。  
  
 為了讓代碼啟用安全性更容易使用且一致，.NET 以角色為基礎的安全性所提供的 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> 物件，可讓 common language runtime 以類似于代碼啟用安全性檢查的方式來執行授權。 <xref:System.Security.Permissions.PrincipalPermission> 類別代表主體必須符合，而且同時與宣告式和命令式安全性檢查相容的識別或角色。 您也可以直接存取主體的識別資訊，並視需要在程式碼中執行角色和識別檢查。  
  
 .NET 提供以角色為基礎的安全性支援，其具有彈性且可擴充，足以滿足各式各樣應用程式的需求。 您可以選擇與現有的驗證基礎結構 (例如 COM + 1.0 服務) 交互操作，或建立自訂驗證系統。 以角色為基礎的安全性特別適合用於 ASP.NET Web 應用程式，它們主要是在伺服器上進行處理。 不過，您可以在用戶端或伺服器上使用 .NET 角色型安全性。  
  
 閱讀本節之前，請確定您瞭解 [重要安全性概念](key-security-concepts.md)中顯示的內容。  
  
## <a name="see-also"></a>請參閱
  
- [Principal 和 Identity 物件](principal-and-identity-objects.md)
- [重要的安全性概念](key-security-concepts.md)
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
- [ASP.NET Core 安全性](/aspnet/core/security/)
