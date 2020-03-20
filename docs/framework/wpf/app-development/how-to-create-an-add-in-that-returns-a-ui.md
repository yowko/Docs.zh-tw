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
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>如何：建立傳回 UI 的增益集
此示例演示如何創建將 Windows 演示文稿基礎 （WPF） 返回到主機 WPF 獨立應用程式的外接程式。  
  
 外接程式返回作為 WPF 使用者控制項的 UI。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式承載外接程式，並將使用者控制項（由外接程式返回）顯示為主應用程式視窗的內容。  
  
 **必要條件**  
  
 此示例突出顯示啟用此方案的 .NET 框架外接程式模型的 WPF 擴展，並假定以下內容：  
  
- 瞭解 .NET 框架外接程式模型，包括管道、外接程式和主機開發。 如果您不熟悉這些概念，請參閱[載入項和可擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 有關演示管道、外接程式和主機應用程式的實現的教程，請參閱[演練：創建可擴展應用程式](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。  
  
- WPF 擴展到 .NET 框架外接程式模型的知識，可以在此處找到[：WPF 外接程式概述](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 要創建返回 WPF UI 的外接程式，需要為每個管道段、外接程式和主機應用程式提供特定代碼。  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 方法必須由返回 UI 的協定定義，並且其傳回值必須為 類型<xref:System.AddIn.Contract.INativeHandleContract>。 以下代碼中`GetAddInUI``IWPFAddInContract`的協定方法證明了這一點。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 由於外接程式實現它作為 子類<xref:System.Windows.FrameworkElement>提供的 U，因此與 關聯的外接程式視圖上相關的方法`IWPFAddInView.GetAddInUI`必須返回類型 的值。 <xref:System.Windows.FrameworkElement> 下列程式碼顯示合約的增益集檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 協定方法返回 一<xref:System.AddIn.Contract.INativeHandleContract>個，但外接程式返回<xref:System.Windows.FrameworkElement>（如外接程式視圖指定）。 因此，在<xref:System.Windows.FrameworkElement>跨越隔離邊界之前，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換為 。 此工作由外接程式端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>執行，如以下代碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 由於主機應用程式將顯示 一個<xref:System.Windows.FrameworkElement>，因此與 關聯的主機視圖上的方法`IWPFAddInHostView.GetAddInUI`必須返回類型<xref:System.Windows.FrameworkElement>的值。 下列程式碼顯示合約的主應用程式檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 協定方法返回 ，<xref:System.AddIn.Contract.INativeHandleContract>但主機應用程式需要 （<xref:System.Windows.FrameworkElement>由主機視圖指定）。 因此，在<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離邊界後必須<xref:System.Windows.FrameworkElement>轉換為 。 此工作由主機端配接器通過調用<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>執行，如以下代碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>實作增益集  
 在創建`WPFAddIn1.AddIn`外接程式配接器和外接程式視圖後，外接程式 （ ） 必須實現`IWPFAddInView.GetAddInUI`方法才能返回<xref:System.Windows.FrameworkElement>物件（在此示例中為<xref:System.Windows.Controls.UserControl>a）。 的<xref:System.Windows.Controls.UserControl>`AddInUI`實現由以下代碼顯示。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 `IWPFAddInView.GetAddInUI`通過外接程式實現的只需返回 的新實例`AddInUI`，如下代碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>實作主應用程式  
 創建主機端配接器和主機視圖後，主機應用程式可以使用 .NET Framework 外接程式模型打開管道、獲取外接程式的主機視圖並調用`IWPFAddInHostView.GetAddInUI`方法。 下列程式碼顯示這些步驟。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
