---
title: "如何：建立傳回 UI 的增益集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd6956f1934f8594a941b57066cc2d4d6214a9a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="22399-102">如何：建立傳回 UI 的增益集</span><span class="sxs-lookup"><span data-stu-id="22399-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="22399-103">這個範例示範如何建立傳回[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主機[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="22399-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="22399-104">增益集傳回[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也就是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="22399-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="22399-105">此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="22399-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="22399-106">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式裝載增益集與主應用程式視窗的內容以顯示使用者控制項 （增益集所傳回）。</span><span class="sxs-lookup"><span data-stu-id="22399-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="22399-107">**必要條件**</span><span class="sxs-lookup"><span data-stu-id="22399-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="22399-108">此範例中會反白顯示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，讓此案例中，並假設下列：</span><span class="sxs-lookup"><span data-stu-id="22399-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="22399-109">知識的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，包括管線、 增益集與主應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="22399-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="22399-110">如果您不熟悉這些概念，請參閱[增益集和擴充性](../../../../docs/framework/add-ins/index.md)。</span><span class="sxs-lookup"><span data-stu-id="22399-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="22399-111">示範在管線、 增益集，與主應用程式的實作的教學課程，請參閱[逐步解說： 建立可延伸應用程式](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)。</span><span class="sxs-lookup"><span data-stu-id="22399-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="22399-112">知識的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，可以在這裡找到： [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="22399-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22399-113">範例</span><span class="sxs-lookup"><span data-stu-id="22399-113">Example</span></span>  
 <span data-ttu-id="22399-114">若要建立傳回[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]每個管線區段、 增益集，以及主應用程式需要特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="22399-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="22399-115">實作合約管線區段</span><span class="sxs-lookup"><span data-stu-id="22399-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="22399-116">必須傳回合約所定義的方法[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，而且它的傳回值必須是型別<xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="22399-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="22399-117">這示範`GetAddInUI`方法`IWPFAddInContract`合約中的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="22399-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="22399-118">實作增益集檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="22399-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="22399-119">因為增益集實作[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]為的子類別提供<xref:System.Windows.FrameworkElement>，增益集的檢視與相互關聯上的方法`IWPFAddInView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="22399-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="22399-120">下列程式碼顯示合約的增益集檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="22399-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="22399-121">實作增益集端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="22399-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="22399-122">合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但是增益集傳回<xref:System.Windows.FrameworkElement>（如同增益集的檢視所指定）。</span><span class="sxs-lookup"><span data-stu-id="22399-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="22399-123">因此，<xref:System.Windows.FrameworkElement>必須轉換成<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔離界限。</span><span class="sxs-lookup"><span data-stu-id="22399-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="22399-124">這項工作由增益集端配接器呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="22399-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="22399-125">實作主應用程式檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="22399-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="22399-126">因為主應用程式會顯示<xref:System.Windows.FrameworkElement>，與相互關聯的主機 檢視上的方法`IWPFAddInHostView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="22399-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="22399-127">下列程式碼顯示合約的主應用程式檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="22399-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="22399-128">實作主應用程式端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="22399-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="22399-129">合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但主應用程式預期<xref:System.Windows.FrameworkElement>（如同 [主機] 檢視所指定）。</span><span class="sxs-lookup"><span data-stu-id="22399-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="22399-130">因此，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換成<xref:System.Windows.FrameworkElement>之後跨越隔離界限。</span><span class="sxs-lookup"><span data-stu-id="22399-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="22399-131">這項工作由主應用程式端配接器呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="22399-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="22399-132">實作增益集</span><span class="sxs-lookup"><span data-stu-id="22399-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="22399-133">使用增益集端配接器與增益集建立檢視，增益集 (`WPFAddIn1.AddIn`) 必須實作`IWPFAddInView.GetAddInUI`方法以傳回<xref:System.Windows.FrameworkElement>物件 (<xref:System.Windows.Controls.UserControl>在此範例中)。</span><span class="sxs-lookup"><span data-stu-id="22399-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="22399-134">實作<xref:System.Windows.Controls.UserControl>， `AddInUI`，以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="22399-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="22399-135">實作`IWPFAddInView.GetAddInUI`增益集只需要傳回的新執行個體`AddInUI`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="22399-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="22399-136">實作主應用程式</span><span class="sxs-lookup"><span data-stu-id="22399-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="22399-137">主機端配接器和建立的 [主機] 檢視中，主應用程式可以使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，若要開啟管線，請取得增益集，並呼叫主應用程式檢視`IWPFAddInHostView.GetAddInUI`方法。</span><span class="sxs-lookup"><span data-stu-id="22399-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="22399-138">下列程式碼顯示這些步驟。</span><span class="sxs-lookup"><span data-stu-id="22399-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="22399-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22399-139">See Also</span></span>  
 [<span data-ttu-id="22399-140">增益集和擴充性</span><span class="sxs-lookup"><span data-stu-id="22399-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="22399-141">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="22399-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
