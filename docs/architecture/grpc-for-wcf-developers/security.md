---
title: GRPC 應用程式中的安全性-適用于 WCF 開發人員的 gRPC
description: GRPC 中的呼叫和通道驗證與授權總覽。
ms.date: 12/15/2020
ms.openlocfilehash: a5c16a4a4f7567e23bf4f9e3049fe116086daf12
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938087"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="4103e-103">gRPC 應用程式中的安全性</span><span class="sxs-lookup"><span data-stu-id="4103e-103">Security in gRPC applications</span></span>

<span data-ttu-id="4103e-104">在任何真實世界的案例中，保護應用程式和服務是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="4103e-104">In any real-world scenario, securing applications and services are essential.</span></span> <span data-ttu-id="4103e-105">安全性涵蓋三個主要領域：</span><span class="sxs-lookup"><span data-stu-id="4103e-105">Security covers three key areas:</span></span>

* <span data-ttu-id="4103e-106">加密網路流量，以防止惡意駭客攔截它。</span><span class="sxs-lookup"><span data-stu-id="4103e-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="4103e-107">驗證用戶端和伺服器以建立身分識別與信任。</span><span class="sxs-lookup"><span data-stu-id="4103e-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="4103e-108">授權用戶端控制對系統的存取，並根據身分識別套用許可權。</span><span class="sxs-lookup"><span data-stu-id="4103e-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="4103e-109">*驗證* 與建立用戶端或伺服器的身分識別相關。</span><span class="sxs-lookup"><span data-stu-id="4103e-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="4103e-110">*授權* 與判斷用戶端是否有權存取資源或發出命令相關。</span><span class="sxs-lookup"><span data-stu-id="4103e-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="4103e-111">本章將涵蓋 gRPC 中的驗證和授權功能，以進行 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="4103e-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="4103e-112">它也會透過 TLS 加密連線來討論網路安全性。</span><span class="sxs-lookup"><span data-stu-id="4103e-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="4103e-113">WCF 驗證與授權</span><span class="sxs-lookup"><span data-stu-id="4103e-113">WCF authentication and authorization</span></span>

<span data-ttu-id="4103e-114">在 Windows Communication Foundation (WCF) ，驗證和授權是以不同的方式處理，視所使用的傳輸和系結而定。</span><span class="sxs-lookup"><span data-stu-id="4103e-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="4103e-115">WCF 支援各種 WS- \* 安全性標準。</span><span class="sxs-lookup"><span data-stu-id="4103e-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="4103e-116">它也支援在 IIS 中執行的 HTTP 服務，或在 Windows 系統之間 NetTCP 服務的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4103e-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="4103e-117">gRPC 驗證和授權</span><span class="sxs-lookup"><span data-stu-id="4103e-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="4103e-118">gRPC authentication 和授權適用于兩個層級：</span><span class="sxs-lookup"><span data-stu-id="4103e-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="4103e-119">呼叫層級驗證/授權通常會透過在進行呼叫時套用於中繼資料的權杖來處理。</span><span class="sxs-lookup"><span data-stu-id="4103e-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="4103e-120">通道層級驗證會使用在連接層級套用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4103e-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="4103e-121">它也可以包含要套用至通道上每次呼叫的呼叫層級驗證/授權認證。</span><span class="sxs-lookup"><span data-stu-id="4103e-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="4103e-122">您可以使用其中一種或兩種機制來協助保護您的服務。</span><span class="sxs-lookup"><span data-stu-id="4103e-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="4103e-123">GRPC 的 ASP.NET Core 執行透過大部分標準 ASP.NET Core 機制來支援驗證和授權：</span><span class="sxs-lookup"><span data-stu-id="4103e-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="4103e-124">呼叫驗證</span><span class="sxs-lookup"><span data-stu-id="4103e-124">Call authentication</span></span>
  - <span data-ttu-id="4103e-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4103e-125">Azure Active Directory</span></span>
  - <span data-ttu-id="4103e-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="4103e-126">IdentityServer</span></span>
  - <span data-ttu-id="4103e-127">JWT 持有人權杖</span><span class="sxs-lookup"><span data-stu-id="4103e-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="4103e-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="4103e-128">OAuth 2.0</span></span>
  - <span data-ttu-id="4103e-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="4103e-129">OpenID Connect</span></span>
  - <span data-ttu-id="4103e-130">WS-同盟</span><span class="sxs-lookup"><span data-stu-id="4103e-130">WS-Federation</span></span>
- <span data-ttu-id="4103e-131">通道驗證</span><span class="sxs-lookup"><span data-stu-id="4103e-131">Channel authentication</span></span>
  - <span data-ttu-id="4103e-132">用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="4103e-132">Client certificate</span></span>

<span data-ttu-id="4103e-133">呼叫驗證方法都是以 *權杖* 為基礎。</span><span class="sxs-lookup"><span data-stu-id="4103e-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="4103e-134">唯一的差別在於權杖的產生方式，以及用來驗證 ASP.NET Core 服務中權杖的程式庫。</span><span class="sxs-lookup"><span data-stu-id="4103e-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="4103e-135">如需詳細資訊，請參閱 [驗證和授權](/aspnet/core/grpc/authn-and-authz) 文章。</span><span class="sxs-lookup"><span data-stu-id="4103e-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="4103e-136">當您透過 TLS 加密的 HTTP/2 連線使用 gRPC 時，用戶端與伺服器之間的所有流量都會加密，即使您未使用通道層級驗證也一樣。</span><span class="sxs-lookup"><span data-stu-id="4103e-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="4103e-137">本章將說明如何將通話認證和通道認證套用至 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="4103e-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="4103e-138">它也會示範如何使用來自 .NET gRPC 用戶端的認證來向服務進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4103e-138">It will also show how to use credentials from a .NET gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4103e-139">[上一個](client-libraries.md) 
>[下一步](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="4103e-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
