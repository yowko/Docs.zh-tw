---
title: Windows Communication Foundation 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: b92f1ad8bb00e9df8daf55da4d7a808420d909cf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253995"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="64f1e-102">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="64f1e-102">Windows Communication Foundation Security</span></span>

<span data-ttu-id="64f1e-103">本節中的主題描述 Windows Communication Foundation (WCF) 安全性功能，以及如何使用這些功能來協助保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="64f1e-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="64f1e-104">如需 Windows Server AppFabric 和安全性的詳細資訊，請參閱 [Windows Server appfabric 的安全性模型。](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="64f1e-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64f1e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="64f1e-105">In This Section</span></span>  

 [<span data-ttu-id="64f1e-106">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="64f1e-106">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="64f1e-107">描述 WCF 中的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="64f1e-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="64f1e-108">安全性概念</span><span class="sxs-lookup"><span data-stu-id="64f1e-108">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="64f1e-109">描述 WCF 安全性中使用的基本術語和概念。</span><span class="sxs-lookup"><span data-stu-id="64f1e-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="64f1e-110">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="64f1e-110">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="64f1e-111">描述您可以使用 WCF 設定的案例和拓撲。</span><span class="sxs-lookup"><span data-stu-id="64f1e-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="64f1e-112">安全性行為</span><span class="sxs-lookup"><span data-stu-id="64f1e-112">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="64f1e-113">提供影響安全性 (例如設定認證) 之 WCF 行為的概觀。</span><span class="sxs-lookup"><span data-stu-id="64f1e-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="64f1e-114">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="64f1e-114">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="64f1e-115">安全性導向的繫結檢視，包括示範如何建立自訂安全性繫結的各個主題。</span><span class="sxs-lookup"><span data-stu-id="64f1e-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="64f1e-116">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="64f1e-116">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="64f1e-117">描述如何使用 WCF 安全性功能來保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="64f1e-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="64f1e-118">驗證</span><span class="sxs-lookup"><span data-stu-id="64f1e-118">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="64f1e-119">示範一般驗證工作。</span><span class="sxs-lookup"><span data-stu-id="64f1e-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="64f1e-120">授權</span><span class="sxs-lookup"><span data-stu-id="64f1e-120">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="64f1e-121">說明使用安全性實作的一般授權案例。</span><span class="sxs-lookup"><span data-stu-id="64f1e-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="64f1e-122">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="64f1e-122">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="64f1e-123">說明聯合的基本概念，以及如何建立可與聯合伺服器通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="64f1e-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="64f1e-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="64f1e-124">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="64f1e-125">描述如何在執行部分信任的情況下執行部分信任的案例和 WCF 限制。</span><span class="sxs-lookup"><span data-stu-id="64f1e-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="64f1e-126">稽核</span><span class="sxs-lookup"><span data-stu-id="64f1e-126">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="64f1e-127">說明如何稽核安全性事件。</span><span class="sxs-lookup"><span data-stu-id="64f1e-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="64f1e-128">安全性指引與最佳做法</span><span class="sxs-lookup"><span data-stu-id="64f1e-128">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="64f1e-129">建立安全 WCF 應用程式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="64f1e-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="64f1e-130">參考</span><span class="sxs-lookup"><span data-stu-id="64f1e-130">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="64f1e-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="64f1e-131">Related Sections</span></span>  

 [<span data-ttu-id="64f1e-132">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="64f1e-132">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="64f1e-133">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="64f1e-133">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="64f1e-134">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="64f1e-134">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="64f1e-135">概觀說明</span><span class="sxs-lookup"><span data-stu-id="64f1e-135">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="64f1e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64f1e-136">See also</span></span>

- [<span data-ttu-id="64f1e-137">設定您的應用程式</span><span class="sxs-lookup"><span data-stu-id="64f1e-137">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
