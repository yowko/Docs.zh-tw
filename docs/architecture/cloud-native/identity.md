---
title: 身分識別
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |2x2
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183046"
---
# <a name="identity"></a><span data-ttu-id="31628-103">身分識別</span><span class="sxs-lookup"><span data-stu-id="31628-103">Identity</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="31628-104">大部分的軟體應用程式必須對呼叫它們的使用者或進程有一些瞭解。</span><span class="sxs-lookup"><span data-stu-id="31628-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="31628-105">與應用程式互動的使用者或進程稱為「安全性主體」，而驗證和授權這些主體的流程稱為「身分識別管理」，或簡稱「身分*識別*」。</span><span class="sxs-lookup"><span data-stu-id="31628-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="31628-106">簡單的應用程式可能會在應用程式內包含所有的身分識別管理，但這種方法並不適合許多應用程式和許多類型的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="31628-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="31628-107">Windows 支援使用 Active Directory 來提供集中式驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="31628-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="31628-108">雖然此解決方案在公司網路內有效，但並不是專供 AD 網域外的使用者或應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="31628-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="31628-109">隨著以網際網路為基礎的應用程式成長，以及雲端原生應用程式的增加，安全性模型已經進化。</span><span class="sxs-lookup"><span data-stu-id="31628-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="31628-110">在現今的雲端原生身分識別模型中，會假設架構已散發。</span><span class="sxs-lookup"><span data-stu-id="31628-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="31628-111">應用程式可以在任何地方部署，而且可能會與其他應用程式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="31628-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="31628-112">用戶端可以從任何地方與這些應用程式通訊，事實上，用戶端可能是由平臺和裝置的任何組合所組成。</span><span class="sxs-lookup"><span data-stu-id="31628-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="31628-113">雲端原生身分識別解決方案會運用開放式標準，以達成用戶端安全的應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="31628-113">Cloud-native identity solutions leverage open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="31628-114">這些用戶端的範圍是從 Pc 或手機上的人力使用者，到在線上隨處裝載的其他應用程式，到在世界各地執行任何軟體平臺的機上盒和 IOT 裝置。</span><span class="sxs-lookup"><span data-stu-id="31628-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="31628-115">新式雲端原生身分識別解決方案通常會在判斷身分識別之後，利用安全權杖服務/伺服器（STS）發行給安全性主體的存取權杖。</span><span class="sxs-lookup"><span data-stu-id="31628-115">Modern cloud-native identity solutions typically leverage access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="31628-116">存取權杖（通常是 JSON Web 權杖（JWT））包含有關安全性主體的*宣告*。</span><span class="sxs-lookup"><span data-stu-id="31628-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="31628-117">這些宣告最少會包含使用者的身分識別，但也可能包含可供應用程式用來判斷授與主體之存取層級的其他宣告。</span><span class="sxs-lookup"><span data-stu-id="31628-117">These claims will minimally include the user's identity but may also include additional claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="31628-118">通常，STS 只負責驗證主體。</span><span class="sxs-lookup"><span data-stu-id="31628-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="31628-119">判斷其對資源的存取層級，會留給應用程式的其他部分。</span><span class="sxs-lookup"><span data-stu-id="31628-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="31628-120">reference</span><span class="sxs-lookup"><span data-stu-id="31628-120">References</span></span>

- [<span data-ttu-id="31628-121">Microsoft 身分識別平臺</span><span class="sxs-lookup"><span data-stu-id="31628-121">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="31628-122">[上一頁](azure-monitor.md)
>[下一頁](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="31628-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
