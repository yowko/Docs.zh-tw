---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf6c70bdcfc402322dd1f20bbff2be74c111798a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="ff6e2-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="ff6e2-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="ff6e2-103">發生非同步中止，指定作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="ff6e2-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ff6e2-104">描述</span><span class="sxs-lookup"><span data-stu-id="ff6e2-104">Description</span></span>  
 <span data-ttu-id="ff6e2-105">目前的交易因另一個參與者有意「中止」、發生逾時或交易參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="ff6e2-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ff6e2-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ff6e2-106">Troubleshooting</span></span>  
 <span data-ttu-id="ff6e2-107">如果這是未預期的中止，請檢查所有系統記錄檔以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="ff6e2-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6e2-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="ff6e2-108">See Also</span></span>  
 [<span data-ttu-id="ff6e2-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="ff6e2-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ff6e2-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="ff6e2-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ff6e2-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="ff6e2-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
