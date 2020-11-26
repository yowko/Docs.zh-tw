---
title: 服務：每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: db9e333f740f19e4f82ea0f1306a11e6c21ba996
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236919"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="2ec4e-102">服務：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="2ec4e-102">Service: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="2ec4e-103">計數器名稱：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="2ec4e-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2ec4e-104">描述</span><span class="sxs-lookup"><span data-stu-id="2ec4e-104">Description</span></span>  

 <span data-ttu-id="2ec4e-105">來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="2ec4e-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="2ec4e-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="2ec4e-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="2ec4e-107">此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="2ec4e-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2ec4e-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2ec4e-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
