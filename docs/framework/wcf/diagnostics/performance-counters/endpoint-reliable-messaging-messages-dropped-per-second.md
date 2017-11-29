---
title: "端點：每秒捨棄的可信賴傳訊訊息數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db61701fabbea99bdf8a8dfc599f6cf9b7e21bb1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="4971c-102">端點：每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="4971c-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="4971c-103">計數器名稱：每秒捨棄的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="4971c-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4971c-104">描述</span><span class="sxs-lookup"><span data-stu-id="4971c-104">Description</span></span>  
 <span data-ttu-id="4971c-105">在此端點上每秒已捨棄的可信賴傳訊訊息數。</span><span class="sxs-lookup"><span data-stu-id="4971c-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="4971c-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="4971c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4971c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="4971c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
