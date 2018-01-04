---
title: "確保服務與用戶端的安全"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 52e07a83f5a1b84abc46f00e6fd6e80e4b9a2622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="b8689-102">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b8689-102">Securing Services and Clients</span></span>
<span data-ttu-id="b8689-103">本節所涵蓋的資訊將著重於 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的程式設計安全性。</span><span class="sxs-lookup"><span data-stu-id="b8689-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="b8689-104">一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="b8689-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="b8689-105">這些技術涵蓋大部分情況下，大部分使用者的安全性需求，如中所示[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="b8689-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="b8689-106">如果您的案例需要更多的功能，第一次看到[自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); 如果方案不會出現，請參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="b8689-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="b8689-107">如果您正在建立 （或與互通） 使用系統，提供豐富的宣告，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="b8689-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8689-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="b8689-108">In This Section</span></span>  
 [<span data-ttu-id="b8689-109">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="b8689-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="b8689-110">用於確保訊息安全的程式設計模型概觀。</span><span class="sxs-lookup"><span data-stu-id="b8689-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="b8689-111">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="b8689-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="b8689-112">如何透過傳輸層確保訊息安全的概觀。</span><span class="sxs-lookup"><span data-stu-id="b8689-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="b8689-113">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="b8689-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="b8689-114">摘要出在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中使用訊息層級安全性的原因。</span><span class="sxs-lookup"><span data-stu-id="b8689-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="b8689-115">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="b8689-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="b8689-116">確保 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作階段安全時，需要的考量事項討論。</span><span class="sxs-lookup"><span data-stu-id="b8689-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="b8689-117">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b8689-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="b8689-118">使用 X.509 憑證時，所需之部分常見工作的說明。</span><span class="sxs-lookup"><span data-stu-id="b8689-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b8689-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="b8689-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="b8689-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="b8689-120">Related Sections</span></span>  
 [<span data-ttu-id="b8689-121">安全性概念</span><span class="sxs-lookup"><span data-stu-id="b8689-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="b8689-122">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="b8689-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="b8689-123">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="b8689-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="b8689-124">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="b8689-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="b8689-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="b8689-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="b8689-126">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="b8689-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="b8689-127">授權</span><span class="sxs-lookup"><span data-stu-id="b8689-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8689-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8689-128">See Also</span></span>  
 [<span data-ttu-id="b8689-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="b8689-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="b8689-130">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="b8689-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
