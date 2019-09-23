---
title: Azure Active Directory
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 207043507a9052c47683383a98cef6417a1a2740
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183690"
---
# <a name="azure-active-directory"></a><span data-ttu-id="c50a4-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c50a4-103">Azure Active Directory</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c50a4-104">Microsoft Azure Active Directory （Azure AD）提供身分識別和存取管理服務。</span><span class="sxs-lookup"><span data-stu-id="c50a4-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="c50a4-105">客戶使用它來設定及維護使用者的身分、要儲存哪些資訊、誰可以存取該資訊、誰可以進行管理，以及哪些應用程式可以存取它。</span><span class="sxs-lookup"><span data-stu-id="c50a4-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="c50a4-106">AAD 可以針對設定為使用它的應用程式驗證使用者，提供單一登入（SSO）體驗。</span><span class="sxs-lookup"><span data-stu-id="c50a4-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="c50a4-107">它可以單獨使用，或與內部部署環境中執行的 Windows AD 整合。</span><span class="sxs-lookup"><span data-stu-id="c50a4-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="c50a4-108">Azure AD 是針對雲端所建立。</span><span class="sxs-lookup"><span data-stu-id="c50a4-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="c50a4-109">它真的是一個雲端原生身分識別解決方案，它使用 REST 架構的圖形 API 和 OData 語法來進行查詢，不同于使用 LDAP 的 Windows AD。</span><span class="sxs-lookup"><span data-stu-id="c50a4-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="c50a4-110">內部部署 Active Directory 可以使用身分識別同步處理服務將使用者屬性同步處理至雲端，允許在雲端中使用 Azure AD 進行所有驗證。</span><span class="sxs-lookup"><span data-stu-id="c50a4-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="c50a4-111">或者，您也可以透過 Connect 設定驗證，以經由 ADFS 傳回到本機 Active Directory，以供 Windows AD 內部部署完成。</span><span class="sxs-lookup"><span data-stu-id="c50a4-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="c50a4-112">Azure AD 支援公司品牌的登入畫面、多工廠驗證和雲端式應用程式 proxy，這些都是用來為裝載于內部部署的應用程式提供 SSO。</span><span class="sxs-lookup"><span data-stu-id="c50a4-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="c50a4-113">它提供不同種類的安全性報告和警示功能。</span><span class="sxs-lookup"><span data-stu-id="c50a4-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="c50a4-114">reference</span><span class="sxs-lookup"><span data-stu-id="c50a4-114">References</span></span>

- [<span data-ttu-id="c50a4-115">Microsoft 身分識別平臺</span><span class="sxs-lookup"><span data-stu-id="c50a4-115">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="c50a4-116">[上一頁](authentication-authorization.md)
>[下一頁](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="c50a4-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
