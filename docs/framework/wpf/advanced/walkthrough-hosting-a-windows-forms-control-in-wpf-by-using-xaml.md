---
title: 逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 3b4b743b07876f240366b2d2d19667405941a40b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976543"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供具有豐富功能集的許多控制項。 不過，您有時可能會想要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。 例如，您可能會大量投資現有的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，或者您可能會有提供獨特功能的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
 本逐步解說將示範如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 控制項。  
  
 如需本逐步解說中所示工作的完整程式代碼清單，請參閱[使用 XAML 在 WPF 中裝載 Windows Forms 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)。
  
## <a name="prerequisites"></a>Prerequisites  

若要完成這個逐步解說，您必須具有 Visual Studio。  
  
## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項  
  
#### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項  
  
1. 建立名為 `HostingWfInWpfWithXaml`的 WPF 應用程式專案。  
  
2. 加入下列組件的參考。  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. 在 WPF 設計工具中開啟 Mainwindow.xaml。  
  
4. 在 <xref:System.Windows.Window> 元素中，新增下列命名空間對應。 `wf` 命名空間對應會建立包含 Windows Forms 控制項之元件的參考。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. 在 <xref:System.Windows.Controls.Grid> 元素中，新增下列 XAML。  
  
     <xref:System.Windows.Forms.MaskedTextBox> 控制項會建立為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的子系。  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms 控制項和對等 WPF 控制項](windows-forms-controls-and-equivalent-wpf-controls.md)
- [使用 XAML 在 WPF 中裝載 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=160000)
