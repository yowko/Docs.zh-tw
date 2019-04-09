---
title: 重新執行攻擊
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: fefcb533cedb5405736ecda70c6879ebe00b8b49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186754"
---
# <a name="replay-attacks"></a><span data-ttu-id="58e6a-102">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="58e6a-102">Replay Attacks</span></span>
<span data-ttu-id="58e6a-103">A*重新執行攻擊*攻擊者複製兩方之間的訊息資料流，並重新執行一個或多個合作對象的資料流時，就會發生。</span><span class="sxs-lookup"><span data-stu-id="58e6a-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="58e6a-104">除非緩解攻擊，否則受到攻擊的電腦會將資料流當成合法訊息來處理，導致發生一連串負面的影響，例如項目的重複排序。</span><span class="sxs-lookup"><span data-stu-id="58e6a-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="58e6a-105">繫結可能受制於反映攻擊</span><span class="sxs-lookup"><span data-stu-id="58e6a-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="58e6a-106">*反映攻擊*會重新執行的訊息傳回給寄件者，如同它們是來自接收者的回覆一樣。</span><span class="sxs-lookup"><span data-stu-id="58e6a-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="58e6a-107">標準*重新執行偵測*在 Windows Communication Foundation (WCF) 機制不會自動處理這。</span><span class="sxs-lookup"><span data-stu-id="58e6a-107">The standard *replay detection* in the Windows Communication Foundation (WCF) mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="58e6a-108">反映攻擊的緩解預設情況下，因為 WCF 服務模型會將要求訊息中的已簽署的訊息識別碼，並預期在帶正負號`relates-to`回應訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="58e6a-108">Reflection attacks are mitigated by default because the WCF service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="58e6a-109">如此一來，要求訊息便無法當成回應來重新執行。</span><span class="sxs-lookup"><span data-stu-id="58e6a-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="58e6a-110">在安全訊息 (RM) 案例中，反映攻擊的緩解原因為：</span><span class="sxs-lookup"><span data-stu-id="58e6a-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
-   <span data-ttu-id="58e6a-111">建立順序與建立順序回應訊息結構描述是不一樣的。</span><span class="sxs-lookup"><span data-stu-id="58e6a-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
-   <span data-ttu-id="58e6a-112">在 Simplex 順序中，用戶端所傳送的順序訊息無法返回重新執行，因為用戶端無法理解此類訊息。</span><span class="sxs-lookup"><span data-stu-id="58e6a-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
-   <span data-ttu-id="58e6a-113">在雙工順序中，兩個順序識別碼必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="58e6a-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="58e6a-114">因此，傳出的順序訊息無法返回當成傳入順序訊息來重新執行 (所有的順序標頭與本文都會一併簽署)。</span><span class="sxs-lookup"><span data-stu-id="58e6a-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="58e6a-115">唯一會受到反映攻擊影響的繫結就是不含 WS-Addressing 的繫結：已經停用 WS-Addressing 並使用對稱式金鑰安全性的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="58e6a-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="58e6a-116"><xref:System.ServiceModel.BasicHttpBinding> 依預設不會使用 WS-Addressing，但是它在使用對稱式金鑰安全性時，不會讓本身受到此攻擊的影響。</span><span class="sxs-lookup"><span data-stu-id="58e6a-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="58e6a-117">自訂繫結的緩解作業不是要建立安全性內容或是要求 WS-Addressing 標頭。</span><span class="sxs-lookup"><span data-stu-id="58e6a-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="58e6a-118">Web 伺服陣列：攻擊者重新執行要求到多個節點</span><span class="sxs-lookup"><span data-stu-id="58e6a-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="58e6a-119">用戶端會使用已在 Web 伺服陣列上實作的服務。</span><span class="sxs-lookup"><span data-stu-id="58e6a-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="58e6a-120">攻擊者會針對伺服陣列中另一個節點重新執行已經傳送至某個伺服陣列節點的要求。</span><span class="sxs-lookup"><span data-stu-id="58e6a-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="58e6a-121">此外，如果服務重新啟動，則會清除重新執行快取，讓攻擊者重新執行要求</span><span class="sxs-lookup"><span data-stu-id="58e6a-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="58e6a-122">(快取中包含已使用、先前看到的訊息簽章值並避免重新執行，以讓簽章只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="58e6a-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="58e6a-123">Web 伺服陣列不會共用重新執行快取)。</span><span class="sxs-lookup"><span data-stu-id="58e6a-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="58e6a-124">風險降低的方式包括：</span><span class="sxs-lookup"><span data-stu-id="58e6a-124">Mitigations include:</span></span>  
  
-   <span data-ttu-id="58e6a-125">使用訊息模式安全性搭配具狀態的安全性內容權杖 (包含或不包含啟用的安全對話)。</span><span class="sxs-lookup"><span data-stu-id="58e6a-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> <span data-ttu-id="58e6a-126">如需詳細資訊，請參閱[如何：建立安全性內容權杖的安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="58e6a-126">For more information, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
-   <span data-ttu-id="58e6a-127">設定服務使用傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="58e6a-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e6a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58e6a-128">See also</span></span>

- [<span data-ttu-id="58e6a-129">安全性考量</span><span class="sxs-lookup"><span data-stu-id="58e6a-129">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="58e6a-130">資訊洩露</span><span class="sxs-lookup"><span data-stu-id="58e6a-130">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="58e6a-131">權限提高</span><span class="sxs-lookup"><span data-stu-id="58e6a-131">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="58e6a-132">阻斷服務</span><span class="sxs-lookup"><span data-stu-id="58e6a-132">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="58e6a-133">竄改</span><span class="sxs-lookup"><span data-stu-id="58e6a-133">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)
- [<span data-ttu-id="58e6a-134">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="58e6a-134">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
