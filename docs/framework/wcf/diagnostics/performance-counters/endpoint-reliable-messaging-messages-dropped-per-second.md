---
title: 端點：每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: a87e5fef0c13e239959a386f108af3c4cebae7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472280"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="9beb1-102">端點：每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="9beb1-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="9beb1-103">計數器名稱：每秒捨棄的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="9beb1-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9beb1-104">描述</span><span class="sxs-lookup"><span data-stu-id="9beb1-104">Description</span></span>  
 <span data-ttu-id="9beb1-105">在此端點上每秒已捨棄的可信賴傳訊訊息數。</span><span class="sxs-lookup"><span data-stu-id="9beb1-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="9beb1-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="9beb1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9beb1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9beb1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
