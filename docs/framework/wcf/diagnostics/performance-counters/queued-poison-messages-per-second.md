---
title: "每秒佇列的有害訊息數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8f22d200834927204918324ced70ac02c3c669f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="fc56c-102">每秒佇列的有害訊息數</span><span class="sxs-lookup"><span data-stu-id="fc56c-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="fc56c-103">計數器名稱：每秒佇列的有害訊息數。</span><span class="sxs-lookup"><span data-stu-id="fc56c-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fc56c-104">描述</span><span class="sxs-lookup"><span data-stu-id="fc56c-104">Description</span></span>  
 <span data-ttu-id="fc56c-105">此服務佇列傳輸標示為有害的每秒訊息數量。</span><span class="sxs-lookup"><span data-stu-id="fc56c-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="fc56c-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="fc56c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fc56c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="fc56c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
