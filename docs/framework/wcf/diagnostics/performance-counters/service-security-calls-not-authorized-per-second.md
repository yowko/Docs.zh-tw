---
title: 服務：每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536922"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="b5c2f-102">服務：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="b5c2f-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="b5c2f-103">計數器名稱：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="b5c2f-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5c2f-104">描述</span><span class="sxs-lookup"><span data-stu-id="b5c2f-104">Description</span></span>  
 <span data-ttu-id="b5c2f-105">來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="b5c2f-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b5c2f-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="b5c2f-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b5c2f-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649)，使用下列公式來計算其值。</span><span class="sxs-lookup"><span data-stu-id="b5c2f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b5c2f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b5c2f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
