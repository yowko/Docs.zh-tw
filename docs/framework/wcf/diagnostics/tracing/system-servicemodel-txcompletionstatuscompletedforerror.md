---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 591e1a1dcb6746d79ff5eceba7e74e890f327354
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112654"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="0350f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="0350f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="0350f-103">由於未處理的執行例外狀況，所以指定之作業的指定異動已完成。</span><span class="sxs-lookup"><span data-stu-id="0350f-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0350f-104">描述</span><span class="sxs-lookup"><span data-stu-id="0350f-104">Description</span></span>  
 <span data-ttu-id="0350f-105">如果在嘗試完成目前交易期間發生錯誤，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="0350f-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="0350f-106">這個情況會發生在回覆或錯誤傳送至呼叫者之前。</span><span class="sxs-lookup"><span data-stu-id="0350f-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0350f-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0350f-107">Troubleshooting</span></span>  
 <span data-ttu-id="0350f-108">檢查追蹤訊息，找出例外狀況訊息和任何可執行動作的項目。</span><span class="sxs-lookup"><span data-stu-id="0350f-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0350f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0350f-109">See also</span></span>

- [<span data-ttu-id="0350f-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="0350f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0350f-111">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="0350f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0350f-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="0350f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
