---
title: "安全工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65a54c06efffb2e3167c77bd109a50a31b971add
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="secure-sessions"></a><span data-ttu-id="01221-102">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="01221-102">Secure Sessions</span></span>
<span data-ttu-id="01221-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 其中一項功能，就是保證按照訊息傳送時的順序來接收訊息的可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="01221-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="01221-104">本節中的主題將就建立可靠工作階段時要考量的安全性影響提供說明。</span><span class="sxs-lookup"><span data-stu-id="01221-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="01221-105">可靠工作階段，請參閱[Sessions<](../../../../docs/framework/wcf/using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="01221-105"> reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01221-106">當 Windows XP 需要模擬時，請使用不包含具狀態之安全性內容權杖 (SCT) 的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="01221-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="01221-107">當可設定狀態的 SCT 與模擬一起使用時，就會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="01221-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="01221-108">[不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="01221-108"> [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01221-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="01221-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="01221-110">安全對話與安全工作階段</span><span class="sxs-lookup"><span data-stu-id="01221-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="01221-111">安全對話與安全工作階段都是一樣的意思。</span><span class="sxs-lookup"><span data-stu-id="01221-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="01221-112">本主題將說明安全對話的運作方式，以及此模式的使用時機與原因。</span><span class="sxs-lookup"><span data-stu-id="01221-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="01221-113">如何：建立安全工作階段</span><span class="sxs-lookup"><span data-stu-id="01221-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="01221-114">逐步解說建立安全工作階段的基本概念。</span><span class="sxs-lookup"><span data-stu-id="01221-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="01221-115">如何：為安全工作階段建立安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="01221-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="01221-116">逐步解說將維護用戶端狀態及工作階段之 Web 伺服陣列的各項建立步驟。</span><span class="sxs-lookup"><span data-stu-id="01221-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="01221-117">安全工作階段的安全性考量</span><span class="sxs-lookup"><span data-stu-id="01221-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="01221-118">描述安全工作階段的特殊考量。</span><span class="sxs-lookup"><span data-stu-id="01221-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="01221-119">參考資料</span><span class="sxs-lookup"><span data-stu-id="01221-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="01221-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="01221-120">Related Sections</span></span>  
 [<span data-ttu-id="01221-121">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="01221-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="01221-122">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="01221-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="01221-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="01221-123">See Also</span></span>  
 [<span data-ttu-id="01221-124">如何：啟用訊息偵測重送攻擊</span><span class="sxs-lookup"><span data-stu-id="01221-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="01221-125">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="01221-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="01221-126">如何：建立需要工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="01221-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
