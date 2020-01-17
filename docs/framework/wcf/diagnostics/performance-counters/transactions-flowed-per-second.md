---
title: 每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163822"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="e1bc1-102">每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="e1bc1-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="e1bc1-103">計數器名稱：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="e1bc1-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="e1bc1-104">描述</span><span class="sxs-lookup"><span data-stu-id="e1bc1-104">Description</span></span>  
 <span data-ttu-id="e1bc1-105">一秒內流動至此作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="e1bc1-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="e1bc1-106">每當傳送給作業的訊息中出現交易識別碼時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="e1bc1-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="e1bc1-107">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="e1bc1-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e1bc1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e1bc1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
