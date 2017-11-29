---
title: "每秒流動的異動數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6769b3d875471ddb56b3888a49f72978f4ee786b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="594cc-102">每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="594cc-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="594cc-103">計數器名稱：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="594cc-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="594cc-104">描述</span><span class="sxs-lookup"><span data-stu-id="594cc-104">Description</span></span>  
 <span data-ttu-id="594cc-105">一秒內流動至此作業的交易數。</span><span class="sxs-lookup"><span data-stu-id="594cc-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="594cc-106">每當傳送給作業的訊息中出現異動識別碼時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="594cc-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="594cc-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="594cc-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="594cc-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="594cc-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
