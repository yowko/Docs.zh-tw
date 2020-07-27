---
title: 在 WPF 中裝載 Windows Forms 控制項
description: 瞭解如何在 Windows Presentation Foundation 中裝載 Windows Forms 控制項，其已提供許多具有豐富功能集的控制項。
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164979"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>逐步解說：將 Windows Forms 控制項裝載在 WPF 中

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供具有豐富功能集的許多控制項。 不過，您有時可能會想要在頁面上使用 Windows Forms 控制項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 例如，您可能會大量投資現有的 Windows Forms 控制項，或者您可能會有提供獨特功能的 Windows Forms 控制項。

本逐步解說將示範如何 <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 使用程式碼，在頁面上裝載 Windows Forms 控制項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。

如需本逐步解說中所示工作的完整程式代碼清單，請參閱[在 WPF 中裝載 Windows Forms 控制項範例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項

### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項

1. 建立名為的 WPF 應用程式專案 `HostingWfInWpf` 。

2. 加入下列組件的參考。

    - WindowsFormsIntegration

    - System.Windows.Forms

3. 在 WPF 設計工具中開啟 Mainwindow.xaml。

4. 將元素命名為 <xref:System.Windows.Controls.Grid> `grid1` 。

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. 在設計檢視或 XAML 視圖中，選取 <xref:System.Windows.Window> 元素。

6. 在 [屬性視窗中，按一下 [**事件**] 索引標籤。

7. 按兩下 <xref:System.Windows.FrameworkElement.Loaded> 事件。

8. 插入下列程式碼來處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. 在檔案的頂端，新增下列 `Imports` 或 `using` 語句。

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. 按 **F5** 以建置並執行應用程式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Form 控制項和對等 WPF 控制項](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF) (在 WPF 中裝載 Windows Forms 控制項的範例)
