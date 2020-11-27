---
title: 每秒中止的交易作業數
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 1a23420ca1521a11168a859eef61cb8861a144f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250017"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="c7309-102">每秒中止的交易作業數</span><span class="sxs-lookup"><span data-stu-id="c7309-102">Transacted Operations Aborted Per Second</span></span>

<span data-ttu-id="c7309-103">計數器名稱：每秒中止的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="c7309-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7309-104">描述</span><span class="sxs-lookup"><span data-stu-id="c7309-104">Description</span></span>  

 <span data-ttu-id="c7309-105">此服務中每秒中止的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="c7309-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="c7309-106">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="c7309-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c7309-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c7309-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
