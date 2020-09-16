---
title: 每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552202"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="a3df8-102">每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="a3df8-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="a3df8-103">計數器名稱：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="a3df8-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="a3df8-104">描述</span><span class="sxs-lookup"><span data-stu-id="a3df8-104">Description</span></span>  
 <span data-ttu-id="a3df8-105">一秒內流動至此作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="a3df8-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="a3df8-106">每當傳送給作業的訊息中出現交易識別碼時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="a3df8-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="a3df8-107">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="a3df8-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a3df8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a3df8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
