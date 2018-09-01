---
title: 端點：每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4cefdd7480c7d0e9475b1883e603d9db1f287d4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386620"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="b58f6-102">端點：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="b58f6-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="b58f6-103">計數器名稱：每秒未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="b58f6-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b58f6-104">描述</span><span class="sxs-lookup"><span data-stu-id="b58f6-104">Description</span></span>  
 <span data-ttu-id="b58f6-105">來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="b58f6-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b58f6-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="b58f6-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b58f6-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="b58f6-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b58f6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b58f6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
