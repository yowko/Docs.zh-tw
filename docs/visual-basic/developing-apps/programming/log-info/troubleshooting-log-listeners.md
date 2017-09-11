---
title: "疑難排解：記錄檔接聽程式 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0542aef4dc60821939e85760e6fadf0dfb528dec
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="1a402-102">疑難排解：記錄檔接聽程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a402-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="1a402-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1a402-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="1a402-104">若要判斷哪些記錄檔接聽程式接收這些訊息，請參閱[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1a402-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="1a402-105">`Log` 物件可以使用記錄檔篩選來限制記錄的資訊數量。</span><span class="sxs-lookup"><span data-stu-id="1a402-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="1a402-106">如果篩選條件設定錯誤，記錄檔可能包含錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="1a402-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="1a402-107">如需詳細資訊，請參閱[逐步解說：篩選 My.Application.Log 輸出](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="1a402-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="1a402-108">不過，如果記錄檔設定不正確，您可能需要目前組態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1a402-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="1a402-109">您可以透過記錄檔的進階 `TraceSource` 屬性來取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="1a402-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="1a402-110">判斷程式碼中記錄檔物件的記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="1a402-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="1a402-111">在程式碼檔案的開頭處匯入 <xref:System.Diagnostics> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1a402-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="1a402-112">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="1a402-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     <span data-ttu-id="1a402-113">[!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1a402-113">[!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]</span></span>  
  
2.  <span data-ttu-id="1a402-114">建立會傳回字串的函式，而該字串包含每個記錄檔接聽程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="1a402-114">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     <span data-ttu-id="1a402-115">[!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1a402-115">[!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]</span></span>  
  
3.  <span data-ttu-id="1a402-116">將記錄檔的追蹤接聽程式集合傳遞至 `GetListeners` 函式，並顯示傳回值。</span><span class="sxs-lookup"><span data-stu-id="1a402-116">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     <span data-ttu-id="1a402-117">[!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1a402-117">[!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]</span></span>  
  
     <span data-ttu-id="1a402-118">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a402-118">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a402-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a402-119">See Also</span></span>  
 <span data-ttu-id="1a402-120"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1a402-120"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="1a402-121">[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="1a402-121">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 [<span data-ttu-id="1a402-122">逐步解說：判斷 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="1a402-122">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

