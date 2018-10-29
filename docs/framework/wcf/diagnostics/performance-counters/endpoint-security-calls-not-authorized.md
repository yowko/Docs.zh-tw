---
title: 端點：未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: b37d4cd33c41c6e978dd82ca7ce6332302a843de
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198025"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="85f1f-102">端點：未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="85f1f-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="85f1f-103">計數器名稱：未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="85f1f-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="85f1f-104">描述</span><span class="sxs-lookup"><span data-stu-id="85f1f-104">Description</span></span>  
 <span data-ttu-id="85f1f-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="85f1f-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="85f1f-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="85f1f-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
