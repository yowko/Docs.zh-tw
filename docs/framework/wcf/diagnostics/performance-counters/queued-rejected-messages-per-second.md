---
title: 每秒佇列拒絕的訊息數
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 096e2188b13d0fd5a9be35e5e6473107a58c5566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916182"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="d4fd8-102">每秒佇列拒絕的訊息數</span><span class="sxs-lookup"><span data-stu-id="d4fd8-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="d4fd8-103">計數器名稱：每秒拒絕的訊息排入佇列。</span><span class="sxs-lookup"><span data-stu-id="d4fd8-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d4fd8-104">描述</span><span class="sxs-lookup"><span data-stu-id="d4fd8-104">Description</span></span>  
 <span data-ttu-id="d4fd8-105">此服務的佇列傳輸每秒拒絕的訊息數。</span><span class="sxs-lookup"><span data-stu-id="d4fd8-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="d4fd8-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="d4fd8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d4fd8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d4fd8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
