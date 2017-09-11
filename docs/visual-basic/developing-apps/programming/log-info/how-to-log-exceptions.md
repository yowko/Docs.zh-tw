---
title: "如何：在 Visual Basic 中記錄例外狀況"
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
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
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
ms.openlocfilehash: adf2dc683a139d21f24379efc779d4510a2057eb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="b85a9-102">如何：在 Visual Basic 中記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="b85a9-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="b85a9-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之例外狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b85a9-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="b85a9-104">下列範例示範如何使用 `My.Application.Log.WriteException` 方法，以記錄您明確攔截到的例外狀況和未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b85a9-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="b85a9-105">如需記錄追蹤資訊，請使用 `My.Application.Log.WriteEntry` 方法。</span><span class="sxs-lookup"><span data-stu-id="b85a9-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="b85a9-106">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>。</span><span class="sxs-lookup"><span data-stu-id="b85a9-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="b85a9-107">記錄已處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b85a9-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="b85a9-108">建立將產生例外狀況資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="b85a9-108">Create the method that will generate the exception information.</span></span>  
  
     <span data-ttu-id="b85a9-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span></span>  
  
2.  <span data-ttu-id="b85a9-110">使用 `Try...Catch` 區塊來攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b85a9-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     <span data-ttu-id="b85a9-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span></span>  
  
3.  <span data-ttu-id="b85a9-112">將可產生例外狀況的程式碼放在 `Try` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="b85a9-112">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="b85a9-113">取消 `Dim` 和 `MsgBox` 行的註解，造成 <xref:System.NullReferenceException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b85a9-113">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     <span data-ttu-id="b85a9-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span></span>  
  
4.  <span data-ttu-id="b85a9-115">在 `Catch` 區塊中，使用 `My.Application.Log.WriteException` 方法來寫入例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="b85a9-115">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     <span data-ttu-id="b85a9-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span></span>  
  
     <span data-ttu-id="b85a9-117">下列範例顯示用於記錄已處理例外狀況的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="b85a9-117">The following example shows the complete code for logging a handled exception.</span></span>  
  
     <span data-ttu-id="b85a9-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span></span>  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="b85a9-119">記錄未處理的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b85a9-119">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="b85a9-120">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="b85a9-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b85a9-121">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="b85a9-121">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="b85a9-122">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b85a9-122">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="b85a9-123">按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="b85a9-123">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="b85a9-124">這會開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="b85a9-124">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="b85a9-125">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="b85a9-125">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="b85a9-126">在 [一般] 功能表上，選擇 [MyApplication 事件]。</span><span class="sxs-lookup"><span data-stu-id="b85a9-126">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="b85a9-127">在 [宣告] 功能表上，選擇 [未處理的例外狀況]。</span><span class="sxs-lookup"><span data-stu-id="b85a9-127">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="b85a9-128">應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。</span><span class="sxs-lookup"><span data-stu-id="b85a9-128">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="b85a9-129">將 `My.Application.Log.WriteException` 方法加入 `UnhandledException` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b85a9-129">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     <span data-ttu-id="b85a9-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span></span>  
  
     <span data-ttu-id="b85a9-131">下列範例顯示用於記錄未處理例外狀況的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="b85a9-131">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     <span data-ttu-id="b85a9-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="b85a9-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85a9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b85a9-133">See Also</span></span>  
 <span data-ttu-id="b85a9-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b85a9-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="b85a9-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="b85a9-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="b85a9-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="b85a9-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="b85a9-137">[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="b85a9-137">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="b85a9-138">[如何：寫入記錄檔訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b85a9-138">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="b85a9-139">[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="b85a9-139">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="b85a9-140">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="b85a9-140">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

