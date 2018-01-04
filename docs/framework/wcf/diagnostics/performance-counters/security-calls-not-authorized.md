---
title: "未授權的安全性呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 641d627868c69a5ec63e1acc3f262d315341d0ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="cab77-102">未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="cab77-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="cab77-103">計數器名稱：未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="cab77-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cab77-104">描述</span><span class="sxs-lookup"><span data-stu-id="cab77-104">Description</span></span>  
 <span data-ttu-id="cab77-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="cab77-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="cab77-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="cab77-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
