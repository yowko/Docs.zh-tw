---
title: 安全工作階段
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590081"
---
# <a name="secure-sessions"></a><span data-ttu-id="7781c-102">安全工作階段</span><span class="sxs-lookup"><span data-stu-id="7781c-102">Secure Sessions</span></span>
<span data-ttu-id="7781c-103">Windows Communication Foundation （WCF）的一項功能是可靠會話，可確保以傳送的順序接收訊息。</span><span class="sxs-lookup"><span data-stu-id="7781c-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="7781c-104">本節中的主題將就建立可靠工作階段時要考量的安全性影響提供說明。</span><span class="sxs-lookup"><span data-stu-id="7781c-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="7781c-105">如需可靠會話的詳細資訊，請參閱[使用會話](../using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="7781c-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7781c-106">當 Windows XP 需要模擬時，請使用不包含具狀態之安全性內容權杖 (SCT) 的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="7781c-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="7781c-107">當可設定狀態的 SCT 與模擬一起使用時，就會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="7781c-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="7781c-108">如需詳細資訊，請參閱[不支援的案例](unsupported-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="7781c-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7781c-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="7781c-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="7781c-110">安全對話與安全工作階段</span><span class="sxs-lookup"><span data-stu-id="7781c-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="7781c-111">安全對話與安全工作階段都是一樣的意思。</span><span class="sxs-lookup"><span data-stu-id="7781c-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="7781c-112">本主題將說明安全對話的運作方式，以及此模式的使用時機與原因。</span><span class="sxs-lookup"><span data-stu-id="7781c-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="7781c-113">如何：建立安全工作階段</span><span class="sxs-lookup"><span data-stu-id="7781c-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="7781c-114">逐步解說建立安全工作階段的基本概念。</span><span class="sxs-lookup"><span data-stu-id="7781c-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="7781c-115">HOW TO：為安全工作階段建立安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="7781c-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="7781c-116">逐步解說將維護用戶端狀態及工作階段之 Web 伺服陣列的各項建立步驟。</span><span class="sxs-lookup"><span data-stu-id="7781c-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="7781c-117">安全工作階段的安全性考量</span><span class="sxs-lookup"><span data-stu-id="7781c-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="7781c-118">描述安全工作階段的特殊考量。</span><span class="sxs-lookup"><span data-stu-id="7781c-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="7781c-119">參考</span><span class="sxs-lookup"><span data-stu-id="7781c-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="7781c-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="7781c-120">Related Sections</span></span>  
 [<span data-ttu-id="7781c-121">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="7781c-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="7781c-122">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="7781c-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7781c-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="7781c-123">See also</span></span>

- [<span data-ttu-id="7781c-124">HOW TO：啟用訊息重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="7781c-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="7781c-125">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="7781c-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="7781c-126">HOW TO：建立需要工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="7781c-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
