---
title: "端點：每秒流動的異動數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe894d16aee91b893015efdfc627350abcdb6c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="0808c-102">端點：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="0808c-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="0808c-103">計數器名稱：每秒流動的異動數。</span><span class="sxs-lookup"><span data-stu-id="0808c-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0808c-104">描述</span><span class="sxs-lookup"><span data-stu-id="0808c-104">Description</span></span>  
 <span data-ttu-id="0808c-105">每秒流動至此端點處作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="0808c-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="0808c-106">每當傳送給端點的訊息中有異動識別碼存在時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="0808c-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="0808c-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="0808c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0808c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0808c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
