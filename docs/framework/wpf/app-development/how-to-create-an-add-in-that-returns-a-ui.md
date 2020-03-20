---
title: 如何：建立傳回 UI 的增益集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174585"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="52d75-102">如何：建立傳回 UI 的增益集</span><span class="sxs-lookup"><span data-stu-id="52d75-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="52d75-103">此示例演示如何創建將 Windows 演示文稿基礎 （WPF） 返回到主機 WPF 獨立應用程式的外接程式。</span><span class="sxs-lookup"><span data-stu-id="52d75-103">This example shows how to create an add-in that returns a Windows Presentation Foundation (WPF) to a host WPF standalone application.</span></span>  
  
 <span data-ttu-id="52d75-104">外接程式返回作為 WPF 使用者控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="52d75-104">The add-in returns a UI that is a WPF user control.</span></span> <span data-ttu-id="52d75-105">此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="52d75-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="52d75-106">WPF 獨立應用程式承載外接程式，並將使用者控制項（由外接程式返回）顯示為主應用程式視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="52d75-106">The WPF standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="52d75-107">**必要條件**</span><span class="sxs-lookup"><span data-stu-id="52d75-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="52d75-108">此示例突出顯示啟用此方案的 .NET 框架外接程式模型的 WPF 擴展，並假定以下內容：</span><span class="sxs-lookup"><span data-stu-id="52d75-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="52d75-109">瞭解 .NET 框架外接程式模型，包括管道、外接程式和主機開發。</span><span class="sxs-lookup"><span data-stu-id="52d75-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="52d75-110">如果您不熟悉這些概念，請參閱[載入項和可擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="52d75-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="52d75-111">有關演示管道、外接程式和主機應用程式的實現的教程，請參閱[演練：創建可擴展應用程式](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="52d75-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="52d75-112">WPF 擴展到 .NET 框架外接程式模型的知識，可以在此處找到[：WPF 外接程式概述](wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="52d75-112">Knowledge of the WPF extensions to the .NET Framework add-in model, which can be found here: [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d75-113">範例</span><span class="sxs-lookup"><span data-stu-id="52d75-113">Example</span></span>  
 <span data-ttu-id="52d75-114">要創建返回 WPF UI 的外接程式，需要為每個管道段、外接程式和主機應用程式提供特定代碼。</span><span class="sxs-lookup"><span data-stu-id="52d75-114">To create an add-in that returns a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="52d75-115">實作合約管線區段</span><span class="sxs-lookup"><span data-stu-id="52d75-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="52d75-116">方法必須由返回 UI 的協定定義，並且其傳回值必須為 類型<xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="52d75-116">A method must be defined by the contract for returning a UI, and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="52d75-117">以下代碼中`GetAddInUI``IWPFAddInContract`的協定方法證明了這一點。</span><span class="sxs-lookup"><span data-stu-id="52d75-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="52d75-118">實作增益集檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="52d75-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="52d75-119">由於外接程式實現它作為 子類<xref:System.Windows.FrameworkElement>提供的 U，因此與 關聯的外接程式視圖上相關的方法`IWPFAddInView.GetAddInUI`必須返回類型 的值。 <xref:System.Windows.FrameworkElement></span><span class="sxs-lookup"><span data-stu-id="52d75-119">Because the add-in implements the UIs it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="52d75-120">下列程式碼顯示合約的增益集檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="52d75-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="52d75-121">實作增益集端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="52d75-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="52d75-122">協定方法返回 一<xref:System.AddIn.Contract.INativeHandleContract>個，但外接程式返回<xref:System.Windows.FrameworkElement>（如外接程式視圖指定）。</span><span class="sxs-lookup"><span data-stu-id="52d75-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="52d75-123">因此，在<xref:System.Windows.FrameworkElement>跨越隔離邊界之前，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換為 。</span><span class="sxs-lookup"><span data-stu-id="52d75-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="52d75-124">此工作由外接程式端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>執行，如以下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="52d75-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="52d75-125">實作主應用程式檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="52d75-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="52d75-126">由於主機應用程式將顯示 一個<xref:System.Windows.FrameworkElement>，因此與 關聯的主機視圖上的方法`IWPFAddInHostView.GetAddInUI`必須返回類型<xref:System.Windows.FrameworkElement>的值。</span><span class="sxs-lookup"><span data-stu-id="52d75-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="52d75-127">下列程式碼顯示合約的主應用程式檢視，並實作為介面。</span><span class="sxs-lookup"><span data-stu-id="52d75-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="52d75-128">實作主應用程式端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="52d75-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="52d75-129">協定方法返回 ，<xref:System.AddIn.Contract.INativeHandleContract>但主機應用程式需要 （<xref:System.Windows.FrameworkElement>由主機視圖指定）。</span><span class="sxs-lookup"><span data-stu-id="52d75-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="52d75-130">因此，在<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離邊界後必須<xref:System.Windows.FrameworkElement>轉換為 。</span><span class="sxs-lookup"><span data-stu-id="52d75-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="52d75-131">此工作由主機端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>執行，如以下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="52d75-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="52d75-132">實作增益集</span><span class="sxs-lookup"><span data-stu-id="52d75-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="52d75-133">在創建`WPFAddIn1.AddIn`外接程式配接器和外接程式視圖後，外接程式 （ ） 必須實現`IWPFAddInView.GetAddInUI`方法才能返回<xref:System.Windows.FrameworkElement>物件（在此示例中為<xref:System.Windows.Controls.UserControl>a）。</span><span class="sxs-lookup"><span data-stu-id="52d75-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="52d75-134">的<xref:System.Windows.Controls.UserControl>`AddInUI`實現由以下代碼顯示。</span><span class="sxs-lookup"><span data-stu-id="52d75-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="52d75-135">`IWPFAddInView.GetAddInUI`通過外接程式實現的只需返回 的新實例`AddInUI`，如下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="52d75-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="52d75-136">實作主應用程式</span><span class="sxs-lookup"><span data-stu-id="52d75-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="52d75-137">創建主機端配接器和主機視圖後，主機應用程式可以使用 .NET Framework 外接程式模型打開管道、獲取外接程式的主機視圖並調用`IWPFAddInHostView.GetAddInUI`方法。</span><span class="sxs-lookup"><span data-stu-id="52d75-137">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="52d75-138">下列程式碼顯示這些步驟。</span><span class="sxs-lookup"><span data-stu-id="52d75-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="52d75-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52d75-139">See also</span></span>

- <span data-ttu-id="52d75-140">[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="52d75-140">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="52d75-141">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="52d75-141">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
