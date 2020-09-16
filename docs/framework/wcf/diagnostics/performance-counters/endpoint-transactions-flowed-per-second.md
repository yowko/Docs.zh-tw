---
title: 端點：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 9391651eaaca130ef47ddee9daa95b1f8c116892
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553788"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="a769d-102">端點：每秒流動的異動數</span><span class="sxs-lookup"><span data-stu-id="a769d-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="a769d-103">計數器名稱：每秒流動的交易數。</span><span class="sxs-lookup"><span data-stu-id="a769d-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a769d-104">描述</span><span class="sxs-lookup"><span data-stu-id="a769d-104">Description</span></span>  
 <span data-ttu-id="a769d-105">每秒流動至此端點處作業的交易數。</span><span class="sxs-lookup"><span data-stu-id="a769d-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="a769d-106">每當傳送給端點的訊息中有交易識別碼存在時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="a769d-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="a769d-107">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="a769d-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a769d-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a769d-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
