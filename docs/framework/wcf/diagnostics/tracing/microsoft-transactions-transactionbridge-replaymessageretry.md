---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0af06181ce888fe00203cf1e780257cd142be7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="0910d-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="0910d-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="0910d-103">重新執行訊息重試已傳送給沒有回應的協調器。</span><span class="sxs-lookup"><span data-stu-id="0910d-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0910d-104">描述</span><span class="sxs-lookup"><span data-stu-id="0910d-104">Description</span></span>  
 <span data-ttu-id="0910d-105">追蹤本機交易管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「重新執行」訊息給上層協調器。</span><span class="sxs-lookup"><span data-stu-id="0910d-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0910d-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0910d-106">Troubleshooting</span></span>  
 <span data-ttu-id="0910d-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="0910d-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="0910d-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="0910d-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="0910d-109">這兩個問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="0910d-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0910d-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="0910d-110">See Also</span></span>  
 [<span data-ttu-id="0910d-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="0910d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0910d-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0910d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0910d-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0910d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
