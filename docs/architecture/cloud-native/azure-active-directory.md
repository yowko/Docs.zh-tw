---
title: Azure Active Directory
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 03f5ea8e84bc3c4a2a88a63d4b109aabf0c64f36
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614275"
---
# <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Azure Active Directory （Azure AD）提供身分識別和存取管理服務。 客戶使用它來設定及維護使用者的身分、要儲存哪些資訊、誰可以存取該資訊、誰可以進行管理，以及哪些應用程式可以存取它。 AAD 可以針對設定為使用它的應用程式驗證使用者，提供單一登入（SSO）體驗。 它可以單獨使用，或與內部部署環境中執行的 Windows AD 整合。

Azure AD 是針對雲端所建立。 它真的是一個雲端原生身分識別解決方案，它使用 REST 架構的圖形 API 和 OData 語法來進行查詢，不同于使用 LDAP 的 Windows AD。 內部部署 Active Directory 可以使用身分識別同步處理服務將使用者屬性同步處理至雲端，允許在雲端中使用 Azure AD 進行所有驗證。 或者，您也可以透過 Connect 設定驗證，以經由 ADFS 傳回到本機 Active Directory，以供 Windows AD 內部部署完成。

Azure AD 支援公司品牌的登入畫面、多工廠驗證和雲端式應用程式 proxy，這些都是用來為裝載于內部部署的應用程式提供 SSO。 它提供不同種類的安全性報告和警示功能。

## <a name="references"></a>參考

- [Microsoft 身分識別平台](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[上一個](authentication-authorization.md) 
>[下一步](identity-server.md)
