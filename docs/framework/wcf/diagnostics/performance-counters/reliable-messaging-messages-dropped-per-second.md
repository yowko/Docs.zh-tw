---
title: 每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877790"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="a41fc-102">每秒捨棄的可信賴傳訊訊息數</span><span class="sxs-lookup"><span data-stu-id="a41fc-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="a41fc-103">計數器名稱：每秒捨棄的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="a41fc-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a41fc-104">描述</span><span class="sxs-lookup"><span data-stu-id="a41fc-104">Description</span></span>  
 <span data-ttu-id="a41fc-105">在此服務中已捨棄的每秒可信賴傳訊訊息總數。</span><span class="sxs-lookup"><span data-stu-id="a41fc-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="a41fc-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="a41fc-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a41fc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a41fc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
