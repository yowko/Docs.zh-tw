---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 0c9e79709f5929e1fa123a8d1695ca720046e9e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190869"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="19e8c-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="19e8c-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="19e8c-103">重新執行訊息重試已傳送給沒有回應的協調器。</span><span class="sxs-lookup"><span data-stu-id="19e8c-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="19e8c-104">描述</span><span class="sxs-lookup"><span data-stu-id="19e8c-104">Description</span></span>  
 <span data-ttu-id="19e8c-105">追蹤本機異動管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「重新執行」訊息給上層協調器。</span><span class="sxs-lookup"><span data-stu-id="19e8c-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="19e8c-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="19e8c-106">Troubleshooting</span></span>  
 <span data-ttu-id="19e8c-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="19e8c-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="19e8c-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="19e8c-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="19e8c-109">這兩個問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="19e8c-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e8c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19e8c-110">See also</span></span>

- [<span data-ttu-id="19e8c-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="19e8c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="19e8c-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="19e8c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="19e8c-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="19e8c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
