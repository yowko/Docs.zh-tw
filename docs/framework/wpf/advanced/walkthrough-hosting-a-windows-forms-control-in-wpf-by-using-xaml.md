---
title: 逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: b55a51a7ca16416b6963c57395da2f2a88a55648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548580"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供具有豐富功能集的許多控制項。 不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上的控制項，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 比方說，您可能必須在現有了大筆投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供唯一的功能。  
  
 本逐步解說會示範如何裝載 Windows Form<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>上控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 本逐步解說中的工作的完整程式碼清單，請參閱[WPF 所使用的 XAML 範例中將 Windows Form 控制項裝載](http://go.microsoft.com/fwlink/?LinkID=160000)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項  
  
#### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項  
  
1.  建立 WPF 應用程式專案，名為`HostingWfInWpfWithXaml`。  
  
2.  加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4.  在<xref:System.Windows.Window>項目，加入下列命名空間對應。 `wf`命名空間對應會建立包含在 Windows Form 控制項的組件的參考。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  在<xref:System.Windows.Controls.Grid>加入下列 XAML 項目。  
  
     <xref:System.Windows.Forms.MaskedTextBox>建立控制項的子系<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows Form 控制項和對等 WPF 控制項](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [使用 XAML 範例中裝載 WPF 中的 Windows Form 控制項](http://go.microsoft.com/fwlink/?LinkID=160000)
