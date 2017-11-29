---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="0f271-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="0f271-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="0f271-103">PeerMaintainer 模組正在執行特定作業 (追蹤訊息本文中會包含詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="0f271-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f271-104">描述</span><span class="sxs-lookup"><span data-stu-id="0f271-104">Description</span></span>  
 <span data-ttu-id="0f271-105">會在各種 PeerMaintainer 作業期間發生此追蹤。</span><span class="sxs-lookup"><span data-stu-id="0f271-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="0f271-106">PeerMaintainer 是 PeerNode 的內部元件。</span><span class="sxs-lookup"><span data-stu-id="0f271-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="0f271-107">每一分鐘，或是每收到 32 個訊息，就會傳送 LinkUtility 訊息至鄰接項目，訊息內容包含已交換的訊息數目和有用訊息數目 (非重複、未遭竄改) 的統計資料。</span><span class="sxs-lookup"><span data-stu-id="0f271-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="0f271-108">這樣可幫助判斷特定鄰接項目的連結公用程式。</span><span class="sxs-lookup"><span data-stu-id="0f271-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="0f271-109">大約每五分鐘，維護程式就會檢查一次鄰接項目的連線狀態。</span><span class="sxs-lookup"><span data-stu-id="0f271-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="0f271-110">如果鄰接項目連線的數目超過理想數目，維護程式就會去除效用最低的連線。</span><span class="sxs-lookup"><span data-stu-id="0f271-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="0f271-111">如果連線數目不足，則維護程式會擷取新的連線。</span><span class="sxs-lookup"><span data-stu-id="0f271-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f271-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f271-112">See Also</span></span>  
 [<span data-ttu-id="0f271-113">追蹤</span><span class="sxs-lookup"><span data-stu-id="0f271-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0f271-114">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="0f271-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0f271-115">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0f271-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
