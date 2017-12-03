---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a4bbaca70954e5aa89dbcfd14723551de7848f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="40cc8-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="40cc8-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="40cc8-103">WS-AT 通訊協定服務在等待來自變動參與者的結果訊息回應時逾時。</span><span class="sxs-lookup"><span data-stu-id="40cc8-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="40cc8-104">如果參與者傳回則交易結果可能不確定。</span><span class="sxs-lookup"><span data-stu-id="40cc8-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="40cc8-105">描述</span><span class="sxs-lookup"><span data-stu-id="40cc8-105">Description</span></span>  
 <span data-ttu-id="40cc8-106">當「變動」參與者決定要「認可」或「中止」，但是在指定時間內尚未回應「認可」或「復原」要求時就會追蹤。</span><span class="sxs-lookup"><span data-stu-id="40cc8-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="40cc8-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="40cc8-107">Troubleshooting</span></span>  
 <span data-ttu-id="40cc8-108">請確定所有的「變動」參與者都能夠在指定時間內回應。</span><span class="sxs-lookup"><span data-stu-id="40cc8-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="40cc8-109">預設時間週期為 180 秒。</span><span class="sxs-lookup"><span data-stu-id="40cc8-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="40cc8-110">如果時間不夠的話，請增加 WS-AT 的 `VolatileOutcomeDelay` 計時器原則。</span><span class="sxs-lookup"><span data-stu-id="40cc8-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40cc8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40cc8-111">See Also</span></span>  
 [<span data-ttu-id="40cc8-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="40cc8-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="40cc8-113">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="40cc8-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="40cc8-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="40cc8-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
