---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: d000447245d973916dfe0df9af5c46b6fa822e32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475126"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="5e374-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="5e374-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="5e374-103">重新執行訊息重試已傳送給沒有回應的協調器。</span><span class="sxs-lookup"><span data-stu-id="5e374-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e374-104">描述</span><span class="sxs-lookup"><span data-stu-id="5e374-104">Description</span></span>  
 <span data-ttu-id="5e374-105">追蹤本機交易管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「重新執行」訊息給上層協調器。</span><span class="sxs-lookup"><span data-stu-id="5e374-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5e374-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="5e374-106">Troubleshooting</span></span>  
 <span data-ttu-id="5e374-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="5e374-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="5e374-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="5e374-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="5e374-109">這兩個問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="5e374-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e374-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e374-110">See Also</span></span>  
 [<span data-ttu-id="5e374-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="5e374-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5e374-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="5e374-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5e374-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="5e374-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
