---
title: 雲原生應用中的身份驗證和授權
description: 為 Azure 構建雲本機 .NET 應用 |雲本機應用中的身份驗證和授權
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805552"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="2afc6-103">雲端原生應用程式中的驗證與授權</span><span class="sxs-lookup"><span data-stu-id="2afc6-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2afc6-104">*身份驗證*是確定安全主體身份的過程。</span><span class="sxs-lookup"><span data-stu-id="2afc6-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="2afc6-105">*授權*是授予經過身份驗證的主體許可權以執行操作或訪問資源的行為。</span><span class="sxs-lookup"><span data-stu-id="2afc6-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="2afc6-106">有時身份驗證將縮短為`AuthN`,授權將縮短`AuthZ`為 。</span><span class="sxs-lookup"><span data-stu-id="2afc6-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="2afc6-107">雲原生應用程式需要依靠基於 HTTP 的開放式協議來驗證安全主體,因為用戶端和應用程式都可以在世界任何平臺或設備上運行。</span><span class="sxs-lookup"><span data-stu-id="2afc6-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="2afc6-108">唯一的常見因素是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="2afc6-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="2afc6-109">許多組織仍然依賴於本地身份驗證服務,如活動目錄聯合服務 (ADFS)。</span><span class="sxs-lookup"><span data-stu-id="2afc6-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="2afc6-110">雖然這種方法傳統上為組織提供了良好的本地身份驗證需求,但雲原生應用程式受益於專為雲設計的系統。</span><span class="sxs-lookup"><span data-stu-id="2afc6-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="2afc6-111">最近 2019 年,英國國家網路安全中心 (NCSC) 的一份通報指出,「使用 Azure AD 作為主要身份驗證源的組織實際上將降低與 ADFS 相比的風險。</span><span class="sxs-lookup"><span data-stu-id="2afc6-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="2afc6-112">[此分析](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)中概述的一些原因包括:</span><span class="sxs-lookup"><span data-stu-id="2afc6-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="2afc6-113">訪問全套 Microsoft 認證保護技術。</span><span class="sxs-lookup"><span data-stu-id="2afc6-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="2afc6-114">大多數組織在某種程度上已經依賴於 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="2afc6-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="2afc6-115">NTLM 哈希的雙重哈希可確保折衷不會允許在本地活動目錄中工作的憑據。</span><span class="sxs-lookup"><span data-stu-id="2afc6-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="2afc6-116">參考</span><span class="sxs-lookup"><span data-stu-id="2afc6-116">References</span></span>

- [<span data-ttu-id="2afc6-117">驗證基本概念</span><span class="sxs-lookup"><span data-stu-id="2afc6-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="2afc6-118">存取權杖與宣告</span><span class="sxs-lookup"><span data-stu-id="2afc6-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="2afc6-119">可能是時候放棄本地身份驗證服務了</span><span class="sxs-lookup"><span data-stu-id="2afc6-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="2afc6-120">[前一個](identity.md)
>[下一個](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="2afc6-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
