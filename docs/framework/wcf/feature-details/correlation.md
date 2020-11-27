---
title: 相互關聯
ms.date: 03/30/2017
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
ms.openlocfilehash: 1a357dd9469d7428af56772d3241e59766429990
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286769"
---
# <a name="correlation"></a><span data-ttu-id="8ab5f-102">相互關聯</span><span class="sxs-lookup"><span data-stu-id="8ab5f-102">Correlation</span></span>

<span data-ttu-id="8ab5f-103">當工作流程服務應用程式與其他服務通訊時，將其中的訊息分派至正確的工作流程執行個體是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="8ab5f-104">相互關聯可提供此操作的機制。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="8ab5f-105">本節中的主題提供相互關聯的概要以及說明如何在不同的工作流程服務案例中加以使用。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ab5f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="8ab5f-106">In This Section</span></span>  

 [<span data-ttu-id="8ab5f-107">相互關聯概觀</span><span class="sxs-lookup"><span data-stu-id="8ab5f-107">Correlation Overview</span></span>](correlation-overview.md)  
 <span data-ttu-id="8ab5f-108">提供適用於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的相互關聯類型概要。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="8ab5f-109">永久性雙工</span><span class="sxs-lookup"><span data-stu-id="8ab5f-109">Durable Duplex</span></span>](durable-duplex-correlation.md)  
 <span data-ttu-id="8ab5f-110">說明永久性雙面相互關聯。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-110">Describes durable duplex correlation.</span></span>
  
 [<span data-ttu-id="8ab5f-111">要求-回覆</span><span class="sxs-lookup"><span data-stu-id="8ab5f-111">Request-Reply</span></span>](request-reply-correlation.md)  
 <span data-ttu-id="8ab5f-112">說明要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-112">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="8ab5f-113">疑難排解相互關聯</span><span class="sxs-lookup"><span data-stu-id="8ab5f-113">Troubleshooting Correlation</span></span>](troubleshooting-correlation.md)  
 <span data-ttu-id="8ab5f-114">提供疑難排解相互關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="8ab5f-114">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab5f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ab5f-115">See also</span></span>

- <xref:System.ServiceModel.Activities.CorrelationHandle>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.Receive>
- <xref:System.ServiceModel.CorrelationQuery>
