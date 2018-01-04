---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41cb1b301d3abc6a15992f36929416053ffa6069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="cfbe8-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="cfbe8-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="cfbe8-103">WS-AT 通訊協定服務無法使用所提供的協調內容登記異動。</span><span class="sxs-lookup"><span data-stu-id="cfbe8-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cfbe8-104">描述</span><span class="sxs-lookup"><span data-stu-id="cfbe8-104">Description</span></span>  
 <span data-ttu-id="cfbe8-105">當 MSDTC 無法登記指定之 2pc 通訊協定的異動時，便會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="cfbe8-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="cfbe8-106">這種情況可能因為異動不再存在、不再允許登記，或是已經存在太多登記而發生。</span><span class="sxs-lookup"><span data-stu-id="cfbe8-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cfbe8-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="cfbe8-107">Troubleshooting</span></span>  
 <span data-ttu-id="cfbe8-108">請檢查追蹤訊息內的狀態字串，以判斷是否有任何可執行動作的項目存在。</span><span class="sxs-lookup"><span data-stu-id="cfbe8-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbe8-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfbe8-109">See Also</span></span>  
 [<span data-ttu-id="cfbe8-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="cfbe8-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cfbe8-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="cfbe8-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cfbe8-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="cfbe8-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
