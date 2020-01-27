---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746423"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="d4858-102">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d4858-102">Securing Services and Clients</span></span>
<span data-ttu-id="d4858-103">本節中的資訊著重于 Windows Communication Foundation （WCF）中的安全性程式設計。</span><span class="sxs-lookup"><span data-stu-id="d4858-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d4858-104">一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="d4858-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="d4858-105">這些技術涵蓋大部分使用者在大多數情況下的安全性需求，如常見的[安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)所示。</span><span class="sxs-lookup"><span data-stu-id="d4858-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="d4858-106">如果您的案例需要更多功能，請先參閱[具有自訂系結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md);如果解決方案不明顯，請參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d4858-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="d4858-107">如果您要建立（或交互操作）使用豐富宣告的系統，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)中的主題。</span><span class="sxs-lookup"><span data-stu-id="d4858-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4858-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d4858-108">In This Section</span></span>  
 [<span data-ttu-id="d4858-109">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="d4858-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="d4858-110">用於確保訊息安全的程式設計模型概觀。</span><span class="sxs-lookup"><span data-stu-id="d4858-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="d4858-111">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d4858-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="d4858-112">如何透過傳輸層確保訊息安全的概觀。</span><span class="sxs-lookup"><span data-stu-id="d4858-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="d4858-113">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="d4858-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="d4858-114">摘要說明在 Windows Communication Foundation （WCF）中使用訊息層級安全性的原因。</span><span class="sxs-lookup"><span data-stu-id="d4858-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="d4858-115">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="d4858-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="d4858-116">保護 WCF 會話時所需考慮的討論。</span><span class="sxs-lookup"><span data-stu-id="d4858-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="d4858-117">使用憑證</span><span class="sxs-lookup"><span data-stu-id="d4858-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="d4858-118">使用 X.509 憑證時，所需之部分常見工作的說明。</span><span class="sxs-lookup"><span data-stu-id="d4858-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d4858-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="d4858-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="d4858-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="d4858-120">Related Sections</span></span>  
 [<span data-ttu-id="d4858-121">安全性概念</span><span class="sxs-lookup"><span data-stu-id="d4858-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="d4858-122">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="d4858-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="d4858-123">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="d4858-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="d4858-124">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="d4858-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="d4858-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="d4858-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="d4858-126">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="d4858-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="d4858-127">授權</span><span class="sxs-lookup"><span data-stu-id="d4858-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="d4858-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4858-128">See also</span></span>

- [<span data-ttu-id="d4858-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="d4858-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="d4858-130">[Windows Server App Fabric 的安全性模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d4858-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
