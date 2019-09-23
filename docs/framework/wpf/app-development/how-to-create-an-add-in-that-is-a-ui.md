---
title: 作法：建立本身為 UI 的增益集
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
ms.openlocfilehash: b0e847061a30e93d36997ab603c52715e2730765
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182647"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a><span data-ttu-id="6e76a-102">作法：建立本身為 UI 的增益集</span><span class="sxs-lookup"><span data-stu-id="6e76a-102">How to: Create an Add-In That Is a UI</span></span>
<span data-ttu-id="6e76a-103">這個範例示範如何建立增益集，這是 WPF 獨立應用程式所裝載的 Windows Presentation Foundation （WPF）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-103">This example shows how to create an add-in that is a Windows Presentation Foundation (WPF) which is hosted by a WPF standalone application.</span></span>  
  
 <span data-ttu-id="6e76a-104">此增益集是 WPF 使用者控制項的 UI。</span><span class="sxs-lookup"><span data-stu-id="6e76a-104">The add-in is a UI that is a WPF user control.</span></span> <span data-ttu-id="6e76a-105">此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="6e76a-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="6e76a-106">WPF 獨立應用程式會將增益集 UI 裝載為主應用程式視窗的內容。</span><span class="sxs-lookup"><span data-stu-id="6e76a-106">The WPF standalone application hosts the add-in UI as the content of the main application window.</span></span>  
  
 <span data-ttu-id="6e76a-107">**必要條件**</span><span class="sxs-lookup"><span data-stu-id="6e76a-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="6e76a-108">這個範例會反白顯示可啟用此案例之 .NET Framework 增益集模型的 WPF 延伸模組，並假設下列各項：</span><span class="sxs-lookup"><span data-stu-id="6e76a-108">This example highlights the WPF extensions to the .NET Framework add-in model that enable this scenario, and assumes the following:</span></span>  
  
- <span data-ttu-id="6e76a-109">.NET Framework 增益集模型的知識，包括管線、增益集和主機開發。</span><span class="sxs-lookup"><span data-stu-id="6e76a-109">Knowledge of the .NET Framework add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="6e76a-110">如果您不熟悉這些概念，請參閱[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性。</span><span class="sxs-lookup"><span data-stu-id="6e76a-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span> <span data-ttu-id="6e76a-111">如需示範管線、增益集和主應用程式之執行的教學課程，請參閱[逐步解說：建立可擴充的應用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))程式。</span><span class="sxs-lookup"><span data-stu-id="6e76a-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).</span></span>  
  
- <span data-ttu-id="6e76a-112">.NET Framework 增益集模型的 WPF 延伸模組知識。</span><span class="sxs-lookup"><span data-stu-id="6e76a-112">Knowledge of the WPF extensions to the .NET Framework add-in model.</span></span> <span data-ttu-id="6e76a-113">請參閱[WPF 增益集總覽](wpf-add-ins-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6e76a-113">See [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e76a-114">範例</span><span class="sxs-lookup"><span data-stu-id="6e76a-114">Example</span></span>  
 <span data-ttu-id="6e76a-115">若要建立 WPF UI 的增益集，需要每個管線區段、增益集和主應用程式的特定程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e76a-115">To create an add-in that is a WPF UI requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="6e76a-116">實作合約管線區段</span><span class="sxs-lookup"><span data-stu-id="6e76a-116">Implementing the Contract Pipeline Segment</span></span>

<span data-ttu-id="6e76a-117">當增益集是 UI 時，增益集的合約必須執行<xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="6e76a-117">When an add-in is a UI, the contract for the add-in must implement <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="6e76a-118">在範例中， `IWPFAddInContract` <xref:System.AddIn.Contract.INativeHandleContract>會執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6e76a-118">In the example, `IWPFAddInContract` implements <xref:System.AddIn.Contract.INativeHandleContract>, as shown in the following code.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="6e76a-119">實作增益集檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="6e76a-119">Implementing the Add-In View Pipeline Segment</span></span>

<span data-ttu-id="6e76a-120">因為增益集會實作為<xref:System.Windows.FrameworkElement>類型的子類別，所以增益集的視圖也必須子類別<xref:System.Windows.FrameworkElement>化。</span><span class="sxs-lookup"><span data-stu-id="6e76a-120">Because the add-in is implemented as a subclass of the <xref:System.Windows.FrameworkElement> type, the add-in view must also subclass <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="6e76a-121">下列程式碼顯示合約的增益集視圖，並實作為`WPFAddInView`類別。</span><span class="sxs-lookup"><span data-stu-id="6e76a-121">The following code shows the add-in view of the contract, implemented as the `WPFAddInView` class.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
<span data-ttu-id="6e76a-122">在這裡，增益集視圖衍生自<xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="6e76a-122">Here, the add-in view is derived from <xref:System.Windows.Controls.UserControl>.</span></span> <span data-ttu-id="6e76a-123">因此，增益集 UI 也應該衍生自<xref:System.Windows.Controls.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="6e76a-123">Consequently, the add-in UI should also derive from <xref:System.Windows.Controls.UserControl>.</span></span>  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="6e76a-124">實作增益集端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="6e76a-124">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>

<span data-ttu-id="6e76a-125">當合約是<xref:System.AddIn.Contract.INativeHandleContract>時，增益集<xref:System.Windows.FrameworkElement>會是（如增益集視圖管線區段所指定）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-125">While the contract is an <xref:System.AddIn.Contract.INativeHandleContract>, the add-in is a <xref:System.Windows.FrameworkElement> (as specified by the add-in view pipeline segment).</span></span> <span data-ttu-id="6e76a-126">因此， <xref:System.Windows.FrameworkElement>必須<xref:System.AddIn.Contract.INativeHandleContract>先將轉換成，才能跨越隔離界限。</span><span class="sxs-lookup"><span data-stu-id="6e76a-126">Therefore, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="6e76a-127">這項工作是由增益集端介面卡藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>來執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6e76a-127">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

<span data-ttu-id="6e76a-128">在增益集模型中，增益集會在其中傳回 ui （請參閱[建立可傳回 ui 的增益集](how-to-create-an-add-in-that-returns-a-ui.md)），增益集介面卡會<xref:System.Windows.FrameworkElement>藉<xref:System.AddIn.Contract.INativeHandleContract>由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>將轉換成。</span><span class="sxs-lookup"><span data-stu-id="6e76a-128">In the add-in model where an add-in returns a UI (see [Create an Add-In That Returns a UI](how-to-create-an-add-in-that-returns-a-ui.md)), the add-in adapter converted the <xref:System.Windows.FrameworkElement> to an <xref:System.AddIn.Contract.INativeHandleContract> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.</span></span> <span data-ttu-id="6e76a-129"><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>您也必須在此模型中呼叫，雖然您需要執行方法，以從中撰寫程式碼來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="6e76a-129"><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> must also be called in this model, although you need to implement a method from which to write the code to call it.</span></span> <span data-ttu-id="6e76a-130">若要這麼做， <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>您可以覆寫並執行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>呼叫的程式碼（如果<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>呼叫的程式<xref:System.AddIn.Contract.INativeHandleContract>代碼需要）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-130">You do this by overriding <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> and implementing the code that calls <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> if the code that is calling <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> is expecting an <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="6e76a-131">在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。</span><span class="sxs-lookup"><span data-stu-id="6e76a-131">In this case, the caller will be the host-side adapter, which is covered in a subsequent subsection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e76a-132">您也需要在此<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>模型中覆寫，以啟用主應用程式 ui 和增益集 ui 之間的 tab 鍵。</span><span class="sxs-lookup"><span data-stu-id="6e76a-132">You also need to override <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> in this model to enable tabbing between host application UI and add-in UI.</span></span> <span data-ttu-id="6e76a-133">如需詳細資訊，請參閱[Wpf 增益集總覽](wpf-add-ins-overview.md)中的「wpf 增益集限制」。</span><span class="sxs-lookup"><span data-stu-id="6e76a-133">For more information, see "WPF Add-In Limitations" in [WPF Add-Ins Overview](wpf-add-ins-overview.md).</span></span>  
  
<span data-ttu-id="6e76a-134">由於增益集端介面卡會實作為衍生自<xref:System.AddIn.Contract.INativeHandleContract>的介面，因此您也需要執行<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，不過當覆寫時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> ，會忽略此項。</span><span class="sxs-lookup"><span data-stu-id="6e76a-134">Because the add-in-side adapter implements an interface that derives from <xref:System.AddIn.Contract.INativeHandleContract>, you also need to implement <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, although this is ignored when <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> is overridden.</span></span>  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="6e76a-135">實作主應用程式檢視管線區段</span><span class="sxs-lookup"><span data-stu-id="6e76a-135">Implementing the Host View Pipeline Segment</span></span>

<span data-ttu-id="6e76a-136">在此模型中，主應用程式通常會預期主控制項為子<xref:System.Windows.FrameworkElement>類別。</span><span class="sxs-lookup"><span data-stu-id="6e76a-136">In this model, the host application typically expects the host view to be a <xref:System.Windows.FrameworkElement> subclass.</span></span> <span data-ttu-id="6e76a-137">主機端介面卡必須在<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限<xref:System.Windows.FrameworkElement>之後，將轉換成。</span><span class="sxs-lookup"><span data-stu-id="6e76a-137">The host-side adapter must convert the <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> after the <xref:System.AddIn.Contract.INativeHandleContract> crosses the isolation boundary.</span></span> <span data-ttu-id="6e76a-138">因為主應用程式不會呼叫方法來取得<xref:System.Windows.FrameworkElement>，所以主機視圖必須藉<xref:System.Windows.FrameworkElement>由包含它來 "return"。</span><span class="sxs-lookup"><span data-stu-id="6e76a-138">Because a method isn't being called by the host application to get the <xref:System.Windows.FrameworkElement>, the host view must "return" the <xref:System.Windows.FrameworkElement> by containing it.</span></span> <span data-ttu-id="6e76a-139">因此，主機視圖必須衍生自可以包含其他 ui <xref:System.Windows.FrameworkElement> （ <xref:System.Windows.Controls.UserControl>例如）的子類別。</span><span class="sxs-lookup"><span data-stu-id="6e76a-139">Consequently, the host view must derive from a subclass of <xref:System.Windows.FrameworkElement> that can contain other UIs, such as <xref:System.Windows.Controls.UserControl>.</span></span> <span data-ttu-id="6e76a-140">下列程式碼顯示合約的主視圖，實作為`WPFAddInHostView`類別。</span><span class="sxs-lookup"><span data-stu-id="6e76a-140">The following code shows the host view of the contract, implemented as the `WPFAddInHostView` class.</span></span>  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="6e76a-141">實作主應用程式端配接器管線區段</span><span class="sxs-lookup"><span data-stu-id="6e76a-141">Implementing the Host-Side Adapter Pipeline Segment</span></span>

<span data-ttu-id="6e76a-142">當合約為時<xref:System.AddIn.Contract.INativeHandleContract>，主應用程式會<xref:System.Windows.Controls.UserControl>預期（如主機視圖所指定）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-142">While the contract is an <xref:System.AddIn.Contract.INativeHandleContract>, the host application expects a <xref:System.Windows.Controls.UserControl> (as specified by the host view).</span></span> <span data-ttu-id="6e76a-143">因此， <xref:System.AddIn.Contract.INativeHandleContract>必須在跨越隔離界限<xref:System.Windows.FrameworkElement>之後轉換成，再將設定為主控制項的內容（衍生自<xref:System.Windows.Controls.UserControl>）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-143">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary, before being set as content of the host view (which derives from <xref:System.Windows.Controls.UserControl>).</span></span>  
  
<span data-ttu-id="6e76a-144">這項工作是由主應用程式端配接器所執行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6e76a-144">This work is performed by the host-side adapter, as shown in the following code.</span></span>  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

<span data-ttu-id="6e76a-145">如您所見，主機端介面卡<xref:System.AddIn.Contract.INativeHandleContract>會藉由呼叫增益集端介面卡的<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>方法（這<xref:System.AddIn.Contract.INativeHandleContract>是跨越隔離界限的點）來取得。</span><span class="sxs-lookup"><span data-stu-id="6e76a-145">As you can see, the host-side adapter acquires the <xref:System.AddIn.Contract.INativeHandleContract> by calling the add-in-side adapter's <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> method (this is the point where the <xref:System.AddIn.Contract.INativeHandleContract> crosses the isolation boundary).</span></span>  
  
<span data-ttu-id="6e76a-146">然後，主機端介面卡會藉<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement>由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，將轉換成。</span><span class="sxs-lookup"><span data-stu-id="6e76a-146">The host-side adapter then converts the <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.</span></span> <span data-ttu-id="6e76a-147">最後， <xref:System.Windows.FrameworkElement>會設定為主視圖的內容。</span><span class="sxs-lookup"><span data-stu-id="6e76a-147">Finally, the <xref:System.Windows.FrameworkElement> is set as the content of the host view.</span></span>  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="6e76a-148">實作增益集</span><span class="sxs-lookup"><span data-stu-id="6e76a-148">Implementing the Add-In</span></span>

<span data-ttu-id="6e76a-149">增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6e76a-149">With the add-in-side adapter and add-in view in place, the add-in can be implemented by deriving from the add-in view, as shown in the following code.</span></span>  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

<span data-ttu-id="6e76a-150">從這個範例中，您可以看到此模型有一個有趣的優點：增益集開發人員只需要執行增益集（因為它也是 UI），而不是增益集類別和增益集 UI。</span><span class="sxs-lookup"><span data-stu-id="6e76a-150">From this example, you can see one interesting benefit of this model: add-in developers only need to implement the add-in (since it is the UI as well), rather than both an add-in class and an add-in UI.</span></span>  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a><span data-ttu-id="6e76a-151">實作主應用程式</span><span class="sxs-lookup"><span data-stu-id="6e76a-151">Implementing the Host Application</span></span>

<span data-ttu-id="6e76a-152">建立主機端介面卡和主控制項時，主應用程式可以使用 .NET Framework 的增益集模型來開啟管線，並取得增益集的主視圖。</span><span class="sxs-lookup"><span data-stu-id="6e76a-152">With the host-side adapter and host view created, the host application can use the .NET Framework add-in model to open the pipeline and acquire a host view of the add-in.</span></span> <span data-ttu-id="6e76a-153">下列程式碼顯示這些步驟。</span><span class="sxs-lookup"><span data-stu-id="6e76a-153">These steps are shown in the following code.</span></span>  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

<span data-ttu-id="6e76a-154">主應用程式會使用一般 .NET Framework 增益集模型程式碼來啟動增益集，這會以隱含方式將主控制項傳回給主應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e76a-154">The host application uses typical .NET Framework add-in model code to activate the add-in, which implicitly returns the host view to the host application.</span></span> <span data-ttu-id="6e76a-155">然後，主應用程式會<xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Grid>從中顯示主機視圖（這是）。</span><span class="sxs-lookup"><span data-stu-id="6e76a-155">The host application subsequently displays the host view (which is a <xref:System.Windows.Controls.UserControl>) from a <xref:System.Windows.Controls.Grid>.</span></span>  
  
 <span data-ttu-id="6e76a-156">處理與增益集 UI 互動的程式碼會在增益集的應用程式域中執行。</span><span class="sxs-lookup"><span data-stu-id="6e76a-156">The code for processing interactions with the add-in UI runs in the add-in's application domain.</span></span> <span data-ttu-id="6e76a-157">這些互動包括：</span><span class="sxs-lookup"><span data-stu-id="6e76a-157">These interactions include the following:</span></span>  
  
- <span data-ttu-id="6e76a-158"><xref:System.Windows.Controls.Button> 處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="6e76a-158">Handling the <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
- <span data-ttu-id="6e76a-159"><xref:System.Windows.MessageBox>顯示。</span><span class="sxs-lookup"><span data-stu-id="6e76a-159">Showing the <xref:System.Windows.MessageBox>.</span></span>  
  
 <span data-ttu-id="6e76a-160">此活動完全與主應用程式隔離。</span><span class="sxs-lookup"><span data-stu-id="6e76a-160">This activity is completely isolated from the host application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e76a-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e76a-161">See also</span></span>

- <span data-ttu-id="6e76a-162">[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="6e76a-162">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="6e76a-163">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="6e76a-163">WPF Add-Ins Overview</span></span>](wpf-add-ins-overview.md)
