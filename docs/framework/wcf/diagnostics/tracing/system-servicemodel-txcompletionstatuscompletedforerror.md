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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25106bffe6d541a89c786035db3d3266d861fd5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="e80d3-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="e80d3-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="e80d3-103">由於未處理的執行例外狀況，所以指定之作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="e80d3-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e80d3-104">描述</span><span class="sxs-lookup"><span data-stu-id="e80d3-104">Description</span></span>  
 <span data-ttu-id="e80d3-105">如果在嘗試完成目前交易期間發生錯誤，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e80d3-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="e80d3-106">這個情況會發生在回覆或錯誤傳送至呼叫者之前。</span><span class="sxs-lookup"><span data-stu-id="e80d3-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e80d3-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e80d3-107">Troubleshooting</span></span>  
 <span data-ttu-id="e80d3-108">檢查追蹤訊息，找出例外狀況訊息和任何可執行動作的項目。</span><span class="sxs-lookup"><span data-stu-id="e80d3-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80d3-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="e80d3-109">See Also</span></span>  
 [<span data-ttu-id="e80d3-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="e80d3-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e80d3-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e80d3-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e80d3-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e80d3-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
