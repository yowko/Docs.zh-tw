---
title: 安全對話與安全工作階段
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: 13
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 502064ce30f6e117168834643a116d3983811fb8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="secure-conversations-and-secure-sessions"></a><span data-ttu-id="49fd2-102">安全對話與安全工作階段</span><span class="sxs-lookup"><span data-stu-id="49fd2-102">Secure Conversations and Secure Sessions</span></span>
<span data-ttu-id="49fd2-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的其中一個特點是在兩個端點之間建立安全工作階段的能力，端點會互相驗證並同意加密與數位簽章程序。</span><span class="sxs-lookup"><span data-stu-id="49fd2-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to establish secure sessions between two endpoints that authenticate each other and agree upon an encryption and digital signature process.</span></span> <span data-ttu-id="49fd2-104">例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="49fd2-104">For example, the service endpoint might require a client endpoint to send a security token based upon an X.509 certificate for authentication.</span></span> <span data-ttu-id="49fd2-105">一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。</span><span class="sxs-lookup"><span data-stu-id="49fd2-105">Once the client is authenticated, the service endpoint returns a security context token (SCT) back to the client that is then used to secure all subsequent messages within the session.</span></span> <span data-ttu-id="49fd2-106">由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。</span><span class="sxs-lookup"><span data-stu-id="49fd2-106">Establishing this secure session enables the set of messages that are exchanged between the two endpoints to be more efficient, because the SCT has a symmetric key.</span></span> <span data-ttu-id="49fd2-107">非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。</span><span class="sxs-lookup"><span data-stu-id="49fd2-107">Asymmetric keys, which X.509 certificates are based upon, require significantly more computational power than symmetric keys when generating a digital signature or encrypting a set of data.</span></span>  
  
 <span data-ttu-id="49fd2-108">啟動程序的原則 (定義於區段 6.2.7 [Ws-securitypolicy](http://go.microsoft.com/fwlink/?LinkId=99817)標準) 包含用來保護通道以及驗證用戶端，則 RST/SCT 和 RSTR/SCT 交換的訊息安全性判斷提示。</span><span class="sxs-lookup"><span data-stu-id="49fd2-108">The bootstrap policy (defined in section 6.2.7 of the [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contains the message security assertions used to secure the channel and authenticate the client prior to the RST/SCT and RSTR/SCT exchange.</span></span> <span data-ttu-id="49fd2-109">某些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 標準繫結的 `Security.Message.EstablishSecurityContext` 屬性可控制是否使用安全對話。</span><span class="sxs-lookup"><span data-stu-id="49fd2-109">Certain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard bindings have a `Security.Message.EstablishSecurityContext` property which controls whether secure conversation is used.</span></span> <span data-ttu-id="49fd2-110">使用自訂繫結時啟動安裝程式會以巢狀安全性繫結項目，透過[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)組態檔中，或藉由呼叫<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>程式碼中。</span><span class="sxs-lookup"><span data-stu-id="49fd2-110">When using custom bindings the bootstrap is indicated by nesting security binding elements, either through [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) in the configuration file, or by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> in code.</span></span>  
  
 <span data-ttu-id="49fd2-111">如需工作階段的詳細資訊，請參閱[Sessions<](../../../../docs/framework/wcf/using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="49fd2-111">For more information about sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49fd2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49fd2-112">See Also</span></span>  
 [<span data-ttu-id="49fd2-113">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="49fd2-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="49fd2-114">如何：建立需要工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="49fd2-114">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
