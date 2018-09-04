---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500555"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="abba1-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="abba1-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="abba1-103">計數器名稱：每秒中止的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="abba1-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="abba1-104">描述</span><span class="sxs-lookup"><span data-stu-id="abba1-104">Description</span></span>  
 <span data-ttu-id="abba1-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="abba1-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="abba1-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="abba1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="abba1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="abba1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
