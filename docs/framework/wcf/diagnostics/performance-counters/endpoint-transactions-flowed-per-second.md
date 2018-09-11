---
title: 端點：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264353"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="b48e8-102">端點：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="b48e8-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="b48e8-103">計數器名稱：每秒流動的異動數。</span><span class="sxs-lookup"><span data-stu-id="b48e8-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b48e8-104">描述</span><span class="sxs-lookup"><span data-stu-id="b48e8-104">Description</span></span>  
 <span data-ttu-id="b48e8-105">每秒流動至此端點處作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="b48e8-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="b48e8-106">每當傳送給端點的訊息中有異動識別碼存在時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="b48e8-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="b48e8-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="b48e8-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b48e8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b48e8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
