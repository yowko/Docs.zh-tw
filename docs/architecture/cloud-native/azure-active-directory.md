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
# <a name="azure-active-directory"></a><span data-ttu-id="4df01-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4df01-103">Azure Active Directory</span></span>

<span data-ttu-id="4df01-104">Microsoft Azure Active Directory (Azure AD) 以服務方式提供身分識別和存取管理。</span><span class="sxs-lookup"><span data-stu-id="4df01-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="4df01-105">客戶可以使用它來設定和維護使用者是誰、要儲存的資訊、誰可以存取該資訊、誰可以管理，以及哪些應用程式可以存取它。</span><span class="sxs-lookup"><span data-stu-id="4df01-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="4df01-106">AAD 可以驗證使用者是否已設定要使用它的應用程式，並提供單一登入 (SSO) 體驗。</span><span class="sxs-lookup"><span data-stu-id="4df01-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="4df01-107">它可以單獨使用，也可以與內部部署環境中執行的 Windows AD 整合。</span><span class="sxs-lookup"><span data-stu-id="4df01-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="4df01-108">Azure AD 是針對雲端所建立。</span><span class="sxs-lookup"><span data-stu-id="4df01-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="4df01-109">這是真正的雲端原生身分識別解決方案，使用 REST 型的圖形 API 和 OData 語法進行查詢，不同于使用 LDAP 的 Windows AD。</span><span class="sxs-lookup"><span data-stu-id="4df01-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="4df01-110">內部部署 Active Directory 可以使用身分識別同步服務，將使用者屬性同步至雲端，以允許在雲端中使用 Azure AD 進行所有驗證。</span><span class="sxs-lookup"><span data-stu-id="4df01-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="4df01-111">或者，您也可以透過 Connect 來設定驗證，以透過 ADFS 傳回到本機 Active Directory，以供 Windows AD 內部部署完成。</span><span class="sxs-lookup"><span data-stu-id="4df01-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="4df01-112">Azure AD 支援公司品牌的登入畫面、多 factory 驗證，以及用來為裝載于內部部署之應用程式提供 SSO 的雲端式應用程式 proxy。</span><span class="sxs-lookup"><span data-stu-id="4df01-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="4df01-113">它提供不同類型的安全性報告和警示功能。</span><span class="sxs-lookup"><span data-stu-id="4df01-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="4df01-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="4df01-114">References</span></span>

- [<span data-ttu-id="4df01-115">Microsoft 身分識別平台</span><span class="sxs-lookup"><span data-stu-id="4df01-115">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="4df01-116">[上一個](authentication-authorization.md) 
>[下一步](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="4df01-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
