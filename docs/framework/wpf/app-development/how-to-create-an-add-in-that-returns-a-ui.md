---
title: HOW TO：建立傳回 UI 的增益集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947832"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>HOW TO：建立傳回 UI 的增益集
此範例示範如何建立 Windows Presentation Foundation (WPF) 傳回至主機的 WPF 獨立應用程式。  
  
 增益集傳回 UI 的 WPF 使用者控制項。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式裝載增益集，並顯示主應用程式視窗的內容 （增益集所傳回） 的使用者控制項。  
  
 **必要條件**  
  
 此範例會反白顯示 啟用此案例中，WPF 擴充功能至.NET Framework 增益集模型，並假設如下：  
  
- .NET Framework 增益集模型，包括管線、 增益集和主應用程式開發的知識。 如果您不熟悉這些概念，請參閱[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 如需示範管線、 增益集，和主應用程式的實作的教學課程，請參閱[逐步解說：建立可延伸應用程式](../../add-ins/walkthrough-create-extensible-app.md)。  
  
- 了解 WPF 擴充功能，在.NET Framework 增益集模型，可以在這裡找到：[WPF 增益集概觀](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立傳回 WPF UI 的增益集需要特定的程式碼的每個管線區段、 增益集，和主應用程式。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 必須傳回 UI 的合約所定義的方法和它的傳回值必須是型別的<xref:System.AddIn.Contract.INativeHandleContract>。 最好的證明`GetAddInUI`方法的`IWPFAddInContract`合約中的下列程式碼。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 因為增益集實作[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]它會提供為的子類別<xref:System.Windows.FrameworkElement>，與相互關聯的增益集檢視上的方法`IWPFAddInView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。 下列程式碼顯示合約的增益集檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但增益集傳回<xref:System.Windows.FrameworkElement>（如同增益集檢視所指定）。 因此，<xref:System.Windows.FrameworkElement>必須轉換成<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限之前。 這項工作藉由呼叫增益集端配接器執行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 因為主應用程式會顯示<xref:System.Windows.FrameworkElement>，與相關聯的 [主機] 檢視上的方法`IWPFAddInHostView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。 下列程式碼顯示合約的主應用程式檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但主應用程式預期<xref:System.Windows.FrameworkElement>（如同 [主機] 檢視所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換成<xref:System.Windows.FrameworkElement>跨越隔離界限之後。 這項工作的執行是由主應用程式端配接器藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集  
 增益集端配接器和增益集建立檢視，增益集 (`WPFAddIn1.AddIn`) 必須實作`IWPFAddInView.GetAddInUI`方法，以傳回<xref:System.Windows.FrameworkElement>物件 (<xref:System.Windows.Controls.UserControl>在此範例中)。 實作<xref:System.Windows.Controls.UserControl>， `AddInUI`，下列程式碼會顯示。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 實作`IWPFAddInView.GetAddInUI`增益集只需要傳回的新執行個體`AddInUI`，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>實作主應用程式  
 主應用程式端配接器和建立的 [主機] 檢視中，主應用程式可以使用.NET Framework 增益集模型開啟管線、 取得增益集，並呼叫主應用程式檢視`IWPFAddInHostView.GetAddInUI`方法。 下列程式碼顯示這些步驟。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
