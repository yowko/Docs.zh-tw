---
title: "端點：每秒發生錯誤的可信賴傳訊工作階段數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f4a8614420a11b31bf3b19fb03e13210f4590a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="200cf-102">端點：每秒發生錯誤的可信賴傳訊工作階段數</span><span class="sxs-lookup"><span data-stu-id="200cf-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="200cf-103">計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。</span><span class="sxs-lookup"><span data-stu-id="200cf-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="200cf-104">描述</span><span class="sxs-lookup"><span data-stu-id="200cf-104">Description</span></span>  
 <span data-ttu-id="200cf-105">在此端點每秒發生的可信賴傳訊工作階段錯誤數。</span><span class="sxs-lookup"><span data-stu-id="200cf-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="200cf-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="200cf-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="200cf-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="200cf-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
