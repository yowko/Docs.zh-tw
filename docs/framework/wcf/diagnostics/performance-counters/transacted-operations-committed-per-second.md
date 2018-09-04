---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564007"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="9819a-102">每秒認可的交易作業數</span><span class="sxs-lookup"><span data-stu-id="9819a-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="9819a-103">計數器名稱：每秒認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="9819a-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9819a-104">描述</span><span class="sxs-lookup"><span data-stu-id="9819a-104">Description</span></span>  
 <span data-ttu-id="9819a-105">此服務每秒所認可的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="9819a-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="9819a-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="9819a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9819a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9819a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
