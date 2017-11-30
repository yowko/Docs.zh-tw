---
title: "如何：建立本身為 UI 的增益集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9151dd5fa36e3691361bcf6d7c7b281646982f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>如何：建立本身為 UI 的增益集
這個範例示範如何建立增益集是[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]由其中裝載[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式。  
  
 增益集是[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也就是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]使用者控制項。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]獨立應用程式裝載增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]做為主要應用程式視窗的內容。  
  
 **必要條件**  
  
 此範例中會反白顯示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，讓此案例中，並假設下列：  
  
-   知識的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，包括管線、 增益集與主應用程式開發。 如果您不熟悉這些概念，請參閱[增益集和擴充性](../../../../docs/framework/add-ins/index.md)。 示範在管線、 增益集，與主應用程式的實作的教學課程，請參閱[逐步解說： 建立可延伸應用程式](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)。  
  
-   知識的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]延伸[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型，可以在這裡找到： [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立增益集是[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]每個管線區段、 增益集，以及主應用程式需要特定的程式碼。  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 當增益集是[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，增益集的合約必須實作<xref:System.AddIn.Contract.INativeHandleContract>。 在範例中，`IWPFAddInContract`實作<xref:System.AddIn.Contract.INativeHandleContract>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 因為增益集實作為的子類別<xref:System.Windows.FrameworkElement>類型、 檢視表增益集也必須子類別化<xref:System.Windows.FrameworkElement>。 下列程式碼顯示增益集檢視的合約，實作為`WPFAddInView`類別。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 在這裡，增益集的檢視衍生自<xref:System.Windows.Controls.UserControl>。 因此，增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也應該衍生自<xref:System.Windows.Controls.UserControl>。  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 當合約是<xref:System.AddIn.Contract.INativeHandleContract>，增益集是<xref:System.Windows.FrameworkElement>（依檢視增益集管線區段所指定）。 因此，<xref:System.Windows.FrameworkElement>必須轉換成<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔離界限。 這項工作由增益集端配接器呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 在其中的增益集是會傳回增益集模型[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](請參閱[建立增益集，傳回的 UI](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md))，增益集配接器轉換<xref:System.Windows.FrameworkElement>至<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>必須也先呼叫在這個模型中，雖然您必須實作從中撰寫程式碼呼叫此方法。 您可以覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>和實作程式碼呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>如果正在呼叫的程式碼<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>預期<xref:System.AddIn.Contract.INativeHandleContract>。 在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。  
  
> [!NOTE]
>  您也需要覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>主應用程式間啟用定位處理此模型中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]和增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 如需詳細資訊，請參閱 < WPF 增益集限制 「 [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)。  
  
 因為增益集端配接器實作的介面，衍生自<xref:System.AddIn.Contract.INativeHandleContract>，您也需要實作<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，但是會忽略此時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>會覆寫。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 在此模型中，主應用程式通常需要主機檢視，以<xref:System.Windows.FrameworkElement>子類別。 主機端配接器必須轉換<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>之後<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限。 若要取得的主應用程式不正在呼叫的方法，因為<xref:System.Windows.FrameworkElement>，主應用程式檢視必須 「 傳回 」<xref:System.Windows.FrameworkElement>由包含它。 因此，主應用程式檢視必須衍生自的子類別<xref:System.Windows.FrameworkElement>可以包含其他[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，例如<xref:System.Windows.Controls.UserControl>。 下列程式碼顯示的合約，實作為 [主機] 檢視`WPFAddInHostView`類別。  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 當合約是<xref:System.AddIn.Contract.INativeHandleContract>，主機應用程式預期<xref:System.Windows.Controls.UserControl>（如同 [主機] 檢視所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換成<xref:System.Windows.FrameworkElement>之後跨越隔離界限之前設定為 [主機] 檢視的內容, (其衍生自<xref:System.Windows.Controls.UserControl>)。  
  
 這項工作是由主應用程式端配接器所執行，如下列程式碼所示。  
  
  
  
 如您所見，主應用程式端配接器取得<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫端的新增配接器的<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>方法 (這是點位置<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限)。  
  
 然後將轉換主應用程式端配接器<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。 最後，<xref:System.Windows.FrameworkElement>設為 [主機] 檢視的內容。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集  
 增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。  
  
  
  
  
  
 從這個範例中，您可以看到此模型的有趣的好處之一： 增益集開發人員只需要實作增益集 (因為它是[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也)，而不是增益集類別和增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>實作主應用程式  
 主機端配接器和建立的 [主機] 檢視中，主應用程式可以使用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型開啟管線，並取得增益集 [主機] 檢視。 下列程式碼顯示這些步驟。  
  
  
  
 主應用程式會使用一般[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型的程式碼，以啟動增益集，會隱含地傳回主應用程式的 [主機] 檢視。 主應用程式接著會顯示 [主機] 檢視 (也就是<xref:System.Windows.Controls.UserControl>) 從<xref:System.Windows.Controls.Grid>。  
  
 處理與增益集的互動的程式碼[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]增益集應用程式定義域中執行。 這些互動包括：  
  
-   處理<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
-   顯示<xref:System.Windows.MessageBox>。  
  
 此活動完全與主應用程式隔離。  
  
## <a name="see-also"></a>另請參閱  
 [增益集和擴充性](../../../../docs/framework/add-ins/index.md)  
 [WPF 增益集概觀](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
