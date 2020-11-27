---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 28b83b293570adf3b1cfdc15c77afd0f0cf768eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259021"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="74c6d-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="74c6d-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="74c6d-103">認可訊息重試已傳送給沒有回應的參與者。</span><span class="sxs-lookup"><span data-stu-id="74c6d-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="74c6d-104">描述</span><span class="sxs-lookup"><span data-stu-id="74c6d-104">Description</span></span>  

 <span data-ttu-id="74c6d-105">如果本機 [交易管理員] 因為下層參與者未在指定時間內接收到回應，而需要重新傳送「認可」訊息給下層參與者，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="74c6d-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="74c6d-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="74c6d-106">Troubleshooting</span></span>  

 <span data-ttu-id="74c6d-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="74c6d-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="74c6d-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="74c6d-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="74c6d-109">這兩個問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="74c6d-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c6d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74c6d-110">See also</span></span>

- [<span data-ttu-id="74c6d-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="74c6d-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="74c6d-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="74c6d-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="74c6d-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="74c6d-113">Administration and Diagnostics</span></span>](../index.md)
