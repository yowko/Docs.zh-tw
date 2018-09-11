---
title: 每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367310"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="1135b-102">每秒發生錯誤的可信賴傳訊工作階段數</span><span class="sxs-lookup"><span data-stu-id="1135b-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="1135b-103">計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="1135b-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1135b-104">描述</span><span class="sxs-lookup"><span data-stu-id="1135b-104">Description</span></span>  
 <span data-ttu-id="1135b-105">在此服務每秒發生的可信賴傳訊工作階段錯誤數。</span><span class="sxs-lookup"><span data-stu-id="1135b-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="1135b-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="1135b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1135b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1135b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
