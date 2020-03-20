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
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>如何：建立本身為 UI 的增益集
此示例演示如何創建由 WPF 獨立應用程式託管的 Windows 演示文稿基礎 （WPF） 的外接程式。  
  
 外接程式是 WPF 使用者控制項的 UI。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式將外接程式 UI 託管為主應用程式視窗的內容。  
  
 **必要條件**  
  
 此示例突出顯示啟用此方案的 .NET 框架外接程式模型的 WPF 擴展，並假定以下內容：  
  
- 瞭解 .NET 框架外接程式模型，包括管道、外接程式和主機開發。 如果您不熟悉這些概念，請參閱[載入項和可擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 有關演示管道、外接程式和主機應用程式的實現的教程，請參閱[演練：創建可擴展應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。  
  
- WPF 擴展到 .NET 框架外接程式模型的知識。 請參閱[WPF 載入項概述](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 要創建一個附加程式，即 WPF UI 需要每個管道段、外接程式和主機應用程式的特定代碼。  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段

當外接程式是 UI 時，外接程式的協定必須實現<xref:System.AddIn.Contract.INativeHandleContract>。 在此示例中，`IWPFAddInContract`實現<xref:System.AddIn.Contract.INativeHandleContract>， 如以下代碼所示。  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段

由於外接程式是作為<xref:System.Windows.FrameworkElement>類型的子類實現的，因此外接程式視圖還必須子類<xref:System.Windows.FrameworkElement>。 以下代碼顯示作為`WPFAddInView`類實現的協定的外接程式視圖。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
此處，外接程式視圖派生自<xref:System.Windows.Controls.UserControl>。 因此，外接程式 UI 也應派生自<xref:System.Windows.Controls.UserControl>。  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段

當協定是 時<xref:System.AddIn.Contract.INativeHandleContract>，外接程式是 （<xref:System.Windows.FrameworkElement>由外接程式視圖管道段指定）。 因此，在<xref:System.Windows.FrameworkElement>跨越隔離邊界之前，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換為 。 此工作由外接程式端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>執行，如以下代碼所示。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

在外接程式返回 UI 的外接程式模型中（請參閱[創建返回 UI 的外接程式](how-to-create-an-add-in-that-returns-a-ui.md)），外接程式配接器<xref:System.Windows.FrameworkElement><xref:System.AddIn.Contract.INativeHandleContract>通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>將 轉換為 。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>還必須在此模型中調用，儘管您需要實現一個方法，從中編寫代碼來調用它。 通過重寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>和實現調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>的代碼（如果調用<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>的代碼是預期 ） <xref:System.AddIn.Contract.INativeHandleContract> 在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。  
  
> [!NOTE]
> 您還需要在此模型中重寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>，以便在主機應用程式 UI 和外接程式 UI 之間啟用選項卡。 有關詳細資訊，請參閱[WPF 外接程式概述中的"WPF](wpf-add-ins-overview.md)外接程式限制"。  
  
由於外接程式配接器實現派生自<xref:System.AddIn.Contract.INativeHandleContract>的介面，因此還需要實現<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，儘管在重寫時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>將忽略這一點。  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段

在此模型中，主機應用程式通常希望主機視圖是<xref:System.Windows.FrameworkElement>子類。 主機端配接器必須在<xref:System.AddIn.Contract.INativeHandleContract><xref:System.Windows.FrameworkElement><xref:System.AddIn.Contract.INativeHandleContract>跨越隔離邊界後將 轉換為 。 由於主機應用程式不調用 方法來獲取 ，<xref:System.Windows.FrameworkElement>因此主機視圖必須通過包含它來"返回"。 <xref:System.Windows.FrameworkElement> 因此，主機視圖必須派生自 可以包含其他<xref:System.Windows.FrameworkElement>UI 的子類，如<xref:System.Windows.Controls.UserControl>。 以下代碼顯示作為類實現的協定的`WPFAddInHostView`主機視圖。  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段

當協定是 時<xref:System.AddIn.Contract.INativeHandleContract>，主機應用程式需要 （<xref:System.Windows.Controls.UserControl>如主機視圖指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>在跨越隔離邊界之前<xref:System.Windows.FrameworkElement><xref:System.Windows.Controls.UserControl>，必須將 轉換為 。  
  
這項工作是由主應用程式端配接器所執行，如下列程式碼所示。  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

如您所見，主機端配接器<xref:System.AddIn.Contract.INativeHandleContract>通過調用外接程式端配接器<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>的方法獲取 獲取 （這是跨越<xref:System.AddIn.Contract.INativeHandleContract>隔離邊界的點）。  
  
然後，主機端配接器通過調用<xref:System.AddIn.Contract.INativeHandleContract><xref:System.Windows.FrameworkElement><xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>將 轉換為 。 最後，<xref:System.Windows.FrameworkElement>將 設置為主機視圖的內容。  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>實作增益集

增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

在此示例中，您可以看到此模型的一個有趣好處：外接程式開發人員只需要實現外接程式（因為它也是 UI），而不是外接程式類和外接程式 UI。  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>實作主應用程式

創建主機端配接器和主機視圖後，主機應用程式可以使用 .NET 框架外接程式模型打開管道並獲取外接程式的主機視圖。 下列程式碼顯示這些步驟。  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

主機應用程式使用典型的 .NET Framework 外接程式模型代碼來啟動外接程式，該載入項隱式地將主機視圖返回到主機應用程式。 主機應用程式隨後顯示 中的主機視圖 （這是<xref:System.Windows.Controls.UserControl>a ） <xref:System.Windows.Controls.Grid>。  
  
 處理與外接程式 UI 交互的代碼在外接程式的應用程式域中運行。 這些互動包括：  
  
- 處理<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
- 顯示<xref:System.Windows.MessageBox>。  
  
 此活動完全與主應用程式隔離。  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
