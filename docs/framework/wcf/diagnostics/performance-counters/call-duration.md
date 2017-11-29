---
title: "呼叫持續時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4973ec3-3c66-4c0b-b5d0-294b62c83f7d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9bf221115b7919a1ca7facdfe80af2af899b3326
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="call-duration"></a><span data-ttu-id="f7835-102">呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="f7835-102">Call Duration</span></span>
<span data-ttu-id="f7835-103">計數器名稱：呼叫持續時間</span><span class="sxs-lookup"><span data-stu-id="f7835-103">Counter Name: Call Duration</span></span>  
  
## <a name="description"></a><span data-ttu-id="f7835-104">描述</span><span class="sxs-lookup"><span data-stu-id="f7835-104">Description</span></span>  
 <span data-ttu-id="f7835-105">這個作業呼叫的平均持續時間。</span><span class="sxs-lookup"><span data-stu-id="f7835-105">The average duration of calls to this operation.</span></span> <span data-ttu-id="f7835-106">平均持續時間是根據此方程式計算而來：(N1-N0)/(D1-D0)。</span><span class="sxs-lookup"><span data-stu-id="f7835-106">The average duration is calculated based on this equation: (N1-N0)/(D1-D0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f7835-107">在非同步 WCF 服務上使用時，呼叫持續時間計數器一定會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="f7835-107">When used on an asynchronous WCF service the Call Duration counter will always return -1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7835-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7835-108">See Also</span></span>  
 [<span data-ttu-id="f7835-109">PERF_AVERAGE_TIMER</span><span class="sxs-lookup"><span data-stu-id="f7835-109">PERF_AVERAGE_TIMER</span></span>](http://go.microsoft.com/fwlink/?LinkId=95015)
