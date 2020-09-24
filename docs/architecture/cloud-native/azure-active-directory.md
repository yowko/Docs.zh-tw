---
title: Azure Active Directory
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 55787f3565fc15bb25cf1a101aa5c1e3ddefe5e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161109"
---
# <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Azure Active Directory (Azure AD) 以服務方式提供身分識別和存取管理。 客戶可以使用它來設定和維護使用者是誰、要儲存的資訊、誰可以存取該資訊、誰可以管理，以及哪些應用程式可以存取它。 AAD 可以驗證使用者是否已設定要使用它的應用程式，並提供單一登入 (SSO) 體驗。 它可以單獨使用，也可以與內部部署環境中執行的 Windows AD 整合。

Azure AD 是針對雲端所建立。 這是真正的雲端原生身分識別解決方案，使用 REST 型的圖形 API 和 OData 語法進行查詢，不同于使用 LDAP 的 Windows AD。 內部部署 Active Directory 可以使用身分識別同步服務，將使用者屬性同步至雲端，以允許在雲端中使用 Azure AD 進行所有驗證。 或者，您也可以透過 Connect 來設定驗證，以透過 ADFS 傳回到本機 Active Directory，以供 Windows AD 內部部署完成。

Azure AD 支援公司品牌的登入畫面、多 factory 驗證，以及用來為裝載于內部部署之應用程式提供 SSO 的雲端式應用程式 proxy。 它提供不同類型的安全性報告和警示功能。

## <a name="references"></a>參考資料

- [Microsoft 身分識別平台](/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[上一個](authentication-authorization.md) 
>[下一步](identity-server.md)
