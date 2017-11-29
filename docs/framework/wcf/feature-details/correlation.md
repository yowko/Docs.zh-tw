---
title: "相互關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d15609db250e4743ae2a7a1b6c3c355600704f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="correlation"></a><span data-ttu-id="dfc47-102">相互關聯</span><span class="sxs-lookup"><span data-stu-id="dfc47-102">Correlation</span></span>
<span data-ttu-id="dfc47-103">當工作流程服務應用程式與其他服務通訊時，將其中的訊息分派至正確的工作流程執行個體是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="dfc47-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="dfc47-104">相互關聯可提供此操作的機制。</span><span class="sxs-lookup"><span data-stu-id="dfc47-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="dfc47-105">本節中的主題提供相互關聯的概要以及說明如何在不同的工作流程服務案例中加以使用。</span><span class="sxs-lookup"><span data-stu-id="dfc47-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dfc47-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="dfc47-106">In This Section</span></span>  
 [<span data-ttu-id="dfc47-107">相互關聯概觀</span><span class="sxs-lookup"><span data-stu-id="dfc47-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="dfc47-108">提供適用於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的相互關聯類型概要。</span><span class="sxs-lookup"><span data-stu-id="dfc47-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="dfc47-109">內容交換</span><span class="sxs-lookup"><span data-stu-id="dfc47-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="dfc47-110">說明內容交換相互關聯。</span><span class="sxs-lookup"><span data-stu-id="dfc47-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="dfc47-111">永久性雙工</span><span class="sxs-lookup"><span data-stu-id="dfc47-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="dfc47-112">說明永久性雙面相互關聯。</span><span class="sxs-lookup"><span data-stu-id="dfc47-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="dfc47-113">基礎的內容</span><span class="sxs-lookup"><span data-stu-id="dfc47-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="dfc47-114">說明以內容為基礎的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="dfc47-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="dfc47-115">要求-回覆</span><span class="sxs-lookup"><span data-stu-id="dfc47-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="dfc47-116">說明要求-回覆相互關聯。</span><span class="sxs-lookup"><span data-stu-id="dfc47-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="dfc47-117">疑難排解相互關聯</span><span class="sxs-lookup"><span data-stu-id="dfc47-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="dfc47-118">提供疑難排解相互關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="dfc47-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc47-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc47-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="dfc47-120">以內容為基礎的相互關聯</span><span class="sxs-lookup"><span data-stu-id="dfc47-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="dfc47-121">相互關聯計算機</span><span class="sxs-lookup"><span data-stu-id="dfc47-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
