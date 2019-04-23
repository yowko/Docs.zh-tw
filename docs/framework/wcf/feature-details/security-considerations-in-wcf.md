---
title: WCF 的安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 16b3afe9540f3e2953311f602408fce5412be2eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112212"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="6dafa-102">WCF 的安全性考量</span><span class="sxs-lookup"><span data-stu-id="6dafa-102">Security Considerations in WCF</span></span>
<span data-ttu-id="6dafa-103">在本節中的主題列出各種安全性相關的項目設計的 Windows Communication Foundation (WCF) 應用程式時需要考量。</span><span class="sxs-lookup"><span data-stu-id="6dafa-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dafa-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="6dafa-104">In This Section</span></span>  
 [<span data-ttu-id="6dafa-105">資訊洩漏</span><span class="sxs-lookup"><span data-stu-id="6dafa-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="6dafa-106">討論資訊可能遭到洩漏或受到攻擊的各種方式，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="6dafa-107">權限提高</span><span class="sxs-lookup"><span data-stu-id="6dafa-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="6dafa-108">討論提供攻擊者超出初始所授與之使用權限的影響，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="6dafa-109">阻絕服務</span><span class="sxs-lookup"><span data-stu-id="6dafa-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="6dafa-110">討論系統無法適當處理訊息時可能發生的情況，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="6dafa-111">竄改</span><span class="sxs-lookup"><span data-stu-id="6dafa-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="6dafa-112">討論訊息的更改或傳遞，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="6dafa-113">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="6dafa-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="6dafa-114">討論當攻擊者複製兩方之間的訊息資料流，並且對其中一方或多方重新執行資料流時可能發生的情況，以及如何減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="6dafa-115">安全工作階段的安全性考量</span><span class="sxs-lookup"><span data-stu-id="6dafa-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="6dafa-116">討論在實作安全工作階段時會影響安全性的項目。</span><span class="sxs-lookup"><span data-stu-id="6dafa-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="6dafa-117">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="6dafa-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="6dafa-118">列出不支援特定的安全性方面，而且應避免或考量的各種狀況。</span><span class="sxs-lookup"><span data-stu-id="6dafa-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6dafa-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="6dafa-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="6dafa-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="6dafa-120">Related Sections</span></span>  
 [<span data-ttu-id="6dafa-121">安全性指引和最佳做法</span><span class="sxs-lookup"><span data-stu-id="6dafa-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="6dafa-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dafa-122">See also</span></span>

- [<span data-ttu-id="6dafa-123">安全性</span><span class="sxs-lookup"><span data-stu-id="6dafa-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
