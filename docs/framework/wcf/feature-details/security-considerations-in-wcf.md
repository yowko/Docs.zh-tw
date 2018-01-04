---
title: "WCF 的安全性考量"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f35bd56bdc69f8c57a7e46984778051b57b7a06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="8af43-102">WCF 的安全性考量</span><span class="sxs-lookup"><span data-stu-id="8af43-102">Security Considerations in WCF</span></span>
<span data-ttu-id="8af43-103">本節中的主題列出在設計 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式時，要考量的各種安全性相關項目。</span><span class="sxs-lookup"><span data-stu-id="8af43-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8af43-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="8af43-104">In This Section</span></span>  
 [<span data-ttu-id="8af43-105">資訊洩漏</span><span class="sxs-lookup"><span data-stu-id="8af43-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="8af43-106">討論資訊可能遭到洩漏或受到攻擊的各種方式，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="8af43-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8af43-107">權限提高</span><span class="sxs-lookup"><span data-stu-id="8af43-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="8af43-108">討論提供攻擊者超出初始所授與之使用權限的影響，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="8af43-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8af43-109">阻絕服務</span><span class="sxs-lookup"><span data-stu-id="8af43-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="8af43-110">討論系統無法適當處理訊息時可能發生的情況，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="8af43-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8af43-111">竄改</span><span class="sxs-lookup"><span data-stu-id="8af43-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="8af43-112">討論訊息的更改或傳遞，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="8af43-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="8af43-113">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="8af43-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="8af43-114">討論當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時可能發生的情況，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="8af43-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="8af43-115">安全工作階段的安全性考量</span><span class="sxs-lookup"><span data-stu-id="8af43-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="8af43-116">討論在實作安全工作階段時會影響安全性的項目。</span><span class="sxs-lookup"><span data-stu-id="8af43-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="8af43-117">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="8af43-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="8af43-118">列出不支援特定的安全性方面，而且應避免或考量的各種狀況。</span><span class="sxs-lookup"><span data-stu-id="8af43-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8af43-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="8af43-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="8af43-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="8af43-120">Related Sections</span></span>  
 [<span data-ttu-id="8af43-121">安全性指引和最佳做法</span><span class="sxs-lookup"><span data-stu-id="8af43-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="8af43-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8af43-122">See Also</span></span>  
 [<span data-ttu-id="8af43-123">安全性</span><span class="sxs-lookup"><span data-stu-id="8af43-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
