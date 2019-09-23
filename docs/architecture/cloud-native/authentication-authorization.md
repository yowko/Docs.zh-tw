---
title: 雲端原生應用程式中的驗證和授權
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |雲端原生應用程式中的驗證和授權
ms.date: 06/30/2019
ms.openlocfilehash: a397175e98c2e8103d2a8c372c81fcca65f19b11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183725"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="5efcf-103">雲端原生應用程式中的驗證和授權</span><span class="sxs-lookup"><span data-stu-id="5efcf-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5efcf-104">*驗證*是判斷安全性主體身分識別的程式。</span><span class="sxs-lookup"><span data-stu-id="5efcf-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="5efcf-105">*授權*是授與已驗證的主體許可權來執行動作或存取資源的動作。</span><span class="sxs-lookup"><span data-stu-id="5efcf-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="5efcf-106">有時會將驗證縮短`AuthN`為，並將授權`AuthZ`縮短為。</span><span class="sxs-lookup"><span data-stu-id="5efcf-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="5efcf-107">雲端原生應用程式必須依賴 open HTTP 型通訊協定來驗證安全性主體，因為用戶端和應用程式都可以在任何平臺或裝置上的世界各地執行。</span><span class="sxs-lookup"><span data-stu-id="5efcf-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="5efcf-108">唯一的常見因素是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="5efcf-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="5efcf-109">許多組織仍依賴本機驗證服務，例如 Active Directory 同盟服務（ADFS）。</span><span class="sxs-lookup"><span data-stu-id="5efcf-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="5efcf-110">雖然這種方法在過去是針對內部部署驗證需求而提供服務，但雲端原生應用程式可受益于專為雲端設計的系統。</span><span class="sxs-lookup"><span data-stu-id="5efcf-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="5efcf-111">最近的2019英國國家網路安全中心（NCSC）諮詢指出「使用 Azure AD 做為主要驗證來源的組織，實際上會降低其與 ADFS 的風險。」</span><span class="sxs-lookup"><span data-stu-id="5efcf-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="5efcf-112">[這項分析](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)中所述的一些原因包括：</span><span class="sxs-lookup"><span data-stu-id="5efcf-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="5efcf-113">存取一組完整的 Microsoft 認證保護技術。</span><span class="sxs-lookup"><span data-stu-id="5efcf-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="5efcf-114">大部分的組織都已經依賴 Azure AD 到某種程度。</span><span class="sxs-lookup"><span data-stu-id="5efcf-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="5efcf-115">NTLM 雜湊的雙重雜湊可確保洩露不會允許在本機 Active Directory 中使用的認證。</span><span class="sxs-lookup"><span data-stu-id="5efcf-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="5efcf-116">reference</span><span class="sxs-lookup"><span data-stu-id="5efcf-116">References</span></span>

- [<span data-ttu-id="5efcf-117">驗證基本概念</span><span class="sxs-lookup"><span data-stu-id="5efcf-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="5efcf-118">存取權杖和宣告</span><span class="sxs-lookup"><span data-stu-id="5efcf-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="5efcf-119">可能有時間揚棄您的內部部署驗證服務</span><span class="sxs-lookup"><span data-stu-id="5efcf-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="5efcf-120">[上一頁](identity.md)
>[下一頁](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="5efcf-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
