---
title: 如何：建立本身為 UI 的增益集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141025"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a><span data-ttu-id="c532c-102">如何：建立本身為 UI 的增益集</span><span class="sxs-lookup"><span data-stu-id="c532c-102">How to: Create an Add-In That Is a UI</span></span>
<span data-ttu-id="c532c-103">此示例演示如何創建由 WPF 獨立應用程式託管的 Windows 演示文稿基礎 （WPF） 的外接程式。</span><span class="sxs-lookup"><span data-stu-id="c532c-103">This example shows how to create an add-in that is a Windows Presentation Foundation (WPF) which is hosted by a WPF standalone application.</span></span>  
  
 <span data-ttu-id="c532c-104">外接程式是 WPF 使用者控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="c532c-104">The add-in is a UI that is a WPF user control.</span></span> <span data-ttu-id="c532c-105">此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="c532c-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="c532c-106">WPF 獨立應用程式將外接程式 UI 託管為主應用程式視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="c532c-106">The WPF standalone application hosts the add-in UI as the content of the main application window.</span></span>  
  
 <span data-ttu-id="c532c-107">**必要條件**</span><span class="sxs-lookup"><span data-stu-id="c532c-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="c532c-108">此示例突出顯示啟用此方案的 .NET 框架外接程式模型的 WPF 擴展，並假定以下內容：</span><span class="sxs-lookup"><span data-stu-id="c532c-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="c532c-109">瞭解 .NET 框架外接程式模型，包括管道、外接程式和主機開發。</span><span class="sxs-lookup"><span data-stu-id="c532c-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="c532c-110">如果您不熟悉這些概念，請參閱[載入項和可擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="c532c-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="c532c-111">有關演示管道、外接程式和主機應用程式的實現的教程，請參閱[演練：創建可擴展應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="c532c-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="c532c-112">WPF 擴展到 .NET 框架外接程式模型的知識。</span><span class="sxs-lookup"><span data-stu-id="c532c-112">Knowledge of the WPF extensions to the .NET Framework add-in model.</span></span> <span data-ttu-id="c532c-113">請參閱[WPF 載入項概述](wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c532c-113">See [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c532c-114">範例</span><span class="sxs-lookup"><span data-stu-id="c532c-114">Example</span></span>  
 <span data-ttu-id="c532c-115">要創建一個附加程式，即 WPF UI 需要每個管道段、外接程式和主機應用程式的特定代碼。</span><span class="sxs-lookup"><span data-stu-id="c532c-115">To create an add-in that is a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="c532c-116">實作合約管線區段</span><span class="sxs-lookup"><span data-stu-id="c532c-116">Implementing the Contract Pipeline Segment</span></span>

<span data-ttu-id="c532c-117">當外接程式是 UI 時，外接程式的協定必須實現<xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="c532c-117">When an add-in is a UI, the contract for the add-in must implement <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="c532c-118">在此示例中，`IWPFAddInContract`實現<xref:System.AddIn.Contract.INativeHandleContract>， 如以下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="c532c-118">In the example, `IWPFAddInContract` implements <xref:System.AddIn.Contract.INativeHandleContract>, as shown in the following code.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="c532c-119">實作增益集檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="c532c-119">Implementing the Add-In View Pipeline Segment</span></span>

<span data-ttu-id="c532c-120">由於外接程式是作為<xref:System.Windows.FrameworkElement>類型的子類實現的，因此外接程式視圖還必須子類<xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="c532c-120">Because the add-in is implemented as a subclass of the <xref:System.Windows.FrameworkElement> type, the add-in view must also subclass <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="c532c-121">以下代碼顯示作為`WPFAddInView`類實現的協定的外接程式視圖。</span><span class="sxs-lookup"><span data-stu-id="c532c-121">The following code shows the add-in view of the contract, implemented as the `WPFAddInView` class.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
<span data-ttu-id="c532c-122">此處，外接程式視圖派生自<xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="c532c-122">Here, the add-in view is derived from <xref:System.Windows.Controls.UserControl>.</span></span> <span data-ttu-id="c532c-123">因此，外接程式 UI 也應派生自<xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="c532c-123">Consequently, the add-in UI should also derive from <xref:System.Windows.Controls.UserControl>.</span></span>  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="c532c-124">實作增益集端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="c532c-124">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>

<span data-ttu-id="c532c-125">當協定是 時<xref:System.AddIn.Contract.INativeHandleContract>，外接程式是 （<xref:System.Windows.FrameworkElement>由外接程式視圖管道段指定）。</span><span class="sxs-lookup"><span data-stu-id="c532c-125">While the contract is an <xref:System.AddIn.Contract.INativeHandleContract>, the add-in is a <xref:System.Windows.FrameworkElement> (as specified by the add-in view pipeline segment).</span></span> <span data-ttu-id="c532c-126">因此，在<xref:System.Windows.FrameworkElement>跨越隔離邊界之前，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換為 。</span><span class="sxs-lookup"><span data-stu-id="c532c-126">Therefore, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="c532c-127">此工作由外接程式端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>執行，如以下代碼所示。</span><span class="sxs-lookup"><span data-stu-id="c532c-127">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

<span data-ttu-id="c532c-128">在外接程式返回 UI 的外接程式模型中（請參閱[創建返回 UI 的外接程式](how-to-create-an-add-in-that-returns-a-ui.md)），外接程式配接器<xref:System.Windows.FrameworkElement><xref:System.AddIn.Contract.INativeHandleContract>通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>將 轉換為 。</span><span class="sxs-lookup"><span data-stu-id="c532c-128">In the add-in model where an add-in returns a UI (see [Create an Add-In That Returns a UI](how-to-create-an-add-in-that-returns-a-ui.md)), the add-in adapter converted the <xref:System.Windows.FrameworkElement> to an <xref:System.AddIn.Contract.INativeHandleContract> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.</span></span> <span data-ttu-id="c532c-129"><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>還必須在此模型中調用，儘管您需要實現一個方法，從中編寫代碼來調用它。</span><span class="sxs-lookup"><span data-stu-id="c532c-129"><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> must also be called in this model, although you need to implement a method from which to write the code to call it.</span></span> <span data-ttu-id="c532c-130">通過重寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>和實現調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>的代碼（如果調用<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>的代碼是預期 ） <xref:System.AddIn.Contract.INativeHandleContract></span><span class="sxs-lookup"><span data-stu-id="c532c-130">You do this by overriding <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> and implementing the code that calls <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> if the code that is calling <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> is expecting an <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="c532c-131">在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。</span><span class="sxs-lookup"><span data-stu-id="c532c-131">In this case, the caller will be the host-side adapter, which is covered in a subsequent subsection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c532c-132">您還需要在此模型中重寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>，以便在主機應用程式 UI 和外接程式 UI 之間啟用選項卡。</span><span class="sxs-lookup"><span data-stu-id="c532c-132">You also need to override <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> in this model to enable tabbing between host application UI and add-in UI.</span></span> <span data-ttu-id="c532c-133">有關詳細資訊，請參閱[WPF 外接程式概述中的"WPF](wpf-add-ins-overview.md)外接程式限制"。</span><span class="sxs-lookup"><span data-stu-id="c532c-133">For more information, see "WPF Add-In Limitations" in [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
<span data-ttu-id="c532c-134">由於外接程式配接器實現派生自<xref:System.AddIn.Contract.INativeHandleContract>的介面，因此還需要實現<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，儘管在重寫時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>將忽略這一點。</span><span class="sxs-lookup"><span data-stu-id="c532c-134">Because the add-in-side adapter implements an interface that derives from <xref:System.AddIn.Contract.INativeHandleContract>, you also need to implement <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, although this is ignored when <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> is overridden.</span></span>  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="c532c-135">實作主應用程式檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="c532c-135">Implementing the Host View Pipeline Segment</span></span>

<span data-ttu-id="c532c-136">在此模型中，主機應用程式通常希望主機視圖是<xref:System.Windows.FrameworkElement>子類。</span><span class="sxs-lookup"><span data-stu-id="c532c-136">In this model, the host application typically expects the host view to be a <xref:System.Windows.FrameworkElement> subclass.</span></span> <span data-ttu-id="c532c-137">主機端配接器必須在<xref:System.AddIn.Contract.INativeHandleContract><xref:System.Windows.FrameworkElement><xref:System.AddIn.Contract.INativeHandleContract>跨越隔離邊界後將 轉換為 。</span><span class="sxs-lookup"><span data-stu-id="c532c-137">The host-side adapter must convert the <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> after the <xref:System.AddIn.Contract.INativeHandleContract> crosses the isolation boundary.</span></span> <span data-ttu-id="c532c-138">由於主機應用程式不調用 方法來獲取 ，<xref:System.Windows.FrameworkElement>因此主機視圖必須通過包含它來"返回"。 <xref:System.Windows.FrameworkElement></span><span class="sxs-lookup"><span data-stu-id="c532c-138">Because a method isn't being called by the host application to get the <xref:System.Windows.FrameworkElement>, the host view must "return" the <xref:System.Windows.FrameworkElement> by containing it.</span></span> <span data-ttu-id="c532c-139">因此，主機視圖必須派生自 可以包含其他<xref:System.Windows.FrameworkElement>UI 的子類，如<xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="c532c-139">Consequently, the host view must derive from a subclass of <xref:System.Windows.FrameworkElement> that can contain other UIs, such as <xref:System.Windows.Controls.UserControl>.</span></span> <span data-ttu-id="c532c-140">以下代碼顯示作為類實現的協定的`WPFAddInHostView`主機視圖。</span><span class="sxs-lookup"><span data-stu-id="c532c-140">The following code shows the host view of the contract, implemented as the `WPFAddInHostView` class.</span></span>  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="c532c-141">實作主應用程式端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="c532c-141">Implementing the Host-Side Adapter Pipeline Segment</span></span>

<span data-ttu-id="c532c-142">當協定是 時<xref:System.AddIn.Contract.INativeHandleContract>，主機應用程式需要 （<xref:System.Windows.Controls.UserControl>如主機視圖指定）。</span><span class="sxs-lookup"><span data-stu-id="c532c-142">While the contract is an <xref:System.AddIn.Contract.INativeHandleContract>, the host application expects a <xref:System.Windows.Controls.UserControl> (as specified by the host view).</span></span> <span data-ttu-id="c532c-143">因此，<xref:System.AddIn.Contract.INativeHandleContract>在跨越隔離邊界之前<xref:System.Windows.FrameworkElement><xref:System.Windows.Controls.UserControl>，必須將 轉換為 。</span><span class="sxs-lookup"><span data-stu-id="c532c-143">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary, before being set as content of the host view (which derives from <xref:System.Windows.Controls.UserControl>).</span></span>  
  
<span data-ttu-id="c532c-144">這項工作是由主應用程式端配接器所執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c532c-144">This work is performed by the host-side adapter, as shown in the following code.</span></span>  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

<span data-ttu-id="c532c-145">如您所見，主機端配接器<xref:System.AddIn.Contract.INativeHandleContract>通過調用外接程式端配接器<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>的方法獲取 獲取 （這是跨越<xref:System.AddIn.Contract.INativeHandleContract>隔離邊界的點）。</span><span class="sxs-lookup"><span data-stu-id="c532c-145">As you can see, the host-side adapter acquires the <xref:System.AddIn.Contract.INativeHandleContract> by calling the add-in-side adapter's <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> method (this is the point where the <xref:System.AddIn.Contract.INativeHandleContract> crosses the isolation boundary).</span></span>  
  
<span data-ttu-id="c532c-146">然後，主機端配接器通過調用<xref:System.AddIn.Contract.INativeHandleContract><xref:System.Windows.FrameworkElement><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>將 轉換為 。</span><span class="sxs-lookup"><span data-stu-id="c532c-146">The host-side adapter then converts the <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.</span></span> <span data-ttu-id="c532c-147">最後，<xref:System.Windows.FrameworkElement>將 設置為主機視圖的內容。</span><span class="sxs-lookup"><span data-stu-id="c532c-147">Finally, the <xref:System.Windows.FrameworkElement> is set as the content of the host view.</span></span>  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a><span data-ttu-id="c532c-148">實作增益集</span><span class="sxs-lookup"><span data-stu-id="c532c-148">Implementing the Add-In</span></span>

<span data-ttu-id="c532c-149">增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c532c-149">With the add-in-side adapter and add-in view in place, the add-in can be implemented by deriving from the add-in view, as shown in the following code.</span></span>  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

<span data-ttu-id="c532c-150">在此示例中，您可以看到此模型的一個有趣好處：外接程式開發人員只需要實現外接程式（因為它也是 UI），而不是外接程式類和外接程式 UI。</span><span class="sxs-lookup"><span data-stu-id="c532c-150">From this example, you can see one interesting benefit of this model: add-in developers only need to implement the add-in (since it is the UI as well), rather than both an add-in class and an add-in UI.</span></span>  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="c532c-151">實作主應用程式</span><span class="sxs-lookup"><span data-stu-id="c532c-151">Implementing the Host Application</span></span>

<span data-ttu-id="c532c-152">創建主機端配接器和主機視圖後，主機應用程式可以使用 .NET 框架外接程式模型打開管道並獲取外接程式的主機視圖。</span><span class="sxs-lookup"><span data-stu-id="c532c-152">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline and acquire a host view of the add-in.</span></span> <span data-ttu-id="c532c-153">下列程式碼顯示這些步驟。</span><span class="sxs-lookup"><span data-stu-id="c532c-153">These steps are shown in the following code.</span></span>  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

<span data-ttu-id="c532c-154">主機應用程式使用典型的 .NET Framework 外接程式模型代碼來啟動外接程式，該載入項隱式地將主機視圖返回到主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="c532c-154">The host application uses typical .NET Framework add-in model code to activate the add-in, which implicitly returns the host view to the host application.</span></span> <span data-ttu-id="c532c-155">主機應用程式隨後顯示 中的主機視圖 （這是<xref:System.Windows.Controls.UserControl>a ） <xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="c532c-155">The host application subsequently displays the host view (which is a <xref:System.Windows.Controls.UserControl>) from a <xref:System.Windows.Controls.Grid>.</span></span>  
  
 <span data-ttu-id="c532c-156">處理與外接程式 UI 交互的代碼在外接程式的應用程式域中運行。</span><span class="sxs-lookup"><span data-stu-id="c532c-156">The code for processing interactions with the add-in UI runs in the add-in's application domain.</span></span> <span data-ttu-id="c532c-157">這些互動包括：</span><span class="sxs-lookup"><span data-stu-id="c532c-157">These interactions include the following:</span></span>  
  
- <span data-ttu-id="c532c-158">處理<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="c532c-158">Handling the <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
- <span data-ttu-id="c532c-159">顯示<xref:System.Windows.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="c532c-159">Showing the <xref:System.Windows.MessageBox>.</span></span>  
  
 <span data-ttu-id="c532c-160">此活動完全與主應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="c532c-160">This activity is completely isolated from the host application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c532c-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c532c-161">See also</span></span>

- <span data-ttu-id="c532c-162">[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="c532c-162">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="c532c-163">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="c532c-163">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
