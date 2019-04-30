---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998188"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="46f58-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="46f58-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="46f58-103">計數器名稱：每秒中止的異動的作業數。</span><span class="sxs-lookup"><span data-stu-id="46f58-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="46f58-104">描述</span><span class="sxs-lookup"><span data-stu-id="46f58-104">Description</span></span>  
 <span data-ttu-id="46f58-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="46f58-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="46f58-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="46f58-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="46f58-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="46f58-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
