---
title: 端點：每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163172"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="b7570-102">端點：每秒未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="b7570-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="b7570-103">計數器名稱：每秒未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="b7570-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b7570-104">描述</span><span class="sxs-lookup"><span data-stu-id="b7570-104">Description</span></span>  
 <span data-ttu-id="b7570-105">來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。</span><span class="sxs-lookup"><span data-stu-id="b7570-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b7570-106">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="b7570-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b7570-107">此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。</span><span class="sxs-lookup"><span data-stu-id="b7570-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b7570-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b7570-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
