---
title: 端點：每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 7dc52caea0233953dd72e77e4d662083f4a370e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164043"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="65ecd-102">端點：每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="65ecd-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="65ecd-103">計數器名稱：每秒捨棄的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="65ecd-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="65ecd-104">描述</span><span class="sxs-lookup"><span data-stu-id="65ecd-104">Description</span></span>  
 <span data-ttu-id="65ecd-105">在此端點上每秒已捨棄的可信賴傳訊訊息數。</span><span class="sxs-lookup"><span data-stu-id="65ecd-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="65ecd-106">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="65ecd-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="65ecd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="65ecd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
