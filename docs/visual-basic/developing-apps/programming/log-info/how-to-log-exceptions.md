---
title: 如何：在 Visual Basic 中記錄例外狀況
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: b8ec45f43438f8181d9e045cdf43c81db34e4242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="bb98d-102">如何：在 Visual Basic 中記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb98d-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="bb98d-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bb98d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="bb98d-104">下列範例示範如何使用 `My.Application.Log.WriteException` 方法，以記錄您明確攔截到的例外狀況和未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb98d-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="bb98d-105">如需記錄追蹤資訊，請使用 `My.Application.Log.WriteEntry` 方法。</span><span class="sxs-lookup"><span data-stu-id="bb98d-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="bb98d-106">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>。</span><span class="sxs-lookup"><span data-stu-id="bb98d-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="bb98d-107">記錄已處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb98d-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="bb98d-108">建立將產生例外狀況資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="bb98d-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  <span data-ttu-id="bb98d-109">使用 `Try...Catch` 區塊來攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb98d-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  <span data-ttu-id="bb98d-110">將可產生例外狀況的程式碼放在 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="bb98d-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="bb98d-111">取消 `Dim` 和 `MsgBox` 行的註解，造成 <xref:System.NullReferenceException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb98d-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  <span data-ttu-id="bb98d-112">在 `Catch` 區塊中，使用 `My.Application.Log.WriteException` 方法來寫入例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="bb98d-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     <span data-ttu-id="bb98d-113">下列範例顯示用於記錄已處理例外狀況的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="bb98d-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="bb98d-114">記錄未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="bb98d-114">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="bb98d-115">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="bb98d-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bb98d-116">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="bb98d-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="bb98d-117">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb98d-117">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="bb98d-118">按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="bb98d-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="bb98d-119">這會開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb98d-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="bb98d-120">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb98d-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="bb98d-121">在 [一般] 功能表上，選擇 [MyApplication 事件]。</span><span class="sxs-lookup"><span data-stu-id="bb98d-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="bb98d-122">在 [宣告] 功能表上，選擇 [未處理的例外狀況]。</span><span class="sxs-lookup"><span data-stu-id="bb98d-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="bb98d-123">應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。</span><span class="sxs-lookup"><span data-stu-id="bb98d-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="bb98d-124">將 `My.Application.Log.WriteException` 方法加入 `UnhandledException` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bb98d-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     <span data-ttu-id="bb98d-125">下列範例顯示用於記錄未處理例外狀況的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="bb98d-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bb98d-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb98d-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="bb98d-127">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="bb98d-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="bb98d-128">如何：寫入記錄檔訊息</span><span class="sxs-lookup"><span data-stu-id="bb98d-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="bb98d-129">逐步解說：判斷 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="bb98d-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="bb98d-130">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="bb98d-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
