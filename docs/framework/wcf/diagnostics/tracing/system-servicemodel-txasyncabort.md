---
title: System.ServiceModel.TxAsyncAbort
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eea341e661b1a67c7424158fc0b5c37f04feac99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="d04d9-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="d04d9-102">System.ServiceModel.TxAsyncAbort</span></span>
<span data-ttu-id="d04d9-103">指定的異動已非同步中止。</span><span class="sxs-lookup"><span data-stu-id="d04d9-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d04d9-104">描述</span><span class="sxs-lookup"><span data-stu-id="d04d9-104">Description</span></span>  
 <span data-ttu-id="d04d9-105">目前的交易因另一個參與者有意「中止」、發生逾時或交易參與者內的其他錯誤而中止。</span><span class="sxs-lookup"><span data-stu-id="d04d9-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d04d9-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d04d9-106">Troubleshooting</span></span>  
 <span data-ttu-id="d04d9-107">檢查所有的系統記錄檔，查看這個中止是否為非預期中的，以判斷中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="d04d9-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d04d9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d04d9-108">See Also</span></span>  
 [<span data-ttu-id="d04d9-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="d04d9-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d04d9-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="d04d9-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d04d9-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="d04d9-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
