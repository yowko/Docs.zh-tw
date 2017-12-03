---
title: "每秒的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: baef18df3e1dda8725859c9529ab61c0668c8ff3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="calls-per-second"></a><span data-ttu-id="2c471-102">每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="2c471-102">Calls Per Second</span></span>
<span data-ttu-id="2c471-103">計數器名稱：每秒的呼叫數</span><span class="sxs-lookup"><span data-stu-id="2c471-103">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c471-104">描述</span><span class="sxs-lookup"><span data-stu-id="2c471-104">Description</span></span>  
 <span data-ttu-id="2c471-105">對這個作業的每秒呼叫數。</span><span class="sxs-lookup"><span data-stu-id="2c471-105">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="2c471-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="2c471-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2c471-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2c471-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
