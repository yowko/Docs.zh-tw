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
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>作法：建立本身為 UI 的增益集
這個範例示範如何建立增益集，這是 WPF 獨立應用程式所裝載的 Windows Presentation Foundation （WPF）。  
  
 此增益集是 WPF 使用者控制項的 UI。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式會將增益集 UI 裝載為主應用程式視窗的內容。  
  
 **必要條件**  
  
 這個範例會反白顯示可啟用此案例之 .NET Framework 增益集模型的 WPF 延伸模組，並假設下列各項：  
  
- .NET Framework 增益集模型的知識，包括管線、增益集和主機開發。 如果您不熟悉這些概念，請參閱[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性。 如需示範管線、增益集和主應用程式之執行的教學課程，請參閱[逐步解說：建立可擴充的應用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))程式。  
  
- .NET Framework 增益集模型的 WPF 延伸模組知識。 請參閱[WPF 增益集總覽](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立 WPF UI 的增益集，需要每個管線區段、增益集和主應用程式的特定程式碼。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段

當增益集是 UI 時，增益集的合約必須執行<xref:System.AddIn.Contract.INativeHandleContract>。 在範例中， `IWPFAddInContract` <xref:System.AddIn.Contract.INativeHandleContract>會執行，如下列程式碼所示。  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段

因為增益集會實作為<xref:System.Windows.FrameworkElement>類型的子類別，所以增益集的視圖也必須子類別<xref:System.Windows.FrameworkElement>化。 下列程式碼顯示合約的增益集視圖，並實作為`WPFAddInView`類別。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
在這裡，增益集視圖衍生自<xref:System.Windows.Controls.UserControl>。 因此，增益集 UI 也應該衍生自<xref:System.Windows.Controls.UserControl>。  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段

當合約是<xref:System.AddIn.Contract.INativeHandleContract>時，增益集<xref:System.Windows.FrameworkElement>會是（如增益集視圖管線區段所指定）。 因此， <xref:System.Windows.FrameworkElement>必須<xref:System.AddIn.Contract.INativeHandleContract>先將轉換成，才能跨越隔離界限。 這項工作是由增益集端介面卡藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>來執行，如下列程式碼所示。  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

在增益集模型中，增益集會在其中傳回 ui （請參閱[建立可傳回 ui 的增益集](how-to-create-an-add-in-that-returns-a-ui.md)），增益集介面卡會<xref:System.Windows.FrameworkElement>藉<xref:System.AddIn.Contract.INativeHandleContract>由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>將轉換成。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>您也必須在此模型中呼叫，雖然您需要執行方法，以從中撰寫程式碼來呼叫它。 若要這麼做， <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>您可以覆寫並執行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>呼叫的程式碼（如果<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>呼叫的程式<xref:System.AddIn.Contract.INativeHandleContract>代碼需要）。 在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。  
  
> [!NOTE]
> 您也需要在此<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>模型中覆寫，以啟用主應用程式 ui 和增益集 ui 之間的 tab 鍵。 如需詳細資訊，請參閱[Wpf 增益集總覽](wpf-add-ins-overview.md)中的「wpf 增益集限制」。  
  
由於增益集端介面卡會實作為衍生自<xref:System.AddIn.Contract.INativeHandleContract>的介面，因此您也需要執行<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，不過當覆寫時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> ，會忽略此項。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段

在此模型中，主應用程式通常會預期主控制項為子<xref:System.Windows.FrameworkElement>類別。 主機端介面卡必須在<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限<xref:System.Windows.FrameworkElement>之後，將轉換成。 因為主應用程式不會呼叫方法來取得<xref:System.Windows.FrameworkElement>，所以主機視圖必須藉<xref:System.Windows.FrameworkElement>由包含它來 "return"。 因此，主機視圖必須衍生自可以包含其他 ui <xref:System.Windows.FrameworkElement> （ <xref:System.Windows.Controls.UserControl>例如）的子類別。 下列程式碼顯示合約的主視圖，實作為`WPFAddInHostView`類別。  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段

當合約為時<xref:System.AddIn.Contract.INativeHandleContract>，主應用程式會<xref:System.Windows.Controls.UserControl>預期（如主機視圖所指定）。 因此， <xref:System.AddIn.Contract.INativeHandleContract>必須在跨越隔離界限<xref:System.Windows.FrameworkElement>之後轉換成，再將設定為主控制項的內容（衍生自<xref:System.Windows.Controls.UserControl>）。  
  
這項工作是由主應用程式端配接器所執行，如下列程式碼所示。  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

如您所見，主機端介面卡<xref:System.AddIn.Contract.INativeHandleContract>會藉由呼叫增益集端介面卡的<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>方法（這<xref:System.AddIn.Contract.INativeHandleContract>是跨越隔離界限的點）來取得。  
  
然後，主機端介面卡會藉<xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement>由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，將轉換成。 最後， <xref:System.Windows.FrameworkElement>會設定為主視圖的內容。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集

增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

從這個範例中，您可以看到此模型有一個有趣的優點：增益集開發人員只需要執行增益集（因為它也是 UI），而不是增益集類別和增益集 UI。  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>實作主應用程式

建立主機端介面卡和主控制項時，主應用程式可以使用 .NET Framework 的增益集模型來開啟管線，並取得增益集的主視圖。 下列程式碼顯示這些步驟。  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

主應用程式會使用一般 .NET Framework 增益集模型程式碼來啟動增益集，這會以隱含方式將主控制項傳回給主應用程式。 然後，主應用程式會<xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Grid>從中顯示主機視圖（這是）。  
  
 處理與增益集 UI 互動的程式碼會在增益集的應用程式域中執行。 這些互動包括：  
  
- <xref:System.Windows.Controls.Button> 處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
- <xref:System.Windows.MessageBox>顯示。  
  
 此活動完全與主應用程式隔離。  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
