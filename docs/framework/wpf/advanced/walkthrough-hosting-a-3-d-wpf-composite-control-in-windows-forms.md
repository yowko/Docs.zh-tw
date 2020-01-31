---
title: 在 Windows Forms 中主控 3D WPF 複合控制項
titleSuffix: ''
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: 07222809d62b207730ddad3c87b8fb60e1602bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744460"
---
# <a name="walkthrough-host-a-3d-wpf-composite-control-in-windows-forms"></a>逐步解說：在 Windows Forms 中裝載 3D WPF 複合控制項

本逐步解說將示範如何建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項，並使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項將它裝載在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項和表單中。

在此逐步解說中，您將會執行包含兩個子控制項的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。 <xref:System.Windows.Controls.UserControl> 會顯示三維（3D）圓錐圖。 與 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]相比，轉譯3D 物件比 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 更容易。 因此，裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 類別以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中建立3D 圖形是合理的。

這個逐步解說中所述的工作包括：

- 建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。

- 建立 Windows Forms 主專案。

- 裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。

## <a name="prerequisites"></a>必要條件：

您需要下列元件才能完成此逐步解說：

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>建立 UserControl

1. 建立名為 `HostingWpfUserControlInWf`的**WPF 使用者控制項程式庫**專案。

2. 在 WPF 設計工具中開啟 UserControl1。

3. 將產生的程式碼取代為下列程式碼：

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     此程式碼會定義包含兩個子控制項的 <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>。 第一個子控制項是 <xref:System.Windows.Controls.Label?displayProperty=nameWithType> 控制項;第二個是顯示3D 圓錐的 <xref:System.Windows.Controls.Viewport3D> 控制項。

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>建立主專案

1. 將名為 `WpfUserControlHost` 的**Windows Forms 應用程式（.NET Framework）** 專案新增至方案。

2. 在**方案總管**中，加入名為 WindowsFormsIntegration 的 WindowsFormsIntegration 元件參考。

3. 新增下列 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元件的參考：

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. 加入 `HostingWpfUserControlInWf` 專案的參考。

5. 在方案總管中，將 `WpfUserControlHost` 專案設定為啟始專案。

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>裝載 UserControl

1. 在 Windows Form 設計工具中，開啟 Form1。

2. 在 屬性視窗中，按一下 **事件**，然後按兩下 <xref:System.Windows.Forms.Form.Load> 事件來建立事件處理常式。

     [程式碼編輯器] 隨即開啟至新產生的 `Form1_Load` 事件處理常式。

3. 將 Form1.cs 中的程式碼取代為下列程式碼。

     `Form1_Load` 事件處理常式會建立 `UserControl1` 的實例，並將背後加入至 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的子控制項集合。 <xref:System.Windows.Forms.Integration.ElementHost> 控制項會加入至表單的子控制項集合。

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. 按 **F5** 鍵建置並執行應用程式。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [在 Windows Forms 範例中裝載 WPF 複合控制項](https://go.microsoft.com/fwlink/?LinkID=160001)
