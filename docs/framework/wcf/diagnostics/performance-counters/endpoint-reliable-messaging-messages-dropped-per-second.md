---
title: 端點：每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797198"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="704e1-102">端點：每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="704e1-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="704e1-103">計數器名稱：每秒捨棄的可靠傳訊工作階段。</span><span class="sxs-lookup"><span data-stu-id="704e1-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="704e1-104">描述</span><span class="sxs-lookup"><span data-stu-id="704e1-104">Description</span></span>  
 <span data-ttu-id="704e1-105">在此端點上每秒已捨棄的可信賴傳訊訊息數。</span><span class="sxs-lookup"><span data-stu-id="704e1-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="704e1-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="704e1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="704e1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="704e1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
