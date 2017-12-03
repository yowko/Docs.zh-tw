---
title: "每秒不確定的交易作業數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cefe433bf7b2fb489483962b5f5358897b4cfa6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="d5cf0-102">每秒不確定的交易作業數</span><span class="sxs-lookup"><span data-stu-id="d5cf0-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="d5cf0-103">計數器名稱：每秒不確定的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="d5cf0-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d5cf0-104">描述</span><span class="sxs-lookup"><span data-stu-id="d5cf0-104">Description</span></span>  
 <span data-ttu-id="d5cf0-105">每秒鐘此服務中結果不確定的異動作業數。</span><span class="sxs-lookup"><span data-stu-id="d5cf0-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="d5cf0-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="d5cf0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d5cf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d5cf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
