---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1386d9ac7f58e4dd692bbca3ca3915bc3fe453f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="e83eb-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="e83eb-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="e83eb-103">嘗試連接具名管道端點失敗。</span><span class="sxs-lookup"><span data-stu-id="e83eb-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="e83eb-104">在指定的逾時期間內，進行另一次嘗試。</span><span class="sxs-lookup"><span data-stu-id="e83eb-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e83eb-105">描述</span><span class="sxs-lookup"><span data-stu-id="e83eb-105">Description</span></span>  
 <span data-ttu-id="e83eb-106">這個告知性追蹤表示無法連接到具名通道端點。</span><span class="sxs-lookup"><span data-stu-id="e83eb-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="e83eb-107">如果具名通道端點找不到或忙碌中，可能就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="e83eb-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="e83eb-108">進行額外的嘗試，每個嘗試之間相隔短暫的時間，直到成功或 OpenTimeout 到期為止。</span><span class="sxs-lookup"><span data-stu-id="e83eb-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83eb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e83eb-109">See Also</span></span>  
 [<span data-ttu-id="e83eb-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="e83eb-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e83eb-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="e83eb-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e83eb-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e83eb-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
