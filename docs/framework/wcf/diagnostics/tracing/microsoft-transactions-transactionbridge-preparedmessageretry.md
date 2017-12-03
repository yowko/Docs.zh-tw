---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ccfbb975ab274dd0a8f558db44e7d24178ed36a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="59fd2-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="59fd2-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="59fd2-103">準備訊息重試已傳送給沒有回應的協調器。</span><span class="sxs-lookup"><span data-stu-id="59fd2-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="59fd2-104">描述</span><span class="sxs-lookup"><span data-stu-id="59fd2-104">Description</span></span>  
 <span data-ttu-id="59fd2-105">追蹤本機交易管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「準備」訊息給上層協調器。</span><span class="sxs-lookup"><span data-stu-id="59fd2-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="59fd2-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="59fd2-106">Troubleshooting</span></span>  
 <span data-ttu-id="59fd2-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="59fd2-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="59fd2-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="59fd2-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="59fd2-109">這兩個問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="59fd2-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fd2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59fd2-110">See Also</span></span>  
 [<span data-ttu-id="59fd2-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="59fd2-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="59fd2-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="59fd2-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="59fd2-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="59fd2-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
