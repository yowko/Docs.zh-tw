---
title: 端點：每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: d639d881bcedd336c7bbabd28ec385f60ff54d43
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163783"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="1a24c-102">端點：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="1a24c-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="1a24c-103">計數器名稱：每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="1a24c-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a24c-104">描述</span><span class="sxs-lookup"><span data-stu-id="1a24c-104">Description</span></span>  
 <span data-ttu-id="1a24c-105">對這個端點的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="1a24c-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="1a24c-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="1a24c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1a24c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1a24c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
