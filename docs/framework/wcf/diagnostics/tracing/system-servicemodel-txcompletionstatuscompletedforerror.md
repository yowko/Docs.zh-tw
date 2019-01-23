---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: e36126dcdfcc87a410d200cdf23aac670dc2b5e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596500"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="24d43-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="24d43-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="24d43-103">由於未處理的執行例外狀況，所以指定之作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="24d43-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="24d43-104">描述</span><span class="sxs-lookup"><span data-stu-id="24d43-104">Description</span></span>  
 <span data-ttu-id="24d43-105">如果在嘗試完成目前交易期間發生錯誤，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="24d43-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="24d43-106">這個情況會發生在回覆或錯誤傳送至呼叫者之前。</span><span class="sxs-lookup"><span data-stu-id="24d43-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="24d43-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="24d43-107">Troubleshooting</span></span>  
 <span data-ttu-id="24d43-108">檢查追蹤訊息，找出例外狀況訊息和任何可執行動作的項目。</span><span class="sxs-lookup"><span data-stu-id="24d43-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d43-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24d43-109">See also</span></span>
- [<span data-ttu-id="24d43-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="24d43-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="24d43-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="24d43-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="24d43-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="24d43-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
