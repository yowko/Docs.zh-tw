---
title: 每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: fafc63d692d2a6892330b0be5fe534ace5d7f0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473200"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="a42fe-102">每秒發生錯誤的可信賴傳訊工作階段數</span><span class="sxs-lookup"><span data-stu-id="a42fe-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="a42fe-103">計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="a42fe-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a42fe-104">描述</span><span class="sxs-lookup"><span data-stu-id="a42fe-104">Description</span></span>  
 <span data-ttu-id="a42fe-105">在此服務每秒發生的可信賴傳訊工作階段錯誤數。</span><span class="sxs-lookup"><span data-stu-id="a42fe-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="a42fe-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="a42fe-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a42fe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a42fe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
