---
title: 每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473551"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="bf535-102">每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="bf535-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="bf535-103">計數器名稱：每秒未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="bf535-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bf535-104">描述</span><span class="sxs-lookup"><span data-stu-id="bf535-104">Description</span></span>  
 <span data-ttu-id="bf535-105">此作業每秒授權失敗的呼叫數。</span><span class="sxs-lookup"><span data-stu-id="bf535-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="bf535-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="bf535-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="bf535-107">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="bf535-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="bf535-108">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="bf535-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bf535-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="bf535-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
