---
title: HOW TO：在應用程式啟動或關閉時記錄訊息 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 20eabd08db0763ec08bb28add41ff63fa3196dd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585626"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="19753-102">HOW TO：在應用程式啟動或關閉時記錄訊息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19753-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="19753-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="19753-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="19753-104">此範例示範如何使用 `My.Application.Log.WriteEntry` 方法 `Startup` 和 `Shutdown` 事件寫入追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="19753-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="19753-105">存取應用程式的事件處理常式程式碼</span><span class="sxs-lookup"><span data-stu-id="19753-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="19753-106">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="19753-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="19753-107">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="19753-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="19753-108">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="19753-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="19753-109">按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="19753-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="19753-110">這會開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="19753-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="19753-111">在應用程式啟動時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="19753-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="19753-112">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="19753-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="19753-113">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="19753-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="19753-114">在 [宣告]  功能表上，選擇 [啟動] 。</span><span class="sxs-lookup"><span data-stu-id="19753-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="19753-115">應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。</span><span class="sxs-lookup"><span data-stu-id="19753-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="19753-116">將 `My.Application.Log.WriteEntry` 方法加入 `Startup` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="19753-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="19753-117">在應用程式關閉時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="19753-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="19753-118">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="19753-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="19753-119">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="19753-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="19753-120">在 [宣告]  功能表上，選擇 [關機] 。</span><span class="sxs-lookup"><span data-stu-id="19753-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="19753-121">應用程式在主應用程式執行後，但在關閉前引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件。</span><span class="sxs-lookup"><span data-stu-id="19753-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="19753-122">將 `My.Application.Log.WriteEntry` 方法加入 `Shutdown` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="19753-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="19753-123">範例</span><span class="sxs-lookup"><span data-stu-id="19753-123">Example</span></span>  
 <span data-ttu-id="19753-124">您可以使用 [專案設計工具] 在 [程式碼編輯器] 中存取應用程式事件。</span><span class="sxs-lookup"><span data-stu-id="19753-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="19753-125">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="19753-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19753-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19753-126">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="19753-127">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19753-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="19753-128">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="19753-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
