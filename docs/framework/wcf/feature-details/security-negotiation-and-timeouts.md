---
title: "安全性交涉與逾時"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6fbee18d31cb1774300c14587b0f7d973a4996ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="ad657-102">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="ad657-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="ad657-103">當用戶端和伺服器進行驗證時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 支援一種在驗證過程中交涉服務認證的模式。</span><span class="sxs-lookup"><span data-stu-id="ad657-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="ad657-104">在這類案例中，用戶端和伺服器之間可能會進行 multi-leg 交換，以便將服務認證傳播至用戶端。</span><span class="sxs-lookup"><span data-stu-id="ad657-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="ad657-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 屬性會控制完成 multi-leg 交換所需要的時間。</span><span class="sxs-lookup"><span data-stu-id="ad657-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="ad657-106">不過，只有在交換所花費的實際時間超過單一要求-回應的時間時，這個逾時情況才適用。</span><span class="sxs-lookup"><span data-stu-id="ad657-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="ad657-107">如果在單一來回行程中完成交涉，逾時就不適用。</span><span class="sxs-lookup"><span data-stu-id="ad657-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad657-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad657-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="ad657-109">如何：設定最大時鐘誤差</span><span class="sxs-lookup"><span data-stu-id="ad657-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
