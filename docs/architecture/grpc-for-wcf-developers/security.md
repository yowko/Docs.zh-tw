---
title: gRPC 應用中的安全性 - 適用于 WCF 開發人員的 gRPC
description: gRPC 中的呼叫和通道身份驗證和授權的概述。
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147811"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="4d50c-103">gRPC 應用程式中的安全性</span><span class="sxs-lookup"><span data-stu-id="4d50c-103">Security in gRPC applications</span></span>

<span data-ttu-id="4d50c-104">在任何實際場景中，保護應用程式和服務都至關重要。</span><span class="sxs-lookup"><span data-stu-id="4d50c-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="4d50c-105">安全涵蓋三個關鍵領域：</span><span class="sxs-lookup"><span data-stu-id="4d50c-105">Security covers three key areas:</span></span>

* <span data-ttu-id="4d50c-106">加密網路流量，防止惡意駭客攔截網路流量。</span><span class="sxs-lookup"><span data-stu-id="4d50c-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="4d50c-107">驗證用戶端和伺服器以建立身份和信任。</span><span class="sxs-lookup"><span data-stu-id="4d50c-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="4d50c-108">授權用戶端控制對系統的訪問，並根據標識應用許可權。</span><span class="sxs-lookup"><span data-stu-id="4d50c-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="4d50c-109">*身份驗證*與建立用戶端或伺服器的標識有關。</span><span class="sxs-lookup"><span data-stu-id="4d50c-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="4d50c-110">*授權*涉及確定用戶端是否具有訪問資源或發出命令的許可權。</span><span class="sxs-lookup"><span data-stu-id="4d50c-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="4d50c-111">本章將介紹 gRPC 中用於ASP.NET核心的身份驗證和授權功能。</span><span class="sxs-lookup"><span data-stu-id="4d50c-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="4d50c-112">它還將討論通過 TLS 加密連接的網路安全。</span><span class="sxs-lookup"><span data-stu-id="4d50c-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="4d50c-113">WCF 身份驗證和授權</span><span class="sxs-lookup"><span data-stu-id="4d50c-113">WCF authentication and authorization</span></span>

<span data-ttu-id="4d50c-114">在 Windows 通信基礎 （WCF） 中，身份驗證和授權的處理方式不同，具體取決於所使用的傳輸和綁定。</span><span class="sxs-lookup"><span data-stu-id="4d50c-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="4d50c-115">WCF 支援各種\*WS-安全標準。</span><span class="sxs-lookup"><span data-stu-id="4d50c-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="4d50c-116">它還支援對在 IIS 中運行的 HTTP 服務或 Windows 系統之間的 NetTCP 服務進行 Windows 身份驗證。</span><span class="sxs-lookup"><span data-stu-id="4d50c-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="4d50c-117">gRPC 身份驗證和授權</span><span class="sxs-lookup"><span data-stu-id="4d50c-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="4d50c-118">gRPC 身份驗證和授權在兩個級別上工作：</span><span class="sxs-lookup"><span data-stu-id="4d50c-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="4d50c-119">調用級別的身份驗證/授權通常通過在進行調用時在中繼資料中應用的權杖進行處理。</span><span class="sxs-lookup"><span data-stu-id="4d50c-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="4d50c-120">通道級身份驗證使用在連接級別應用的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="4d50c-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="4d50c-121">它還可以包括呼叫級身份驗證/授權憑據，以便自動應用於通道上的每個呼叫。</span><span class="sxs-lookup"><span data-stu-id="4d50c-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="4d50c-122">您可以使用以下任一機制或兩種機制來説明保護服務。</span><span class="sxs-lookup"><span data-stu-id="4d50c-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="4d50c-123">gRPC ASP.NET核心實現通過大多數標準ASP.NET核心機制支援身份驗證和授權：</span><span class="sxs-lookup"><span data-stu-id="4d50c-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="4d50c-124">呼叫身份驗證</span><span class="sxs-lookup"><span data-stu-id="4d50c-124">Call authentication</span></span>
  - <span data-ttu-id="4d50c-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="4d50c-125">Azure Active Directory</span></span>
  - <span data-ttu-id="4d50c-126">標識伺服器</span><span class="sxs-lookup"><span data-stu-id="4d50c-126">IdentityServer</span></span>
  - <span data-ttu-id="4d50c-127">JWT 持票代幣</span><span class="sxs-lookup"><span data-stu-id="4d50c-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="4d50c-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="4d50c-128">OAuth 2.0</span></span>
  - <span data-ttu-id="4d50c-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="4d50c-129">OpenID Connect</span></span>
  - <span data-ttu-id="4d50c-130">WS-同盟</span><span class="sxs-lookup"><span data-stu-id="4d50c-130">WS-Federation</span></span>
- <span data-ttu-id="4d50c-131">通道身份驗證</span><span class="sxs-lookup"><span data-stu-id="4d50c-131">Channel authentication</span></span>
  - <span data-ttu-id="4d50c-132">用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="4d50c-132">Client certificate</span></span>

<span data-ttu-id="4d50c-133">調用身份驗證方法都基於*權杖*。</span><span class="sxs-lookup"><span data-stu-id="4d50c-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="4d50c-134">唯一的真正區別是權杖的生成方式以及用於驗證 ASP.NET Core 服務中的權杖的庫。</span><span class="sxs-lookup"><span data-stu-id="4d50c-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="4d50c-135">有關詳細資訊，請參閱[身份驗證和授權](/aspnet/core/grpc/authn-and-authz)一文。</span><span class="sxs-lookup"><span data-stu-id="4d50c-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="4d50c-136">當您通過 TLS 加密的 HTTP/2 連接使用 gRPC 時，用戶端和伺服器之間的所有流量都加密，即使您不使用通道級身份驗證也是如此。</span><span class="sxs-lookup"><span data-stu-id="4d50c-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="4d50c-137">本章將演示如何將呼叫憑據和通道憑據應用於 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="4d50c-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="4d50c-138">它還將演示如何使用 .NET Core gRPC 用戶端的憑據對服務進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="4d50c-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4d50c-139">[上一個](client-libraries.md)
>[下一個](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="4d50c-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
