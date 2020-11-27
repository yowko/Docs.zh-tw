---
title: 竄改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249796"
---
# <a name="tampering"></a><span data-ttu-id="38761-102">竄改</span><span class="sxs-lookup"><span data-stu-id="38761-102">Tampering</span></span>

<span data-ttu-id="38761-103">*篡改* 是指改變訊息、傳送訊息，以及使用改變的訊息，而不是它所用的用途。</span><span class="sxs-lookup"><span data-stu-id="38761-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="38761-104">請勿停用 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="38761-104">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="38761-105">WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="38761-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="38761-106">您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。</span><span class="sxs-lookup"><span data-stu-id="38761-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="38761-107">當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="38761-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="38761-108">如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。</span><span class="sxs-lookup"><span data-stu-id="38761-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="38761-109">為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="38761-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38761-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38761-110">See also</span></span>

- [<span data-ttu-id="38761-111">安全性考量</span><span class="sxs-lookup"><span data-stu-id="38761-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="38761-112">洩露資訊</span><span class="sxs-lookup"><span data-stu-id="38761-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="38761-113">提高權限</span><span class="sxs-lookup"><span data-stu-id="38761-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="38761-114">拒絕服務</span><span class="sxs-lookup"><span data-stu-id="38761-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="38761-115">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="38761-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="38761-116">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="38761-116">Replay Attacks</span></span>](replay-attacks.md)
