---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bce99f11ba5a18e80c24fc51e65b66de97f9e7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="95d07-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="95d07-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="95d07-103">由於未處理的執行例外狀況，所以指定之作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="95d07-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="95d07-104">描述</span><span class="sxs-lookup"><span data-stu-id="95d07-104">Description</span></span>  
 <span data-ttu-id="95d07-105">如果在嘗試完成目前交易期間發生錯誤，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="95d07-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="95d07-106">這個情況會發生在回覆或錯誤傳送至呼叫者之前。</span><span class="sxs-lookup"><span data-stu-id="95d07-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="95d07-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="95d07-107">Troubleshooting</span></span>  
 <span data-ttu-id="95d07-108">檢查追蹤訊息，找出例外狀況訊息和任何可執行動作的項目。</span><span class="sxs-lookup"><span data-stu-id="95d07-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d07-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95d07-109">See Also</span></span>  
 [<span data-ttu-id="95d07-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="95d07-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="95d07-111">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="95d07-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="95d07-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="95d07-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
