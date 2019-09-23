---
title: GRPC 應用程式中的安全性-WCF 開發人員適用的 gRPC
description: GRPC 中的呼叫和通道驗證和授權的總覽。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184138"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="e11a4-103">GRPC 應用程式中的安全性</span><span class="sxs-lookup"><span data-stu-id="e11a4-103">Security in gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e11a4-104">在任何真實世界的案例中，保護應用程式和服務都是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="e11a4-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="e11a4-105">安全性涵蓋三個主要領域：加密網路流量以防止不良執行者攔截它;驗證用戶端和伺服器以建立身分識別和信任;和會授權用戶端控制系統的存取權，並根據身分識別套用許可權。</span><span class="sxs-lookup"><span data-stu-id="e11a4-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="e11a4-106">**驗證**會考慮建立用戶端或伺服器的身分識別。</span><span class="sxs-lookup"><span data-stu-id="e11a4-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="e11a4-107">**授權**會負責判斷用戶端是否有存取資源或發出命令的許可權。</span><span class="sxs-lookup"><span data-stu-id="e11a4-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="e11a4-108">本章將涵蓋 gRPC for ASP.NET Core 中驗證和授權的功能，並討論使用 TLS 加密連線的網路安全性。</span><span class="sxs-lookup"><span data-stu-id="e11a4-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="e11a4-109">WCF 驗證和授權</span><span class="sxs-lookup"><span data-stu-id="e11a4-109">WCF authentication and authorization</span></span>

<span data-ttu-id="e11a4-110">在 WCF 中，驗證和授權是以不同的方式處理，視使用的傳輸和系結而定。</span><span class="sxs-lookup"><span data-stu-id="e11a4-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="e11a4-111">WCF 支援各種 WS-\*安全性標準，以及 windows 驗證，適用于在 IIS 中執行的 HTTP 服務或 windows 系統之間的 NetTCP 服務。</span><span class="sxs-lookup"><span data-stu-id="e11a4-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="e11a4-112">gRPC 驗證與授權</span><span class="sxs-lookup"><span data-stu-id="e11a4-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="e11a4-113">gRPC 驗證和授權適用于兩個層級。</span><span class="sxs-lookup"><span data-stu-id="e11a4-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="e11a4-114">呼叫層級驗證/授權通常會使用在進行呼叫時于中繼資料中套用的權杖來處理。</span><span class="sxs-lookup"><span data-stu-id="e11a4-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="e11a4-115">通道層級驗證會使用在連線層級套用的用戶端憑證，也可以包含要自動套用至通道上每個呼叫的呼叫層級驗證/授權認證。</span><span class="sxs-lookup"><span data-stu-id="e11a4-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="e11a4-116">您可以使用其中一種或兩種機制來保護您的服務。</span><span class="sxs-lookup"><span data-stu-id="e11a4-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="e11a4-117">GRPC 的 ASP.NET Core 實作為使用大部分標準 ASP.NET Core 機制來支援驗證和授權：</span><span class="sxs-lookup"><span data-stu-id="e11a4-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="e11a4-118">呼叫驗證</span><span class="sxs-lookup"><span data-stu-id="e11a4-118">Call authentication</span></span>
  - <span data-ttu-id="e11a4-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e11a4-119">Azure Active Directory</span></span>
  - <span data-ttu-id="e11a4-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="e11a4-120">IdentityServer</span></span>
  - <span data-ttu-id="e11a4-121">JWT 持有人權杖</span><span class="sxs-lookup"><span data-stu-id="e11a4-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="e11a4-122">OAuth 2。0</span><span class="sxs-lookup"><span data-stu-id="e11a4-122">OAuth 2.0</span></span>
  - <span data-ttu-id="e11a4-123">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="e11a4-123">OpenID Connect</span></span>
  - <span data-ttu-id="e11a4-124">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="e11a4-124">WS-Federation</span></span>
- <span data-ttu-id="e11a4-125">通道驗證</span><span class="sxs-lookup"><span data-stu-id="e11a4-125">Channel authentication</span></span>
  - <span data-ttu-id="e11a4-126">用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="e11a4-126">Client Certificate</span></span>

<span data-ttu-id="e11a4-127">呼叫驗證方法全都以*權杖*為基礎。</span><span class="sxs-lookup"><span data-stu-id="e11a4-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="e11a4-128">唯一的真正差異在於權杖的產生方式，以及用來驗證 ASP.NET Core 服務中之權杖的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e11a4-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="e11a4-129">如需詳細資訊，請參閱[Microsoft Docs 上的驗證和授權檔](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0)。</span><span class="sxs-lookup"><span data-stu-id="e11a4-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="e11a4-130">在 TLS 加密的 HTTP/2 連線上使用 gRPC 時，用戶端與伺服器之間的所有流量都會加密，即使您未使用通道層級驗證也一樣。</span><span class="sxs-lookup"><span data-stu-id="e11a4-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="e11a4-131">本章將示範如何將呼叫認證和通道認證套用至 gRPC 服務，以及如何使用 .NET Core gRPC 用戶端的認證來向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e11a4-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e11a4-132">[上一頁](client-libraries.md)
>[下一頁](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="e11a4-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
