---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
ms.openlocfilehash: 111a0dd003b0427490b498f895a7e526bafb52b7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198226"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="46913-102">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="46913-102">Securing Services and Clients</span></span>
<span data-ttu-id="46913-103">在本節中的資訊，著重於程式設計 Windows Communication Foundation (WCF) 中的安全性。</span><span class="sxs-lookup"><span data-stu-id="46913-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="46913-104">一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="46913-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="46913-105">這些技術涵蓋了大部分的情況下，大多數使用者的安全性需求，如中所示[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="46913-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="46913-106">如果您的案例需要更多的功能，第一次看到[自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); 如果方案不明顯，請參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="46913-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="46913-107">如果您要建立 （或與交互操作） 的系統，使用豐富的宣告，請參閱中的主題[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="46913-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46913-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="46913-108">In This Section</span></span>  
 [<span data-ttu-id="46913-109">WCF 安全性程式設計</span><span class="sxs-lookup"><span data-stu-id="46913-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="46913-110">用於確保訊息安全的程式設計模型概觀。</span><span class="sxs-lookup"><span data-stu-id="46913-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="46913-111">傳輸安全性概觀</span><span class="sxs-lookup"><span data-stu-id="46913-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="46913-112">如何透過傳輸層確保訊息安全的概觀。</span><span class="sxs-lookup"><span data-stu-id="46913-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="46913-113">訊息安全性</span><span class="sxs-lookup"><span data-stu-id="46913-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="46913-114">摘要說明使用訊息層級安全性的 Windows Communication Foundation (WCF) 中的原因。</span><span class="sxs-lookup"><span data-stu-id="46913-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="46913-115">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="46913-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="46913-116">需要保護的 WCF 工作階段時的考量事項討論。</span><span class="sxs-lookup"><span data-stu-id="46913-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="46913-117">使用憑證</span><span class="sxs-lookup"><span data-stu-id="46913-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="46913-118">使用 X.509 憑證時，所需之部分常見工作的說明。</span><span class="sxs-lookup"><span data-stu-id="46913-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="46913-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="46913-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="46913-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="46913-120">Related Sections</span></span>  
 [<span data-ttu-id="46913-121">安全性概念</span><span class="sxs-lookup"><span data-stu-id="46913-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="46913-122">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="46913-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="46913-123">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="46913-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="46913-124">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="46913-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="46913-125">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="46913-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="46913-126">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="46913-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="46913-127">授權</span><span class="sxs-lookup"><span data-stu-id="46913-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="46913-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46913-128">See Also</span></span>  
 [<span data-ttu-id="46913-129">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="46913-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="46913-130">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="46913-130">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
