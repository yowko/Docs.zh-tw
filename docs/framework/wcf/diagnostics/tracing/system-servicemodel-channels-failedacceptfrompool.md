---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df0f983d646ea89eeef338b9742843e9fa50487b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="3210b-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="3210b-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="3210b-103">嘗試重複使用共用連線失敗。</span><span class="sxs-lookup"><span data-stu-id="3210b-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="3210b-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="3210b-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3210b-105">描述</span><span class="sxs-lookup"><span data-stu-id="3210b-105">Description</span></span>  
 <span data-ttu-id="3210b-106">這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3210b-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="3210b-107">因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="3210b-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="3210b-108">若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。</span><span class="sxs-lookup"><span data-stu-id="3210b-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3210b-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="3210b-109">See Also</span></span>  
 [<span data-ttu-id="3210b-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="3210b-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3210b-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3210b-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3210b-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="3210b-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
