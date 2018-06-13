---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: dacdf93f4610df9161134a41ece19fd2a18637c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474528"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="d3f9f-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="d3f9f-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="d3f9f-103">計數器名稱：每秒中止的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="d3f9f-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d3f9f-104">描述</span><span class="sxs-lookup"><span data-stu-id="d3f9f-104">Description</span></span>  
 <span data-ttu-id="d3f9f-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="d3f9f-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="d3f9f-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="d3f9f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d3f9f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d3f9f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
