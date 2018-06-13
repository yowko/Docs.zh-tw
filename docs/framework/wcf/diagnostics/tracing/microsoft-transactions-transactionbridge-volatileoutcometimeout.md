---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475627"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="34ff7-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="34ff7-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="34ff7-103">WS-AT 通訊協定服務在等待來自變動參與者的結果訊息回應時逾時。</span><span class="sxs-lookup"><span data-stu-id="34ff7-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="34ff7-104">如果參與者傳回則異動結果可能不確定。</span><span class="sxs-lookup"><span data-stu-id="34ff7-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34ff7-105">描述</span><span class="sxs-lookup"><span data-stu-id="34ff7-105">Description</span></span>  
 <span data-ttu-id="34ff7-106">當「變動」參與者決定要「認可」或「中止」，但是在指定時間內尚未回應「認可」或「復原」要求時就會追蹤。</span><span class="sxs-lookup"><span data-stu-id="34ff7-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="34ff7-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="34ff7-107">Troubleshooting</span></span>  
 <span data-ttu-id="34ff7-108">請確定所有的「變動」參與者都能夠在指定時間內回應。</span><span class="sxs-lookup"><span data-stu-id="34ff7-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="34ff7-109">預設時間週期為 180 秒。</span><span class="sxs-lookup"><span data-stu-id="34ff7-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="34ff7-110">如果時間不夠的話，請增加 WS-AT 的 `VolatileOutcomeDelay` 計時器原則。</span><span class="sxs-lookup"><span data-stu-id="34ff7-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ff7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34ff7-111">See Also</span></span>  
 [<span data-ttu-id="34ff7-112">追蹤</span><span class="sxs-lookup"><span data-stu-id="34ff7-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="34ff7-113">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="34ff7-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="34ff7-114">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="34ff7-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
