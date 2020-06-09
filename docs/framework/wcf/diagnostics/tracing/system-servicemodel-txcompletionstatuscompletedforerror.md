---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 2bc71d18480fa19be66cbfa1687a7b63eb548309
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601448"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="45df2-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="45df2-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="45df2-103">由於未處理的執行例外狀況，所以指定之作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="45df2-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="45df2-104">描述</span><span class="sxs-lookup"><span data-stu-id="45df2-104">Description</span></span>  
 <span data-ttu-id="45df2-105">如果在嘗試完成目前交易期間發生錯誤，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="45df2-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="45df2-106">這個情況會發生在回覆或錯誤傳送至呼叫者之前。</span><span class="sxs-lookup"><span data-stu-id="45df2-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="45df2-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="45df2-107">Troubleshooting</span></span>  
 <span data-ttu-id="45df2-108">檢查追蹤訊息，找出例外狀況訊息和任何可執行動作的項目。</span><span class="sxs-lookup"><span data-stu-id="45df2-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45df2-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="45df2-109">See also</span></span>

- [<span data-ttu-id="45df2-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="45df2-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="45df2-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="45df2-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="45df2-112">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="45df2-112">Administration and Diagnostics</span></span>](../index.md)
