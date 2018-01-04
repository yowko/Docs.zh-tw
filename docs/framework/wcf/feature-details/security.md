---
title: "Windows Communication Foundation 安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f2314c8def27bac9e64685d2af3cdd7639332f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="19df0-102">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="19df0-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="19df0-103">本節中的各個主題將說明 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性功能，以及如何使用這些功能來協助保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="19df0-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="19df0-104">Windows Server AppFabric 和安全性，請參閱[安全性模型的 Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="19df0-104"> Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19df0-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="19df0-105">In This Section</span></span>  
 [<span data-ttu-id="19df0-106">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="19df0-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="19df0-107">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="19df0-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="19df0-108">安全性概念</span><span class="sxs-lookup"><span data-stu-id="19df0-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="19df0-109">說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性中使用的基本用語與概念。</span><span class="sxs-lookup"><span data-stu-id="19df0-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="19df0-110">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="19df0-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="19df0-111">說明您可以透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 進行設定的各種案例與拓撲。</span><span class="sxs-lookup"><span data-stu-id="19df0-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="19df0-112">安全性行為</span><span class="sxs-lookup"><span data-stu-id="19df0-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="19df0-113">提供影響安全性 (例如設定認證) 之 WCF 行為的概觀。</span><span class="sxs-lookup"><span data-stu-id="19df0-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="19df0-114">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="19df0-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="19df0-115">安全性導向的繫結檢視，包括示範如何建立自訂安全性繫結的各個主題。</span><span class="sxs-lookup"><span data-stu-id="19df0-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="19df0-116">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="19df0-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="19df0-117">說明如何透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 安全性功能來保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="19df0-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="19df0-118">驗證</span><span class="sxs-lookup"><span data-stu-id="19df0-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="19df0-119">示範一般驗證工作。</span><span class="sxs-lookup"><span data-stu-id="19df0-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="19df0-120">授權</span><span class="sxs-lookup"><span data-stu-id="19df0-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="19df0-121">說明使用安全性實作的一般授權案例。</span><span class="sxs-lookup"><span data-stu-id="19df0-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="19df0-122">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="19df0-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="19df0-123">說明聯合的基本概念，以及如何建立可與聯合伺服器通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="19df0-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="19df0-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="19df0-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="19df0-125">說明如何執行部分信任的案例，以及在部分信任狀態下執行時，有哪些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 限制。</span><span class="sxs-lookup"><span data-stu-id="19df0-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="19df0-126">稽核</span><span class="sxs-lookup"><span data-stu-id="19df0-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="19df0-127">說明如何稽核安全性事件。</span><span class="sxs-lookup"><span data-stu-id="19df0-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="19df0-128">安全性指引和最佳做法</span><span class="sxs-lookup"><span data-stu-id="19df0-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="19df0-129">建立安全 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的方針。</span><span class="sxs-lookup"><span data-stu-id="19df0-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19df0-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="19df0-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="19df0-131">相關章節</span><span class="sxs-lookup"><span data-stu-id="19df0-131">Related Sections</span></span>  
 [<span data-ttu-id="19df0-132">WCF 功能詳細資料</span><span class="sxs-lookup"><span data-stu-id="19df0-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="19df0-133">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="19df0-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="19df0-134">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="19df0-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="19df0-135">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="19df0-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="19df0-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="19df0-136">See Also</span></span>  
 [<span data-ttu-id="19df0-137">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="19df0-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
