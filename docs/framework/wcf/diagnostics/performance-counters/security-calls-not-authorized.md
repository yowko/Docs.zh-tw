---
title: 未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
author: BrucePerlerMS
ms.openlocfilehash: 6af1c7576e6a0fe7ae21f6f1997b2ebe3b919214
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111902"
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="3fa7a-102">未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="3fa7a-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="3fa7a-103">計數器名稱：未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="3fa7a-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3fa7a-104">描述</span><span class="sxs-lookup"><span data-stu-id="3fa7a-104">Description</span></span>  
 <span data-ttu-id="3fa7a-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="3fa7a-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="3fa7a-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="3fa7a-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
