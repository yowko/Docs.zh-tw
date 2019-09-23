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
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182666"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>作法：建立傳回 UI 的增益集
這個範例示範如何建立將 Windows Presentation Foundation （WPF）傳回給主控制項 WPF 獨立應用程式的增益集。  
  
 此增益集會傳回做為 WPF 使用者控制項的 UI。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式會裝載增益集，並顯示使用者控制項（由增益集傳回）做為主應用程式視窗的內容。  
  
 **必要條件**  
  
 這個範例會反白顯示可啟用此案例之 .NET Framework 增益集模型的 WPF 延伸模組，並假設下列各項：  
  
- .NET Framework 增益集模型的知識，包括管線、增益集和主機開發。 如果您不熟悉這些概念，請參閱[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性。 如需示範管線、增益集和主應用程式之執行的教學課程，請參閱[逐步解說：建立可擴充的應用](../../add-ins/walkthrough-create-extensible-app.md)程式。  
  
- .NET Framework 增益集模型的 WPF 延伸模組知識，可以在這裡找到：[WPF 增益集總覽](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立可傳回 WPF UI 的增益集，需要每個管線區段、增益集和主應用程式的特定程式碼。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 方法必須由合約定義以傳回 UI，而且其傳回值必須是類型<xref:System.AddIn.Contract.INativeHandleContract>。 這是由下列程式`GetAddInUI`代碼中的`IWPFAddInContract`合約方法所示範。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 由於增益集[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]會將它當做的<xref:System.Windows.FrameworkElement>子類別來執行，因此，與相關聯之載入`IWPFAddInView.GetAddInUI`宏視圖上的方法必須傳回類型<xref:System.Windows.FrameworkElement>的值。 下列程式碼顯示合約的增益集檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 合約方法<xref:System.AddIn.Contract.INativeHandleContract>會傳回，但增益集<xref:System.Windows.FrameworkElement>會傳回（如 [增益集] 視圖所指定）。 因此， <xref:System.Windows.FrameworkElement>必須<xref:System.AddIn.Contract.INativeHandleContract>先將轉換成，才能跨越隔離界限。 這項工作是由增益集端介面卡藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>來執行，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 因為主應用程式會顯示<xref:System.Windows.FrameworkElement>，所以與`IWPFAddInHostView.GetAddInUI`關聯的主控制項上的方法必須傳回類型<xref:System.Windows.FrameworkElement>的值。 下列程式碼顯示合約的主應用程式檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 合約方法<xref:System.AddIn.Contract.INativeHandleContract>會傳回，但主應用程式會<xref:System.Windows.FrameworkElement>預期（如主機視圖所指定）。 因此， <xref:System.AddIn.Contract.INativeHandleContract>必須在跨越隔離界限<xref:System.Windows.FrameworkElement>之後，將轉換成。 這項工作是由主機端介面卡藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>來執行，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集  
 建立增益集端介面卡和增益集視圖之後，`WPFAddIn1.AddIn`增益集（）必須`IWPFAddInView.GetAddInUI`執行方法，以<xref:System.Windows.FrameworkElement>傳回物件（在此範例中為<xref:System.Windows.Controls.UserControl> ）。 下列程式碼會<xref:System.Windows.Controls.UserControl>顯示`AddInUI`的執行。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 增益集的實`IWPFAddInView.GetAddInUI`作為`AddInUI`，只需要傳回的新實例，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>實作主應用程式  
 建立主機端介面卡和主控制項後，主應用程式可以使用 .NET Framework 增益集模型來開啟管線、取得增益集的主控制項，以及呼叫`IWPFAddInHostView.GetAddInUI`方法。 下列程式碼顯示這些步驟。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
