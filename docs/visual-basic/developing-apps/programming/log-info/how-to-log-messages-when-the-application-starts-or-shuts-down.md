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
ms.openlocfilehash: 8fc7b441c6e19d70ceefa3422cf9823007280b64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330567"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="5c9b0-102">HOW TO：在應用程式啟動或關閉時記錄訊息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c9b0-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="5c9b0-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="5c9b0-104">此範例示範如何使用 `My.Application.Log.WriteEntry` 方法 `Startup` 和 `Shutdown` 事件寫入追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="5c9b0-105">存取應用程式的事件處理常式程式碼</span><span class="sxs-lookup"><span data-stu-id="5c9b0-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="5c9b0-106">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5c9b0-107">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="5c9b0-108">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="5c9b0-109">按一下 [檢視應用程式事件]  按鈕以開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="5c9b0-110">這會開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="5c9b0-111">在應用程式啟動時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="5c9b0-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="5c9b0-112">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="5c9b0-113">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="5c9b0-114">在 [宣告]  功能表上，選擇 [啟動] 。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="5c9b0-115">應用程式在主應用程式執行之前，引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="5c9b0-116">將 `My.Application.Log.WriteEntry` 方法加入 `Startup` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="5c9b0-117">在應用程式關閉時記錄訊息</span><span class="sxs-lookup"><span data-stu-id="5c9b0-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="5c9b0-118">在 [程式碼編輯器] 中開啟 ApplicationEvents.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="5c9b0-119">在 [一般]  功能表上，選擇 [MyApplication 事件] 。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="5c9b0-120">在 [宣告]  功能表上，選擇 [關機] 。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="5c9b0-121">應用程式在主應用程式執行後，但在關閉前引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="5c9b0-122">將 `My.Application.Log.WriteEntry` 方法加入 `Shutdown` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="5c9b0-123">範例</span><span class="sxs-lookup"><span data-stu-id="5c9b0-123">Example</span></span>  
 <span data-ttu-id="5c9b0-124">您可以使用 [專案設計工具] 在 [程式碼編輯器] 中存取應用程式事件。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="5c9b0-125">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="5c9b0-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5c9b0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c9b0-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="5c9b0-127">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c9b0-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="5c9b0-128">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="5c9b0-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
