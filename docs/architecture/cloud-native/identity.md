---
title: 身分識別
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |身份
ms.date: 05/13/2020
ms.openlocfilehash: 66ff29947093d7c4fe57b11039190836dc37db08
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163748"
---
# <a name="identity"></a><span data-ttu-id="51e31-103">身分識別</span><span class="sxs-lookup"><span data-stu-id="51e31-103">Identity</span></span>

<span data-ttu-id="51e31-104">大部分的軟體應用程式都必須知道呼叫它們的使用者或進程。</span><span class="sxs-lookup"><span data-stu-id="51e31-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="51e31-105">與應用程式互動的使用者或進程稱為安全性主體，而驗證和授權這些主體的程式稱為身分識別管理或單純身分 *識別*。</span><span class="sxs-lookup"><span data-stu-id="51e31-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="51e31-106">簡單的應用程式可能會在應用程式中包含所有的身分識別管理，但這種方法並不適合許多應用程式和許多類型的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="51e31-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="51e31-107">Windows 支援使用 Active Directory 來提供集中式驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="51e31-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="51e31-108">雖然此解決方案在公司網路中是有效的，但它並不是專為 AD 網域以外的使用者或應用程式所使用而設計。</span><span class="sxs-lookup"><span data-stu-id="51e31-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="51e31-109">隨著以網際網路為基礎的應用程式成長和雲端原生應用程式的成長，安全性模型也已演進。</span><span class="sxs-lookup"><span data-stu-id="51e31-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="51e31-110">在現今的雲端原生身分識別模型中，架構會假設為已散發。</span><span class="sxs-lookup"><span data-stu-id="51e31-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="51e31-111">應用程式可以在任何地方部署，並可在任何地方與其他應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="51e31-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="51e31-112">用戶端可能會從任何地方與這些應用程式通訊，事實上，用戶端可能包含平臺和裝置的任何組合。</span><span class="sxs-lookup"><span data-stu-id="51e31-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="51e31-113">雲端原生身分識別解決方案利用開放式標準，從用戶端達成安全的應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="51e31-113">Cloud-native identity solutions leverage open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="51e31-114">這些用戶端的範圍是從電腦或手機上的使用者，到線上裝載的其他應用程式，到在世界各地執行任何軟體平臺的機上盒和 IOT 裝置。</span><span class="sxs-lookup"><span data-stu-id="51e31-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="51e31-115">新式的雲端原生身分識別解決方案通常會利用安全權杖服務/伺服器 (STS) 的存取權杖，在判斷身分識別之後，將其授與安全性主體。</span><span class="sxs-lookup"><span data-stu-id="51e31-115">Modern cloud-native identity solutions typically leverage access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="51e31-116">存取權杖（通常是 (JWT) 的 JSON Web 權杖）包含有關安全性主體的 *宣告* 。</span><span class="sxs-lookup"><span data-stu-id="51e31-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="51e31-117">這些宣告最少包含使用者的身分識別，但也可能包含其他宣告，可供應用程式用來判斷授與主體的存取層級。</span><span class="sxs-lookup"><span data-stu-id="51e31-117">These claims will minimally include the user's identity but may also include additional claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="51e31-118">通常，STS 只負責驗證主體。</span><span class="sxs-lookup"><span data-stu-id="51e31-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="51e31-119">判斷其對資源的存取層級會保留給應用程式的其他部分。</span><span class="sxs-lookup"><span data-stu-id="51e31-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="51e31-120">參考資料</span><span class="sxs-lookup"><span data-stu-id="51e31-120">References</span></span>

- [<span data-ttu-id="51e31-121">Microsoft 身分識別平台</span><span class="sxs-lookup"><span data-stu-id="51e31-121">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="51e31-122">[上一個](azure-monitor.md) 
>[下一步](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="51e31-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
