---
title: 雲端原生應用程式中的驗證和授權
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式中的驗證和授權
ms.date: 05/13/2020
ms.openlocfilehash: bbd2df110dd7a7dc7363e9c07d87f1fa12f4e464
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161135"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>雲端原生應用程式中的驗證與授權

*驗證* 是判斷安全性主體身分識別的程式。 *授權* 是指授與已驗證的主體許可權來執行動作或存取資源的動作。 有時會縮短驗證 `AuthN` ，並且將授權縮短為 `AuthZ` 。 雲端原生應用程式需要依賴開放式 HTTP 通訊協定來驗證安全性主體，因為用戶端和應用程式都可以在任何平臺或裝置上的世界各地執行。 唯一的常見因素是 HTTP。

許多組織仍依賴本機驗證服務，例如 Active Directory 同盟服務 (ADFS) 。 雖然此方法在傳統上是針對內部部署驗證需求提供服務，但雲端原生應用程式可從專為雲端所設計的系統中獲益。 最近的2019英國國家網路安全中心 (NCSC) 諮詢指出，「使用 Azure AD 作為主要驗證來源的組織實際上會降低其與 ADFS 相較的風險」。 [這項分析](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)中所述的某些原因包括：

- 存取一組完整的 Microsoft 認證保護技術。
- 大部分的組織都已經依賴 Azure AD 的程度。
- NTLM 雜湊的雙重雜湊可確保洩露不允許在本機 Active Directory 中使用的認證。

## <a name="references"></a>參考資料

- [驗證基本概念](/azure/active-directory/develop/authentication-scenarios)
- [存取權杖和宣告](/azure/active-directory/develop/access-tokens)
- [可能有時間揚棄您的內部部署驗證服務](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[上一個](identity.md) 
>[下一步](azure-active-directory.md)
