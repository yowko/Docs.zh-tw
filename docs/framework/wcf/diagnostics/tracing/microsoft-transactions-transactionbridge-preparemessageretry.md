---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7b53620a08d21d40a230f82b3b2b3ea3cd05feea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="32320-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="32320-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="32320-103">準備訊息重試已傳送給沒有回應的參與者。</span><span class="sxs-lookup"><span data-stu-id="32320-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="32320-104">描述</span><span class="sxs-lookup"><span data-stu-id="32320-104">Description</span></span>  
 <span data-ttu-id="32320-105">如果本機 [交易管理員] 因為下層參與者未在指定時間內接收到回應，而需要重新傳送「準備」訊息給下層參與者，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="32320-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="32320-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="32320-106">Troubleshooting</span></span>  
 <span data-ttu-id="32320-107">調查讓回應無法準時傳遞的潛在網路或產品問題。</span><span class="sxs-lookup"><span data-stu-id="32320-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="32320-108">如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。</span><span class="sxs-lookup"><span data-stu-id="32320-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="32320-109">這兩種問題都會大幅降低系統內的異動量。</span><span class="sxs-lookup"><span data-stu-id="32320-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32320-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32320-110">See Also</span></span>  
 [<span data-ttu-id="32320-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="32320-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="32320-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="32320-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="32320-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="32320-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
