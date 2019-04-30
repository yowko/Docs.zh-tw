---
title: 逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10554145de9725bb4cfc655ed88195dce28d739c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032106"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供具有豐富功能集的許多控制項。 不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制上您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 比方說，您可能已長期開發現有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供獨特的功能。  
  
 本逐步解說會示範如何裝載 Windows Forms<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上，使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 如需完整的程式碼的清單在本逐步解說所示範的工作，請參閱 <<c0> [ 裝載 Windows Forms 控制項中所使用的 XAML 範例 WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)。
  
## <a name="prerequisites"></a>必要條件  

若要完成這個逐步解說，您必須具有 Visual Studio。  
  
## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項  
  
#### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項  
  
1. 建立 WPF 應用程式專案，名為`HostingWfInWpfWithXaml`。  
  
2. 加入下列組件的參考。  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. 開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4. 在 <xref:System.Windows.Window>項目，加入下列命名空間對應。 `wf`命名空間對應會建立包含在 Windows Form 控制項的組件的參考。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. 在 <xref:System.Windows.Controls.Grid>加入下列 XAML 項目。  
  
     <xref:System.Windows.Forms.MaskedTextBox>控制項會建立為子系<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：裝載在 WPF 中的 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Form 控制項和對等 WPF 控制項](windows-forms-controls-and-equivalent-wpf-controls.md)
- [使用 XAML 範例裝載在 WPF 中的 Windows Forms 控制項](https://go.microsoft.com/fwlink/?LinkID=160000)
