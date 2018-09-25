---
title: 端點：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079632"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="1ee0c-102">端點：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="1ee0c-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="1ee0c-103">計數器名稱：每秒流動的異動數。</span><span class="sxs-lookup"><span data-stu-id="1ee0c-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ee0c-104">描述</span><span class="sxs-lookup"><span data-stu-id="1ee0c-104">Description</span></span>  
 <span data-ttu-id="1ee0c-105">每秒流動至此端點處作業的異動數。</span><span class="sxs-lookup"><span data-stu-id="1ee0c-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="1ee0c-106">每當傳送給端點的訊息中有異動識別碼存在時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="1ee0c-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="1ee0c-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="1ee0c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1ee0c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1ee0c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
