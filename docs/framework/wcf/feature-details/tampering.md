---
title: "竄改"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ee041de1a9e009ca68ecc8bba8bc2fa06ba6ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="tampering"></a><span data-ttu-id="d82cf-102">竄改</span><span class="sxs-lookup"><span data-stu-id="d82cf-102">Tampering</span></span>
<span data-ttu-id="d82cf-103">*竄改*會改變一則訊息或傳遞的訊息，並使用修改的訊息用於不它適用於的行為。</span><span class="sxs-lookup"><span data-stu-id="d82cf-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="d82cf-104">請勿停用 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="d82cf-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="d82cf-105">WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="d82cf-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="d82cf-106">您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。</span><span class="sxs-lookup"><span data-stu-id="d82cf-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="d82cf-107">當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="d82cf-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="d82cf-108">如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。</span><span class="sxs-lookup"><span data-stu-id="d82cf-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="d82cf-109">為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="d82cf-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82cf-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="d82cf-110">See Also</span></span>  
 [<span data-ttu-id="d82cf-111">安全性考量</span><span class="sxs-lookup"><span data-stu-id="d82cf-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="d82cf-112">資訊洩漏</span><span class="sxs-lookup"><span data-stu-id="d82cf-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="d82cf-113">權限提高</span><span class="sxs-lookup"><span data-stu-id="d82cf-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="d82cf-114">阻絕服務</span><span class="sxs-lookup"><span data-stu-id="d82cf-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="d82cf-115">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="d82cf-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="d82cf-116">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="d82cf-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
