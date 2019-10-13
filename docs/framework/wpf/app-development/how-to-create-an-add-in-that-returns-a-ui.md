---
title: 作法：建立傳回 UI 的增益集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: e32987355a6c7ad32b5e0e8522dc4daa63783fdd
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291254"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="40023-102">作法：建立傳回 UI 的增益集</span><span class="sxs-lookup"><span data-stu-id="40023-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="40023-103">這個範例示範如何建立將 Windows Presentation Foundation （WPF）傳回給主控制項 WPF 獨立應用程式的增益集。</span><span class="sxs-lookup"><span data-stu-id="40023-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="40023-104">此增益集會傳回做為 WPF 使用者控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="40023-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="40023-105">此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="40023-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="40023-106">WPF 獨立應用程式會裝載增益集，並顯示使用者控制項（由增益集傳回）做為主應用程式視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="40023-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="40023-107">**必要條件**</span><span class="sxs-lookup"><span data-stu-id="40023-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="40023-108">這個範例會反白顯示可啟用此案例之 .NET Framework 增益集模型的 WPF 延伸模組，並假設下列各項：</span><span class="sxs-lookup"><span data-stu-id="40023-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="40023-109">.NET Framework 增益集模型的知識，包括管線、增益集和主機開發。</span><span class="sxs-lookup"><span data-stu-id="40023-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="40023-110">如果您不熟悉這些概念，請參閱[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性。</span><span class="sxs-lookup"><span data-stu-id="40023-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="40023-111">如需示範管線、增益集和主應用程式之執行的教學課程，請參閱 @no__t 0Walkthrough：建立可擴充的應用程式 @ no__t-0。</span><span class="sxs-lookup"><span data-stu-id="40023-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
- <span data-ttu-id="40023-112">.NET Framework 增益集模型的 WPF 延伸模組知識，可以在這裡找到：[WPF 增益集總覽](wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="40023-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40023-113">範例</span><span class="sxs-lookup"><span data-stu-id="40023-113">Example</span></span>  
 <span data-ttu-id="40023-114">若要建立可傳回 WPF UI 的增益集，需要每個管線區段、增益集和主應用程式的特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="40023-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="40023-115">實作合約管線區段</span><span class="sxs-lookup"><span data-stu-id="40023-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="40023-116">方法必須由合約定義以傳回 UI，而且其傳回值的類型必須是 <xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="40023-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="40023-117">這是在下列程式碼中，由 `IWPFAddInContract` 合約的 `GetAddInUI` 方法所示範。</span><span class="sxs-lookup"><span data-stu-id="40023-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="40023-118">實作增益集檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="40023-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="40023-119">因為增益集會將它所提供的 Ui 當做 <xref:System.Windows.FrameworkElement> 的子類別，所以與 `IWPFAddInView.GetAddInUI` 相關聯之增益集視圖上的方法必須傳回 <xref:System.Windows.FrameworkElement> 類型的值。</span><span class="sxs-lookup"><span data-stu-id="40023-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="40023-120">下列程式碼顯示合約的增益集檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="40023-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="40023-121">實作增益集端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="40023-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="40023-122">合約方法會傳回 <xref:System.AddIn.Contract.INativeHandleContract>，但增益集會傳回 <xref:System.Windows.FrameworkElement> （如 [增益集] 視圖所指定）。</span><span class="sxs-lookup"><span data-stu-id="40023-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="40023-123">因此，在跨越隔離界限之前，<xref:System.Windows.FrameworkElement> 必須轉換成 <xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="40023-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="40023-124">這項工作是由增益集端介面卡藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 來執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="40023-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="40023-125">實作主應用程式檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="40023-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="40023-126">因為主應用程式會顯示 <xref:System.Windows.FrameworkElement>，所以與 `IWPFAddInHostView.GetAddInUI` 關聯之主控制項上的方法必須傳回類型 <xref:System.Windows.FrameworkElement> 的值。</span><span class="sxs-lookup"><span data-stu-id="40023-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="40023-127">下列程式碼顯示合約的主應用程式檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="40023-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="40023-128">實作主應用程式端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="40023-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="40023-129">合約方法會傳回 <xref:System.AddIn.Contract.INativeHandleContract>，但主應用程式預期會有 <xref:System.Windows.FrameworkElement> （如主機視圖所指定）。</span><span class="sxs-lookup"><span data-stu-id="40023-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="40023-130">因此，在跨越隔離界限之後，<xref:System.AddIn.Contract.INativeHandleContract> 必須轉換成 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="40023-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="40023-131">這項工作是由主機端介面卡藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 來執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="40023-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="40023-132">實作增益集</span><span class="sxs-lookup"><span data-stu-id="40023-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="40023-133">建立增益集端介面卡和增益集視圖之後，增益集（`WPFAddIn1.AddIn`）必須執行 `IWPFAddInView.GetAddInUI` 方法，以傳回 <xref:System.Windows.FrameworkElement> 物件（在此範例中為 <xref:System.Windows.Controls.UserControl>）。</span><span class="sxs-lookup"><span data-stu-id="40023-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="40023-134">@No__t-0，`AddInUI` 的實作為下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="40023-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="40023-135">增益集 `IWPFAddInView.GetAddInUI` 的執行只需要傳回 `AddInUI` 的新實例，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="40023-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="40023-136">實作主應用程式</span><span class="sxs-lookup"><span data-stu-id="40023-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="40023-137">建立主機端介面卡和主控制項時，主應用程式可以使用 .NET Framework 增益集模型來開啟管線、取得增益集的主控制項，以及呼叫 `IWPFAddInHostView.GetAddInUI` 方法。</span><span class="sxs-lookup"><span data-stu-id="40023-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="40023-138">下列程式碼顯示這些步驟。</span><span class="sxs-lookup"><span data-stu-id="40023-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="40023-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40023-139">See also</span></span>

- <span data-ttu-id="40023-140">[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="40023-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="40023-141">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="40023-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
