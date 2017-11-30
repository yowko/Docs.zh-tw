---
title: "每秒失敗的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 504470a7338a22d058f6ae1f99192e9665b4d968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="013b0-102">每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="013b0-102">Calls Failed Per Second</span></span>
<span data-ttu-id="013b0-103">計數器名稱：每秒失敗的呼叫數</span><span class="sxs-lookup"><span data-stu-id="013b0-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="013b0-104">描述</span><span class="sxs-lookup"><span data-stu-id="013b0-104">Description</span></span>  
 <span data-ttu-id="013b0-105">此作業中包含每秒未處理例外狀況的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="013b0-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="013b0-106">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="013b0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="013b0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="013b0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="013b0-108">每當此作業含有未處理的例外狀況時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="013b0-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013b0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013b0-109">See Also</span></span>  
 [<span data-ttu-id="013b0-110">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="013b0-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
