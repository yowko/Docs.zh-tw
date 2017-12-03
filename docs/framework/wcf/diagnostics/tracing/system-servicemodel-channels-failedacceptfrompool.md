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
ms.openlocfilehash: 339ba8df7e782281fcec962ff6c6f01988122b3a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="0cb67-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="0cb67-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="0cb67-103">嘗試重複使用共用連線失敗。</span><span class="sxs-lookup"><span data-stu-id="0cb67-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="0cb67-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="0cb67-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0cb67-105">描述</span><span class="sxs-lookup"><span data-stu-id="0cb67-105">Description</span></span>  
 <span data-ttu-id="0cb67-106">這個告知性追蹤表示嘗試重複使用共用連線時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cb67-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="0cb67-107">因為共用連線不相容、尚未就緒或不是使用中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="0cb67-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="0cb67-108">若在指定的逾時值之內額外嘗試重複使用其他的共用連線，會建立新的連線，以防找不到可用的連線。</span><span class="sxs-lookup"><span data-stu-id="0cb67-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb67-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb67-109">See Also</span></span>  
 [<span data-ttu-id="0cb67-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="0cb67-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0cb67-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="0cb67-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0cb67-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0cb67-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
