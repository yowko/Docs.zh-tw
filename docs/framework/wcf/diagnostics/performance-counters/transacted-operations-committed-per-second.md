---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 3bec51a7be63c54a240b85032ecac09b87173393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474268"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="6e8c0-102">每秒認可的交易作業數</span><span class="sxs-lookup"><span data-stu-id="6e8c0-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="6e8c0-103">計數器名稱：每秒認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="6e8c0-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6e8c0-104">描述</span><span class="sxs-lookup"><span data-stu-id="6e8c0-104">Description</span></span>  
 <span data-ttu-id="6e8c0-105">此服務每秒所認可的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="6e8c0-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="6e8c0-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="6e8c0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6e8c0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="6e8c0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
