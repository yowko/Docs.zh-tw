---
title: 每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927188"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="f140b-102">每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="f140b-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="f140b-103">計數器名稱：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="f140b-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="f140b-104">描述</span><span class="sxs-lookup"><span data-stu-id="f140b-104">Description</span></span>  
 <span data-ttu-id="f140b-105">一秒內流動至此作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="f140b-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="f140b-106">每當傳送給作業的訊息中出現交易識別碼時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="f140b-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="f140b-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="f140b-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f140b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="f140b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
