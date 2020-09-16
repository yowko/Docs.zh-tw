---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 713737b129771967958fddf44e9ef28583d49422
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554074"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="2becf-102">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2becf-102">Securing Services and Clients</span></span>
<span data-ttu-id="2becf-103">本節中的資訊著重于 Windows Communication Foundation (WCF) 的程式設計安全性。</span><span class="sxs-lookup"><span data-stu-id="2becf-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2becf-104">一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="2becf-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="2becf-105">這些技術涵蓋大部分案例的大部分使用者安全性需求，如 [常見的安全性案例](common-security-scenarios.md)所示。</span><span class="sxs-lookup"><span data-stu-id="2becf-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="2becf-106">如果您的案例需要更多的功能，請先參閱 [自訂系結的安全性功能](security-capabilities-with-custom-bindings.md);如果解決方案並不明顯，請參閱 [擴充安全性](../extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2becf-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="2becf-107">如果您要建立 (或與使用豐富宣告的系統) 交互操作，請參閱 [授權](authorization-in-wcf.md)中的主題。</span><span class="sxs-lookup"><span data-stu-id="2becf-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2becf-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="2becf-108">In This Section</span></span>  
 [<span data-ttu-id="2becf-109">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="2becf-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="2becf-110">用於確保訊息安全的程式設計模型概觀。</span><span class="sxs-lookup"><span data-stu-id="2becf-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="2becf-111">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="2becf-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="2becf-112">如何透過傳輸層確保訊息安全的概觀。</span><span class="sxs-lookup"><span data-stu-id="2becf-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="2becf-113">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="2becf-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="2becf-114">摘要說明在 Windows Communication Foundation (WCF) 中使用訊息層級安全性的原因。</span><span class="sxs-lookup"><span data-stu-id="2becf-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="2becf-115">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="2becf-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="2becf-116">保護 WCF 會話安全時所需考慮的討論。</span><span class="sxs-lookup"><span data-stu-id="2becf-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="2becf-117">使用憑證</span><span class="sxs-lookup"><span data-stu-id="2becf-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="2becf-118">使用 X.509 憑證時，所需之部分常見工作的說明。</span><span class="sxs-lookup"><span data-stu-id="2becf-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2becf-119">參考</span><span class="sxs-lookup"><span data-stu-id="2becf-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="2becf-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="2becf-120">Related Sections</span></span>  
 [<span data-ttu-id="2becf-121">安全性概念</span><span class="sxs-lookup"><span data-stu-id="2becf-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="2becf-122">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="2becf-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="2becf-123">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="2becf-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="2becf-124">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="2becf-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="2becf-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="2becf-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="2becf-126">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="2becf-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="2becf-127">授權</span><span class="sxs-lookup"><span data-stu-id="2becf-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="2becf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2becf-128">See also</span></span>

- [<span data-ttu-id="2becf-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="2becf-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="2becf-130">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2becf-130">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
