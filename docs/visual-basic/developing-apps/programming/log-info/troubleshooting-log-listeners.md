---
title: "疑難排解：記錄檔接聽程式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="1c0a3-102">疑難排解：記錄檔接聽程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c0a3-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="1c0a3-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="1c0a3-104">若要判斷哪些記錄檔接聽程式接收這些訊息，請參閱[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="1c0a3-105">`Log` 物件可以使用記錄檔篩選來限制記錄的資訊數量。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="1c0a3-106">如果篩選條件設定錯誤，記錄檔可能包含錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="1c0a3-107">如需詳細資訊，請參閱[逐步解說：篩選 My.Application.Log 輸出](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="1c0a3-108">不過，如果記錄檔設定不正確，您可能需要目前組態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="1c0a3-109">您可以透過記錄檔的進階 `TraceSource` 屬性來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="1c0a3-110">判斷程式碼中記錄檔物件的記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="1c0a3-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="1c0a3-111">在程式碼檔案的開頭處匯入 <xref:System.Diagnostics> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="1c0a3-112">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="1c0a3-113">建立會傳回字串的函式，而該字串包含每個記錄檔接聽程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="1c0a3-114">將記錄檔的追蹤接聽程式集合傳遞至 `GetListeners` 函式，並顯示傳回值。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="1c0a3-115">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="1c0a3-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0a3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c0a3-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="1c0a3-117">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="1c0a3-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="1c0a3-118">逐步解說：判斷 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="1c0a3-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
