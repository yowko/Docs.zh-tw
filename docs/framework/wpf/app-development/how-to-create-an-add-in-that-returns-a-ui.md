---
title: "如何：建立傳回 UI 的增益集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "增益集 [WPF], 傳回 UI"
  - "建立傳回 UI 的增益集 [WPF]"
  - "實作增益集管線區段 [WPF]"
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：建立傳回 UI 的增益集
本範例示範如何建立可將 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 傳回主 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式的增益集 \(Add\-In\)。  
  
 此增益集所傳回的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用者控制項。  這個使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式則裝載增益集，會將使用者控制項 \(由增益集傳回\) 顯示為主應用程式視窗的內容。  
  
 **必要條件**  
  
 這個範例的重點是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型實現此案例的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 擴充，並假設下列項目：  
  
-   了解 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，包括管線、增益集和主應用程式開發。  如果您不熟悉這些概念，請參閱[增益集和擴充性](../../../../ml/index.xml)。  如需示範實作管線、增益集和主應用程式的教學課程，請參閱[逐步解說：建立可延伸應用程式](../Topic/Walkthrough:%20Creating%20an%20Extensible%20Application.md)。  
  
-   了解 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 擴充，相關知識請參閱：[WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
## 範例  
 若要建立傳回 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的增益集，每個管線區段、增益集和主應用程式都需要特定的程式碼。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Contract"></a>   
## 實作合約管線區段  
 方法必須由傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的合約所定義，且傳回值必須是型別 <xref:System.AddIn.Contract.INativeHandleContract>。  下列程式碼中以 `IWPFAddInContract` 合約的 `GetAddInUI` 方法來示範。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## 實作增益集檢視管線區段  
 因為增益集實作 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，提供做為 <xref:System.Windows.FrameworkElement> 的子類別，增益集檢視上與 `IWPFAddInView.GetAddInUI` 關聯的方法，必須傳回型別為 <xref:System.Windows.FrameworkElement> 的值。  下列程式碼顯示合約的增益集檢視，實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## 實作增益集端配接器管線區段  
 合約方法傳回 <xref:System.AddIn.Contract.INativeHandleContract>，但增益集傳回 <xref:System.Windows.FrameworkElement> \(如增益集檢視所指定\)。  因此，在跨越隔離界限之前，<xref:System.Windows.FrameworkElement> 必須轉換為 <xref:System.AddIn.Contract.INativeHandleContract>。  這個工作是由增益集端配接器藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 來執行的，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## 實作主應用程式檢視管線區段  
 因為主應用程式會顯示 <xref:System.Windows.FrameworkElement>，主應用程式檢視上與 `IWPFAddInHostView.GetAddInUI` 關聯的方法，必須傳回型別為 <xref:System.Windows.FrameworkElement> 的值。  下列程式碼顯示合約的主應用程式檢視，實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## 實作主應用程式端配接器管線區段  
 合約方法傳回 <xref:System.AddIn.Contract.INativeHandleContract>，但主應用程式預期是 <xref:System.Windows.FrameworkElement> \(如主應用程式檢視所指定\)。  因此，在跨越隔離界限之後，<xref:System.AddIn.Contract.INativeHandleContract> 必須轉換為 <xref:System.Windows.FrameworkElement>。  這個工作是由主應用程式端配接器藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 來執行的，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## 實作增益集  
 隨著增益集端配接器和增益集檢視的建立，增益集 \(`WPFAddIn1.AddIn`\) 必須實作 `IWPFAddInView.GetAddInUI` 方法以傳回 <xref:System.Windows.FrameworkElement> 物件 \(本範例中的 <xref:System.Windows.Controls.UserControl>\)。  下列程式碼顯示 <xref:System.Windows.Controls.UserControl> 的實作 `AddInUI`。  
  
 [!code-xml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 增益集實作的 `IWPFAddInView.GetAddInUI` 只需要傳回 `AddInUI` 的新執行個體，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## 實作主應用程式  
 隨著主應用程式端配接器和主應用程式檢視的建立，主應用程式可以使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型開啟管線、取得增益集的主應用程式檢視，以及呼叫 `IWPFAddInHostView.GetAddInUI` 方法。  這些步驟顯示在下列程式碼中。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## 請參閱  
 [增益集和擴充性](../../../../ml/index.xml)   
 [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)