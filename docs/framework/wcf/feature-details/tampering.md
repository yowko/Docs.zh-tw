---
title: 竄改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107883"
---
# <a name="tampering"></a><span data-ttu-id="8e17b-102">竄改</span><span class="sxs-lookup"><span data-stu-id="8e17b-102">Tampering</span></span>
<span data-ttu-id="8e17b-103">*竄改*是改變一則訊息或傳遞的訊息，以及用於不該適用於使用修改的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="8e17b-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="8e17b-104">請勿停用 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="8e17b-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="8e17b-105">WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="8e17b-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="8e17b-106">您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。</span><span class="sxs-lookup"><span data-stu-id="8e17b-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="8e17b-107">當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。</span><span class="sxs-lookup"><span data-stu-id="8e17b-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="8e17b-108">如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e17b-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="8e17b-109">為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e17b-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e17b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e17b-110">See also</span></span>

- [<span data-ttu-id="8e17b-111">安全性考量</span><span class="sxs-lookup"><span data-stu-id="8e17b-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="8e17b-112">資訊洩露</span><span class="sxs-lookup"><span data-stu-id="8e17b-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="8e17b-113">權限提高</span><span class="sxs-lookup"><span data-stu-id="8e17b-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="8e17b-114">阻斷服務</span><span class="sxs-lookup"><span data-stu-id="8e17b-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="8e17b-115">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="8e17b-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [<span data-ttu-id="8e17b-116">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="8e17b-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
