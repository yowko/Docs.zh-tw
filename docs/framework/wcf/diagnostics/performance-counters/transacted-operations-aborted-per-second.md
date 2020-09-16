---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: bf7d13f04f0bad315c879f1b4299a78e9515cc56
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550647"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="5ba58-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="5ba58-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="5ba58-103">計數器名稱：每秒中止的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="5ba58-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5ba58-104">描述</span><span class="sxs-lookup"><span data-stu-id="5ba58-104">Description</span></span>  
 <span data-ttu-id="5ba58-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="5ba58-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="5ba58-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="5ba58-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5ba58-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5ba58-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
