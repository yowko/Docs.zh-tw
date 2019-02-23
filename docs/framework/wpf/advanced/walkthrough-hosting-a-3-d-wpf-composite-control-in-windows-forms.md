---
title: 逐步解說：裝載 Windows Forms 中的 3d WPF 複合控制項
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: d32b98fce3cf5e4fe82745c3d0ba8992ee75339e
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746201"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>逐步解說：裝載 Windows Forms 中的 3d WPF 複合控制項

本逐步解說將示範如何建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項，並將它裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和表單使用<xref:System.Windows.Forms.Integration.ElementHost>控制項。

在此逐步解說中，您將實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>包含兩個子控制項。 <xref:System.Windows.Controls.UserControl>顯示三維 (3-D) 圓錐式。 呈現 3d 物件是更為容易[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]比使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。 因此，它對有意義主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>類別來建立 3d 圖形[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。

這個逐步解說中所述的工作包括：

-   建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。

-   建立 Windows Forms 主應用程式專案。

-   裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>建立使用者控制項

1.  建立**WPF 使用者控制項程式庫**專案，命名為`HostingWpfUserControlInWf`。

2.  開啟在 UserControl1.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。

3.  產生的程式碼取代為下列程式碼：

     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     此程式碼定義<xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>包含兩個子控制項。 第一個子控制項<xref:System.Windows.Controls.Label?displayProperty=nameWithType>控制項，第二個是<xref:System.Windows.Controls.Viewport3D>顯示 3d 圓錐式控制項。

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>建立主應用程式專案

1.  新增**WPF 應用程式 (.NET Framework)** 專案，命名為`WpfUserControlHost`至方案。 如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。

2.  在 [**方案總管] 中**，加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。

3.  將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件：

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4.  加入 `HostingWpfUserControlInWf` 專案的參考。

5.  在 [方案總管] 中，設定`WpfUserControlHost`專案是啟始專案。

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>裝載使用者控制項

1.  在 Windows Form 設計工具中，開啟 Form1。

2.  在 [屬性] 視窗中，按一下**事件**，然後按兩下<xref:System.Windows.Forms.Form.Load>事件建立事件處理常式。

     以新產生的程式碼編輯器中開啟`Form1_Load`事件處理常式。

3.  取代為下列程式碼的 Form1.cs 中的程式碼。

     `Form1_Load`事件處理常式建立的執行個體`UserControl1`，並將與<xref:System.Windows.Forms.Integration.ElementHost>子控制項的控制項的集合。 <xref:System.Windows.Forms.Integration.ElementHost>控制項加入至表單的集合中的子控制項。

     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4.  按 **F5** 鍵建置並執行應用程式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [裝載 WPF 複合控制項在 Windows Form 範例](https://go.microsoft.com/fwlink/?LinkID=160001)