---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467470"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="29efe-102">每秒認可的交易作業數</span><span class="sxs-lookup"><span data-stu-id="29efe-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="29efe-103">計數器名稱：每秒認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="29efe-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="29efe-104">描述</span><span class="sxs-lookup"><span data-stu-id="29efe-104">Description</span></span>  
 <span data-ttu-id="29efe-105">此服務每秒所認可的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="29efe-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="29efe-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="29efe-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="29efe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="29efe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
