---
title: Windows Communication Foundation 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 36a7943ec9a4bab361784b99c569dbf6c42f61e5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181399"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="86b1c-102">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="86b1c-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="86b1c-103">在本節中的主題會描述 Windows Communication Foundation (WCF) 安全性功能，以及如何使用它們來保護訊息。</span><span class="sxs-lookup"><span data-stu-id="86b1c-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="86b1c-104">如需有關 Windows Server AppFabric 和安全性的詳細資訊，請參閱[安全性模型的 Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="86b1c-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86b1c-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="86b1c-105">In This Section</span></span>  
 [<span data-ttu-id="86b1c-106">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="86b1c-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="86b1c-107">說明 WCF 中的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="86b1c-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="86b1c-108">安全性概念</span><span class="sxs-lookup"><span data-stu-id="86b1c-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="86b1c-109">描述基本術語與使用 WCF 安全性的概念。</span><span class="sxs-lookup"><span data-stu-id="86b1c-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="86b1c-110">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="86b1c-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="86b1c-111">描述各種案例與拓撲，您可以使用 WCF 設定。</span><span class="sxs-lookup"><span data-stu-id="86b1c-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="86b1c-112">安全性行為</span><span class="sxs-lookup"><span data-stu-id="86b1c-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="86b1c-113">提供影響安全性 (例如設定認證) 之 WCF 行為的概觀。</span><span class="sxs-lookup"><span data-stu-id="86b1c-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="86b1c-114">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="86b1c-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="86b1c-115">安全性導向的繫結檢視，包括示範如何建立自訂安全性繫結的各個主題。</span><span class="sxs-lookup"><span data-stu-id="86b1c-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="86b1c-116">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="86b1c-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="86b1c-117">說明如何保護使用 WCF 安全性功能的訊息。</span><span class="sxs-lookup"><span data-stu-id="86b1c-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="86b1c-118">驗證</span><span class="sxs-lookup"><span data-stu-id="86b1c-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="86b1c-119">示範一般驗證工作。</span><span class="sxs-lookup"><span data-stu-id="86b1c-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="86b1c-120">授權</span><span class="sxs-lookup"><span data-stu-id="86b1c-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="86b1c-121">說明使用安全性實作的一般授權案例。</span><span class="sxs-lookup"><span data-stu-id="86b1c-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="86b1c-122">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="86b1c-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="86b1c-123">說明聯合的基本概念，以及如何建立可與聯合伺服器通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="86b1c-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="86b1c-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="86b1c-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="86b1c-125">描述如何執行部分信任時，執行部分信任案例和 WCF 的限制。</span><span class="sxs-lookup"><span data-stu-id="86b1c-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="86b1c-126">稽核</span><span class="sxs-lookup"><span data-stu-id="86b1c-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="86b1c-127">說明如何稽核安全性事件。</span><span class="sxs-lookup"><span data-stu-id="86b1c-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="86b1c-128">安全性指引和最佳做法</span><span class="sxs-lookup"><span data-stu-id="86b1c-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="86b1c-129">建立安全的 WCF 應用程式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="86b1c-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="86b1c-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="86b1c-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="86b1c-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="86b1c-131">Related Sections</span></span>  
 [<span data-ttu-id="86b1c-132">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="86b1c-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="86b1c-133">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="86b1c-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="86b1c-134">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="86b1c-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="86b1c-135">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="86b1c-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="86b1c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b1c-136">See Also</span></span>  
 [<span data-ttu-id="86b1c-137">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="86b1c-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
