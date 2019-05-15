---
title: 作法：建立本身為 UI 的增益集
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 0464d87aef3d4e88d9340af2ac1db93c13ba26e2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592656"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>作法：建立本身為 UI 的增益集
此範例示範如何建立增益集是 Windows Presentation Foundation (WPF) 所裝載的 WPF 獨立應用程式。  
  
 增益集是 WPF 使用者控制項的 UI。 此使用者控制項的內容是單一按鈕，當按下時，會顯示訊息方塊。 WPF 獨立應用程式會裝載增益集 UI，主應用程式視窗的內容。  
  
 **必要條件**  
  
 此範例會反白顯示 啟用此案例中，WPF 擴充功能至.NET Framework 增益集模型，並假設如下：  
  
- .NET Framework 增益集模型，包括管線、 增益集和主應用程式開發的知識。 如果您不熟悉這些概念，請參閱[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。 如需示範管線、 增益集，和主應用程式的實作的教學課程，請參閱[逐步解說：建立可延伸應用程式](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))。  
  
- .NET Framework 增益集模型的 WPF 延伸模組的知識。 請參閱[WPF 增益集概觀](wpf-add-ins-overview.md)。  
  
## <a name="example"></a>範例  
 若要建立為 WPF UI 的增益集需要特定的程式碼的每個管線區段、 增益集，和主應用程式。  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>實作合約管線區段  
 當增益集 UI，增益集的合約必須實作<xref:System.AddIn.Contract.INativeHandleContract>。 在範例中，`IWPFAddInContract`實作<xref:System.AddIn.Contract.INativeHandleContract>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>實作增益集檢視管線區段  
 因為增益集實作為的子類別<xref:System.Windows.FrameworkElement>類型，[增益集] 檢視也必須子類別化<xref:System.Windows.FrameworkElement>。 下列程式碼顯示的增益集檢視的合約，實作為`WPFAddInView`類別。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 在這裡，增益集檢視衍生自<xref:System.Windows.Controls.UserControl>。 因此，增益集 UI 也應該衍生自<xref:System.Windows.Controls.UserControl>。  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>實作增益集端配接器管線區段  
 雖然合約是<xref:System.AddIn.Contract.INativeHandleContract>，增益集是<xref:System.Windows.FrameworkElement>（如同增益集檢視管線區段所指定）。 因此，<xref:System.Windows.FrameworkElement>必須轉換成<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限之前。 這項工作藉由呼叫增益集端配接器執行<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，如下列程式碼所示。  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 其中的增益集傳回 UI 的增益集模型中 (請參閱[建立增益集，傳回 UI](how-to-create-an-add-in-that-returns-a-ui.md))，增益集配接器轉換<xref:System.Windows.FrameworkElement>要<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 也必須呼叫在此模型中，雖然您需要實作要撰寫程式碼呼叫它的方法。 您可以覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>和實作程式碼呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>如果正在呼叫的程式碼<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>之所以<xref:System.AddIn.Contract.INativeHandleContract>。 在此情況下，呼叫端會是主應用程式端配接器，後續小節將進行說明。  
  
> [!NOTE]
>  您也需要覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>主應用程式 UI 間啟用定位處理和增益集 UI 此模型中。 如需詳細資訊，請參閱 < WPF 增益集限制 > 中[WPF 增益集概觀](wpf-add-ins-overview.md)。  
  
 因為增益集端配接器實作的介面，衍生自<xref:System.AddIn.Contract.INativeHandleContract>，您也需要實作<xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>，但會忽略此項時<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>會覆寫。  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>實作主應用程式檢視管線區段  
 在此模型中，主應用程式通常會預期主應用程式檢視是<xref:System.Windows.FrameworkElement>子類別。 主應用程式端配接器必須轉換<xref:System.AddIn.Contract.INativeHandleContract>要<xref:System.Windows.FrameworkElement>之後<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限。 因為方法不會呼叫主應用程式，以取得<xref:System.Windows.FrameworkElement>、 [主機] 檢視的動作必須"return"<xref:System.Windows.FrameworkElement>藉由包含它。 因此，主應用程式檢視必須衍生自的子類別<xref:System.Windows.FrameworkElement>可包含其他[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，例如<xref:System.Windows.Controls.UserControl>。 下列程式碼顯示合約，並實作為主應用程式檢視`WPFAddInHostView`類別。  

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>實作主應用程式端配接器管線區段  
 雖然合約是<xref:System.AddIn.Contract.INativeHandleContract>，主應用程式預期<xref:System.Windows.Controls.UserControl>（如同 [主機] 檢視所指定）。 因此，<xref:System.AddIn.Contract.INativeHandleContract>必須轉換成<xref:System.Windows.FrameworkElement>跨越隔離界限之後，才能設定 [主機] 檢視的內容 (衍生自<xref:System.Windows.Controls.UserControl>)。  
  
 這項工作是由主應用程式端配接器所執行，如下列程式碼所示。  

 如您所見，主應用程式端配接器取得<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫增益集端配接器<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>方法 (這是點位置<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限)。  
  
 然後將轉換的主應用程式端配接器<xref:System.AddIn.Contract.INativeHandleContract>要<xref:System.Windows.FrameworkElement>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。 最後，<xref:System.Windows.FrameworkElement>設為 [主機] 檢視的內容。  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>實作增益集  
 增益集端配接器和增益集檢視就定位之後，增益集可以藉由衍生自增益集檢視來實作，如下列程式碼所示。  

 此範例中，您可以看到此模型的有趣的好處之一： 增益集開發人員只需要增益集 （因為它是 UI 也），而不是同時實作增益集類別和增益集 UI。  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>實作主應用程式  
 主應用程式端配接器和建立的 [主機] 檢視中，主應用程式可以使用.NET Framework 增益集模型開啟管線，並取得增益集主應用程式檢視。 下列程式碼顯示這些步驟。  

 主應用程式會使用一般的.NET Framework 增益集模型程式碼來啟動增益集，隱含傳回給主應用程式的 [主機] 檢視。 主應用程式接著會顯示 [主機] 檢視 (也就是<xref:System.Windows.Controls.UserControl>) 從<xref:System.Windows.Controls.Grid>。  
  
 處理增益集 UI 互動的程式碼會執行增益集的應用程式定義域中。 這些互動包括：  
  
- 處理<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。  
  
- 顯示<xref:System.Windows.MessageBox>。  
  
 此活動完全與主應用程式隔離。  
  
## <a name="see-also"></a>另請參閱

- [增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF 增益集概觀](wpf-add-ins-overview.md)
