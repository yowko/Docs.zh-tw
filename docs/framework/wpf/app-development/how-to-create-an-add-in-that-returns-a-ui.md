---
title: 如何：建立傳回 UI 的增益集
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e89cb9d0c8e5a26703ff5f56a3af10d7fe9923f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>如何：建立傳回 UI 的增益集
這個範例示範如何建立 Windows Presentation Foundation (WPF) 傳回至主機[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式。  
  
 增益集傳回[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也就是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]使用者控制項。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式裝載增益集與主應用程式視窗的內容以顯示使用者控制項 （增益集所傳回）。  
  
 **必要條件**  
  
 此範例中會反白顯示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，讓此案例中，並假設下列：  
  
-   知識的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，包括管線、 增益集與主應用程式開發。 如果您不熟悉這些概念，請參閱[增益集和擴充性](../../../../docs/framework/add-ins/index.md)。 示範在管線、 增益集，與主應用程式的實作的教學課程，請參閱[逐步解說： 建立可延伸應用程式](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)。  
  
-   知識的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，可以在這裡找到： [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立傳回[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]每個管線區段、 增益集，以及主應用程式需要特定的程式碼。  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 必須傳回合約所定義的方法[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，而且它的傳回值必須是型別<xref:System.AddIn.Contract.INativeHandleContract>。 這示範`GetAddInUI`方法`IWPFAddInContract`合約中的下列程式碼。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 因為增益集實作[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]為的子類別提供<xref:System.Windows.FrameworkElement>，增益集的檢視與相互關聯上的方法`IWPFAddInView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。 下列程式碼顯示合約的增益集檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但是增益集傳回<xref:System.Windows.FrameworkElement>（如同增益集的檢視所指定）。 因此，<xref:System.Windows.FrameworkElement>必須轉換成<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔離界限。 這項工作由增益集端配接器呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 因為主應用程式會顯示<xref:System.Windows.FrameworkElement>，與相互關聯的主機 檢視上的方法`IWPFAddInHostView.GetAddInUI`必須傳回型別的值<xref:System.Windows.FrameworkElement>。 下列程式碼顯示合約的主應用程式檢視，並實作為介面。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 合約方法會傳回<xref:System.AddIn.Contract.INativeHandleContract>，但主應用程式預期<xref:System.Windows.FrameworkElement>（如同 [主機] 檢視所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換成<xref:System.Windows.FrameworkElement>之後跨越隔離界限。 這項工作由主應用程式端配接器呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集  
 使用增益集端配接器與增益集建立檢視，增益集 (`WPFAddIn1.AddIn`) 必須實作`IWPFAddInView.GetAddInUI`方法以傳回<xref:System.Windows.FrameworkElement>物件 (<xref:System.Windows.Controls.UserControl>在此範例中)。 實作<xref:System.Windows.Controls.UserControl>， `AddInUI`，以下列程式碼所示。  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 實作`IWPFAddInView.GetAddInUI`增益集只需要傳回的新執行個體`AddInUI`，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>實作主應用程式  
 主機端配接器和建立的 [主機] 檢視中，主應用程式可以使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，若要開啟管線，請取得增益集，並呼叫主應用程式檢視`IWPFAddInHostView.GetAddInUI`方法。 下列程式碼顯示這些步驟。  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>另請參閱  
 [增益集和擴充性](../../../../docs/framework/add-ins/index.md)  
 [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
