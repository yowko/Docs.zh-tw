---
title: "如何：存取 Managed HTML 文件物件模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ee8c5e0cd578a0eb821a35a27c5ff0072e5533
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="6b004-102">如何：存取 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="6b004-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="6b004-103">您可以從兩種類型的應用程式中，存取受管理的「HTML 文件物件模型」(DOM)：</span><span class="sxs-lookup"><span data-stu-id="6b004-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="6b004-104">執行有受管理之 <xref:System.Windows.Forms.WebBrowser> 控制項的 Windows Forms 應用程式 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="6b004-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="6b004-105">這兩種技術為互補，<xref:System.Windows.Forms.WebBrowser> 控制項負責將頁面顯示給使用者，HTML DOM 負責顯示文件的邏輯結構。</span><span class="sxs-lookup"><span data-stu-id="6b004-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="6b004-106">Windows Forms <xref:System.Windows.Forms.UserControl> 會在 Internet Explorer 中執行。</span><span class="sxs-lookup"><span data-stu-id="6b004-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="6b004-107">無論要變更文件的結構，或開啟強制回應對話方塊等等，都可以使用負責顯示您 <xref:System.Windows.Forms.UserControl> 執行所在之頁面的 HTML DOM。</span><span class="sxs-lookup"><span data-stu-id="6b004-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="6b004-108">從 Windows Forms 應用程式存取 DOM</span><span class="sxs-lookup"><span data-stu-id="6b004-108">To access DOM from a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="6b004-109">在 Windows Forms 應用程式中執行 <xref:System.Windows.Forms.WebBrowser> 控制項並監視 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="6b004-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="6b004-110">如需裝載控制項以及監視事件的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6b004-110">For details on hosting controls and monitoring for events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
2.  <span data-ttu-id="6b004-111">存取 <xref:System.Windows.Forms.HtmlDocument> 控制項的 <xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性，以擷取目前頁面的 <xref:System.Windows.Forms.WebBrowser>。</span><span class="sxs-lookup"><span data-stu-id="6b004-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="6b004-112">存取 Internet Explorer 中所執行之 UserControl 的 DOM</span><span class="sxs-lookup"><span data-stu-id="6b004-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="6b004-113">建立您自己之 <xref:System.Windows.Forms.UserControl> 類別的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="6b004-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="6b004-114">如需詳細資訊，請參閱[如何：撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6b004-114">For more information, see [How to: Author Composite Controls](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span></span>  
  
2.  <span data-ttu-id="6b004-115">將下列程式碼放入您 <xref:System.Windows.Forms.UserControl> 的 Load 事件處理常式中：</span><span class="sxs-lookup"><span data-stu-id="6b004-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6b004-116">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6b004-116">Robust Programming</span></span>  
  
1.  <span data-ttu-id="6b004-117">透過 <xref:System.Windows.Forms.WebBrowser> 控制項使用 DOM 時，請務必等候 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件發生，再嘗試存取 <xref:System.Windows.Forms.WebBrowser.Document%2A> 控制項的 <xref:System.Windows.Forms.WebBrowser> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b004-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="6b004-118">當整份文件全部載入之後，會引發 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件，若您在此之前使用 DOM，可能會導致應用程式執行時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b004-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6b004-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6b004-119">.NET Framework Security</span></span>  
  
1.  <span data-ttu-id="6b004-120">您的應用程式或 <xref:System.Windows.Forms.UserControl> 需要完全信任，才能存取受管理的 HTML DOM。</span><span class="sxs-lookup"><span data-stu-id="6b004-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="6b004-121">若要部署使用 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 的 Windows Forms 應用程式，可以使用「使用權限提高」或「受信任的應用程式部署」要求完全信任；如需詳細資料，請參閱[保護 ClickOnce 應用程式](/visualstudio/deployment/securing-clickonce-applications)。</span><span class="sxs-lookup"><span data-stu-id="6b004-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b004-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b004-122">See Also</span></span>  
 [<span data-ttu-id="6b004-123">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="6b004-123">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
