---
title: 逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 61a234a679d9937cb38a753a3d73f2ecc9ec891a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190362"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 許多控制項提供一組豐富的功能。 不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制上您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 比方說，您可能已長期開發現有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供獨特的功能。  
  
 本逐步解說會示範如何裝載 Windows Forms<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上，使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 如需完整的程式碼的清單在本逐步解說所示範的工作，請參閱 <<c0> [ 裝載 Windows Forms 控制項中所使用的 XAML 範例 WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)。
  
## <a name="prerequisites"></a>必要條件  

若要完成這個逐步解說，您必須具有 Visual Studio。  
  
## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項  
  
#### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項  
  
1.  建立 WPF 應用程式專案，名為`HostingWfInWpfWithXaml`。  
  
2.  加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4.  在 <xref:System.Windows.Window>項目，加入下列命名空間對應。 `wf`命名空間對應會建立包含在 Windows Form 控制項的組件的參考。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  在 <xref:System.Windows.Controls.Grid>加入下列 XAML 項目。  
  
     <xref:System.Windows.Forms.MaskedTextBox>控制項會建立為子系<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：將 Windows Forms 控制項裝載在 WPF 中](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Form 控制項和對等 WPF 控制項](windows-forms-controls-and-equivalent-wpf-controls.md)
- [使用 XAML 範例裝載在 WPF 中的 Windows Forms 控制項](https://go.microsoft.com/fwlink/?LinkID=160000)
