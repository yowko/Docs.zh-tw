---
title: 端點：未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: b37d4cd33c41c6e978dd82ca7ce6332302a843de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916275"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="26fd2-102">端點：未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="26fd2-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="26fd2-103">計數器名稱：未獲授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="26fd2-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="26fd2-104">描述</span><span class="sxs-lookup"><span data-stu-id="26fd2-104">Description</span></span>  
 <span data-ttu-id="26fd2-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="26fd2-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="26fd2-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="26fd2-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
