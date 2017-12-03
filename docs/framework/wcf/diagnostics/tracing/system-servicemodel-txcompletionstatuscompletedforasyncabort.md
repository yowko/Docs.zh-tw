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
ms.openlocfilehash: 2a99e8b3158da9d473d50bc7792ce9e2aa19bb27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="6fe4b-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="6fe4b-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="6fe4b-103">發生非同步中止，指定作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="6fe4b-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6fe4b-104">描述</span><span class="sxs-lookup"><span data-stu-id="6fe4b-104">Description</span></span>  
 <span data-ttu-id="6fe4b-105">目前的交易因另一個參與者有意「中止」、發生逾時或交易參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="6fe4b-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6fe4b-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="6fe4b-106">Troubleshooting</span></span>  
 <span data-ttu-id="6fe4b-107">如果這是未預期的中止，請檢查所有系統記錄檔以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="6fe4b-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe4b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fe4b-108">See Also</span></span>  
 [<span data-ttu-id="6fe4b-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="6fe4b-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6fe4b-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="6fe4b-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6fe4b-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="6fe4b-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
