---
title: "以角色為基礎的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 83a3f58fc13eb1aaacb99a3f35c3149d78451c23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="role-based-security"></a>以角色為基礎的安全性
角色通常用在財務和商務應用程式中以強制執行原則。 例如，應用程式可能會根據提出要求的使用者是否為指定角色的成員，而限制正在處理之交易的大小。 職員可能具有授權，可以處理小於指定臨界值的交易，監督員可能有更高的限制，而副總裁可能有再更高的限制 (或根本沒有限制)。 以角色為基礎的安全性也可用於應用程式需要多重許可才能完成動作之時。 這樣的情況可能是採購系統，任何員工可以產生採購要求，但只有採購人員可以將該要求轉換成可以傳送給供應商的訂單。  
  
 .NET Framework 以角色為基礎的安全性，是藉由將主體的有關資訊 (這是從關聯的識別所建構) 提供給目前的執行緒，而支援授權。 識別 (以及它協助定義的主體) 可以是根據 Windows 帳戶，或者是與 Windows 帳戶無關的自訂識別。 .NET Framework 應用程式可以依據主體的識別及/或角色成員資格，做出授權決策。 角色是在安全性方面具有相同權限之主體的命名集 (例如櫃員或經理)。 主體可以是一個或多個角色的成員。 因此，應用程式可以使用角色成員資格，來判斷主體是否已獲授權執行要求的動作。  
  
 為了提供程式碼存取安全性的使用方便性和一致性，.NET Framework 以角色為基礎的安全性提供 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> 物件，會讓 Common Language Runtime 能以和程式碼存取安全性檢查類似的方式執行授權。 <xref:System.Security.Permissions.PrincipalPermission> 類別代表主體必須符合，而且同時與宣告式和命令式安全性檢查相容的識別或角色。 您也可以直接存取主體的識別資訊，並視需要在程式碼中執行角色和識別檢查。  
  
 .NET Framework 提供以角色為基礎的安全性支援，具有足夠的彈性和可擴充性，可滿足廣泛應用程式的需要。 您可以選擇與現有的驗證基礎結構 (例如 COM + 1.0 服務) 交互操作，或建立自訂驗證系統。 以角色為基礎的安全性特別適合用於 ASP.NET Web 應用程式，它們主要是在伺服器上進行處理。 不過，.NET Framework 以角色為基礎的安全性可以用在用戶端或伺服器上。  
  
 之前讀取這個區段，請確定您了解中所呈現的題材[重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[Principal 和 Identity 物件](../../../docs/standard/security/principal-and-identity-objects.md)|說明如何設定和管理 Windows 和泛型識別和主體。|  
|[重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)|介紹您在使用 .NET Framework 安全性之前必須了解的基本概念。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
