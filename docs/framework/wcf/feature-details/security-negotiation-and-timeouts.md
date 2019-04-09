---
title: 安全性交涉與逾時
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180636"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="7c02f-102">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="7c02f-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="7c02f-103">當用戶端和服務驗證時，Windows Communication Foundation (WCF) 支援驗證過程中交涉服務認證的其中一個模式。</span><span class="sxs-lookup"><span data-stu-id="7c02f-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="7c02f-104">在這類案例中，用戶端和伺服器之間可能會進行 multi-leg 交換，以便將服務認證傳播至用戶端。</span><span class="sxs-lookup"><span data-stu-id="7c02f-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="7c02f-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 屬性會控制完成 multi-leg 交換所需要的時間。</span><span class="sxs-lookup"><span data-stu-id="7c02f-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="7c02f-106">不過，只有在交換所花費的實際時間超過單一要求-回應的時間時，這個逾時情況才適用。</span><span class="sxs-lookup"><span data-stu-id="7c02f-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="7c02f-107">如果在單一來回行程中完成交涉，逾時就不適用。</span><span class="sxs-lookup"><span data-stu-id="7c02f-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c02f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c02f-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="7c02f-109">HOW TO：設定最大時鐘誤差</span><span class="sxs-lookup"><span data-stu-id="7c02f-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
