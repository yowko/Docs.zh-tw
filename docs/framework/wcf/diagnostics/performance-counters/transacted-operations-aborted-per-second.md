---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: d03f1faf7d2a00d02500fe9759ba940445d8eee3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164017"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="5a649-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="5a649-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="5a649-103">計數器名稱：每秒中止的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="5a649-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a649-104">描述</span><span class="sxs-lookup"><span data-stu-id="5a649-104">Description</span></span>  
 <span data-ttu-id="5a649-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="5a649-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="5a649-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="5a649-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5a649-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5a649-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
