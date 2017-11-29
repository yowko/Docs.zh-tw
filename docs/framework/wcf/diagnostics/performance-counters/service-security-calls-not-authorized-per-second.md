---
title: "服務：每秒未授權的安全性呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ad28d6afe26537e7a3eface8be70bcecf15b7aa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="53eb2-102">服務：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="53eb2-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="53eb2-103">計數器名稱：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="53eb2-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="53eb2-104">描述</span><span class="sxs-lookup"><span data-stu-id="53eb2-104">Description</span></span>  
 <span data-ttu-id="53eb2-105">來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="53eb2-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="53eb2-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="53eb2-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="53eb2-107">這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649)，其值使用以下公式計算。</span><span class="sxs-lookup"><span data-stu-id="53eb2-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="53eb2-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="53eb2-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
