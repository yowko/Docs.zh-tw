---
title: 服務：未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: a38b5e0eb467a5cad698fd6e3e01c0adef825d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773317"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="fb400-102">服務：未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="fb400-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="fb400-103">計數器名稱：未獲授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="fb400-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb400-104">描述</span><span class="sxs-lookup"><span data-stu-id="fb400-104">Description</span></span>  
 <span data-ttu-id="fb400-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="fb400-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="fb400-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="fb400-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
