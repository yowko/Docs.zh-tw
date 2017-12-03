---
title: "每秒認可的交易作業數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8708e7f030e0c10028938abcdccb54903a7fca52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="72e10-102">每秒認可的交易作業數</span><span class="sxs-lookup"><span data-stu-id="72e10-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="72e10-103">計數器名稱：每秒認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="72e10-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="72e10-104">描述</span><span class="sxs-lookup"><span data-stu-id="72e10-104">Description</span></span>  
 <span data-ttu-id="72e10-105">此服務每秒所認可的交易作業數。</span><span class="sxs-lookup"><span data-stu-id="72e10-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="72e10-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="72e10-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="72e10-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="72e10-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
