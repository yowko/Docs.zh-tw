---
title: 每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163926"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="c565a-102">每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="c565a-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="c565a-103">計數器名稱：每秒未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="c565a-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c565a-104">描述</span><span class="sxs-lookup"><span data-stu-id="c565a-104">Description</span></span>  
 <span data-ttu-id="c565a-105">此作業每秒授權失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="c565a-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="c565a-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="c565a-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="c565a-107">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="c565a-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="c565a-108">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="c565a-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c565a-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c565a-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
