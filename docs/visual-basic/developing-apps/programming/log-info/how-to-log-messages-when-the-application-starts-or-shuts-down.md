---
title: "如何：在應用程式啟動或關閉時記錄訊息 (Visual Basic)"
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
- event logs, shutdown
- My.Application.Log object, logging
- Startup event
- event logs, startup
- Shutdown event
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa5bf57ac5245e9363089b85607b7e6d1a00ba14
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="f2a4b-102">如何：在應用程式啟動或關閉時記錄訊息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2a4b-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="f2a4b-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f2a4b-104">此範例示範如何使用 `My.Application.Log.WriteEntry` 方法 `Startup` 和 `Shutdown` 事件寫入追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="f2a4b-105">存取應用程式的事件處理常式程式碼</span><span class="sxs-lookup"><span data-stu-id="f2a4b-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="f2a4b-106">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f2a4b-107">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="f2a4b-108">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="f2a4b-109">按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="f2a4b-110">這會開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="f2a4b-111">在應用程式啟動時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="f2a4b-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="f2a4b-112">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="f2a4b-113">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="f2a4b-114">在 [宣告]  功能表上，選擇 [啟動] 。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="f2a4b-115">應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="f2a4b-116">將 `My.Application.Log.WriteEntry` 方法加入 `Startup` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     <span data-ttu-id="f2a4b-117">[!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a4b-117">[!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]</span></span>  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="f2a4b-118">在應用程式關閉時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="f2a4b-118">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="f2a4b-119">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-119">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="f2a4b-120">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-120">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="f2a4b-121">在 [宣告]  功能表上，選擇 [關機] 。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-121">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="f2a4b-122">應用程式在主應用程式執行後，但在關閉前引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-122">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="f2a4b-123">將 `My.Application.Log.WriteEntry` 方法加入 `Shutdown` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-123">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     <span data-ttu-id="f2a4b-124">[!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a4b-124">[!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2a4b-125">範例</span><span class="sxs-lookup"><span data-stu-id="f2a4b-125">Example</span></span>  
 <span data-ttu-id="f2a4b-126">您可以使用 [專案設計工具] 在 [程式碼編輯器] 中存取應用程式事件。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-126">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="f2a4b-127">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="f2a4b-127">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="f2a4b-128">[!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a4b-128">[!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a4b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a4b-129">See Also</span></span>  
 <span data-ttu-id="f2a4b-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f2a4b-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="f2a4b-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="f2a4b-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="f2a4b-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="f2a4b-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="f2a4b-133">[專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="f2a4b-133">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
 [<span data-ttu-id="f2a4b-134">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="f2a4b-134">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

