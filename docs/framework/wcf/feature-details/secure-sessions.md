---
title: 安全工作階段
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
ms.openlocfilehash: 09c261afb2c64a46fc1f4619c4ec6b2e87b3fbbf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070197"
---
# <a name="secure-sessions"></a><span data-ttu-id="908e1-102">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="908e1-102">Secure Sessions</span></span>
<span data-ttu-id="908e1-103">功能的 Windows Communication Foundation (WCF) 是確保傳送的順序接收訊息的可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="908e1-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="908e1-104">本節中的主題將就建立可靠工作階段時要考量的安全性影響提供說明。</span><span class="sxs-lookup"><span data-stu-id="908e1-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="908e1-105">如需可靠工作階段的詳細資訊，請參閱[使用工作階段的](../../../../docs/framework/wcf/using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="908e1-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="908e1-106">當 Windows XP 需要模擬時，請使用不包含具狀態之安全性內容權杖 (SCT) 的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="908e1-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="908e1-107">當可設定狀態的 SCT 與模擬一起使用時，就會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="908e1-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="908e1-108">如需詳細資訊，請參閱 <<c0> [ 不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="908e1-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="908e1-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="908e1-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="908e1-110">安全對話與安全工作階段</span><span class="sxs-lookup"><span data-stu-id="908e1-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="908e1-111">安全對話與安全工作階段都是一樣的意思。</span><span class="sxs-lookup"><span data-stu-id="908e1-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="908e1-112">本主題將說明安全對話的運作方式，以及此模式的使用時機與原因。</span><span class="sxs-lookup"><span data-stu-id="908e1-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="908e1-113">如何：建立安全工作階段</span><span class="sxs-lookup"><span data-stu-id="908e1-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="908e1-114">逐步解說建立安全工作階段的基本概念。</span><span class="sxs-lookup"><span data-stu-id="908e1-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="908e1-115">如何：為安全工作階段建立安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="908e1-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="908e1-116">逐步解說將維護用戶端狀態及工作階段之 Web 伺服陣列的各項建立步驟。</span><span class="sxs-lookup"><span data-stu-id="908e1-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="908e1-117">安全工作階段的安全性考量</span><span class="sxs-lookup"><span data-stu-id="908e1-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="908e1-118">描述安全工作階段的特殊考量。</span><span class="sxs-lookup"><span data-stu-id="908e1-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="908e1-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="908e1-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="908e1-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="908e1-120">Related Sections</span></span>  
 [<span data-ttu-id="908e1-121">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="908e1-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="908e1-122">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="908e1-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="908e1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="908e1-123">See Also</span></span>  
 [<span data-ttu-id="908e1-124">如何：啟用訊息偵測重送攻擊</span><span class="sxs-lookup"><span data-stu-id="908e1-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="908e1-125">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="908e1-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="908e1-126">如何：建立需要工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="908e1-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
