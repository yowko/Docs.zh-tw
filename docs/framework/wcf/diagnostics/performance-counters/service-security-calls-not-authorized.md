---
title: "服務：未授權的安全性呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5dae370d90082c9efe89f9d523740fc25ece21ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="d06b5-102">服務：未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="d06b5-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="d06b5-103">計數器名稱：未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="d06b5-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d06b5-104">描述</span><span class="sxs-lookup"><span data-stu-id="d06b5-104">Description</span></span>  
 <span data-ttu-id="d06b5-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="d06b5-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d06b5-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="d06b5-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
