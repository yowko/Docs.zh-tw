---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="66eb2-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="66eb2-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="66eb2-103">WS-AT 通訊協定服務無法登錄控制通訊協定的參與者。</span><span class="sxs-lookup"><span data-stu-id="66eb2-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="66eb2-104">描述</span><span class="sxs-lookup"><span data-stu-id="66eb2-104">Description</span></span>  
 <span data-ttu-id="66eb2-105">如果 MSDTC 偵測到無效的登錄要求則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="66eb2-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="66eb2-106">這種情形可能是因為多個完成登錄要求和內部錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="66eb2-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="66eb2-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="66eb2-107">Troubleshooting</span></span>  
 <span data-ttu-id="66eb2-108">請勿嘗試多次登錄完成。</span><span class="sxs-lookup"><span data-stu-id="66eb2-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="66eb2-109">同時，檢查追蹤訊息內的狀態字串，以判斷是否有任何可執行動作的項目存在。</span><span class="sxs-lookup"><span data-stu-id="66eb2-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66eb2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66eb2-110">See Also</span></span>  
 [<span data-ttu-id="66eb2-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="66eb2-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="66eb2-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="66eb2-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="66eb2-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="66eb2-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
