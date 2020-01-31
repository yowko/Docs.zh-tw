---
title: 在 WPF 中裝載 ActiveX 控制項
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742619"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>逐步解說：在 WPF 中裝載 ActiveX 控制項
若要改善與瀏覽器的互動，您可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中使用 Microsoft ActiveX 控制項。 本逐步解說會示範如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 Microsoft Windows 媒體播放機做為控制項。

 這個逐步解說中所述的工作包括：

- 建立專案。

- 建立 ActiveX 控制項。

- 將 ActiveX 控制項裝載在 WPF 頁面上。

 當您完成本逐步解說時，您將瞭解如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中使用 Microsoft ActiveX 控制項。

## <a name="prerequisites"></a>必要條件：
 您需要下列元件才能完成此逐步解說：

- 安裝 Visual Studio 的電腦上安裝了 Microsoft Windows 媒體播放機。

- Visual Studio 2010。

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-and-set-up-the-project"></a>建立並設定專案

1. 建立名為 `HostingAxInWpf`的 WPF 應用程式專案。

2. 將 Windows Forms 控制項程式庫專案新增至方案，並將專案命名為 `WmpAxLib`。

3. 在 WmpAxLib 專案中，加入名為 wmp 的 Windows 媒體播放機元件的參考。

4. 開啟 [**工具箱**]。

5. 在 [**工具箱**] 中按一下滑鼠右鍵，然後按一下 **[選擇專案**]。

6. 按一下 [ **COM 元件**] 索引標籤，選取 [ **Windows 媒體播放機**] 控制項，然後按一下 **[確定]** 。

     Windows 媒體播放機控制項就會加入 [**工具箱**] 中。

7. 在方案總管中，以滑鼠右鍵按一下**UserControl1**檔案，然後按一下 [**重新命名**]。

8. 視語言而定，將名稱變更為 `WmpAxControl.vb` 或 `WmpAxControl.cs`。

9. 如果系統提示您重新命名所有參考，請按一下 **[是]** 。

## <a name="creating-the-activex-control"></a>建立 ActiveX 控制項
當控制項加入至設計介面時，Visual Studio 會自動為 Microsoft ActiveX 控制項產生 <xref:System.Windows.Forms.AxHost> 的包裝函式類別。 下列程式會建立名為 AxInterop. WMPLib 的 managed 元件。

### <a name="to-create-the-activex-control"></a>若要建立 ActiveX 控制項

1. 在 Windows Form 設計工具中開啟 WmpAxControl 或 WmpAxControl.cs。

2. 從 [**工具箱**] 中，將 Windows 媒體播放機控制項加入至設計介面。

3. 在屬性視窗中，將 Windows 媒體播放機控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值設定為 [<xref:System.Windows.Forms.DockStyle.Fill>]。

4. 建立 WmpAxLib 控制項程式庫專案。

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>在 WPF 頁面上裝載 ActiveX 控制項

### <a name="to-host-the-activex-control"></a>裝載 ActiveX 控制項

1. 在 HostingAxInWpf 專案中，新增所產生 ActiveX 互通性元件的參考。

     這個元件名為 AxInterop. WMPLib，而當您匯入 Windows 媒體播放機控制項時，會加入至 WmpAxLib 專案的 Debug 資料夾。

2. 加入 WindowsFormsIntegration 元件的參考，其名稱為 WindowsFormsIntegration。

3. 將參考加入至名為 System.web 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 元件。

4. 在 WPF 設計工具中開啟 Mainwindow.xaml。

5. 將 <xref:System.Windows.Controls.Grid> 元素命名為 `grid1`。

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. 在設計檢視或 XAML 視圖中，選取 [<xref:System.Windows.Window>] 元素。

7. 在 屬性視窗中，按一下 **事件** 索引標籤。

8. 按兩下 [<xref:System.Windows.FrameworkElement.Loaded>] 事件。

9. 插入下列程式碼以處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。

     此程式碼會建立 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的實例，並將 `AxWindowsMediaPlayer` 控制項的實例當做其子系加入。

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. 按 F5 建置並執行應用程式。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
