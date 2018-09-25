---
title: 端點：未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
ms.openlocfilehash: 2d2f114d45675ece23f818d4d56bcc40684f9dbf
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156284"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="63dc0-102">端點：未授權的安全性呼叫數</span><span class="sxs-lookup"><span data-stu-id="63dc0-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="63dc0-103">計數器名稱：未授權的安全性呼叫數。</span><span class="sxs-lookup"><span data-stu-id="63dc0-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="63dc0-104">描述</span><span class="sxs-lookup"><span data-stu-id="63dc0-104">Description</span></span>  
 <span data-ttu-id="63dc0-105">當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。</span><span class="sxs-lookup"><span data-stu-id="63dc0-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="63dc0-106">這表示傳入訊息是來自有效的使用者而且有適當地加以保護，但是未授權使用者執行特定工作的權限。</span><span class="sxs-lookup"><span data-stu-id="63dc0-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
