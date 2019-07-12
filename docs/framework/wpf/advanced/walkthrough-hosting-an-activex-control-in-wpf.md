---
title: 逐步解說：將 ActiveX 控制項裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859942"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>逐步解說：將 ActiveX 控制項裝載在 WPF 中
若要啟用改善的瀏覽器互動，您可以使用 Microsoft ActiveX 控制項，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。 本逐步解說示範您可以託管[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上的控制項為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。

 這個逐步解說中所述的工作包括：

- 建立專案。

- 建立 ActiveX 控制項。

- 裝載 WPF 頁面上的 ActiveX 控制項。

 當您完成這個逐步解說中時，您將了解如何使用 Microsoft ActiveX 控制項，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 安裝 Visual Studio 電腦上安裝。

- Visual Studio 2010。

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-and-set-up-the-project"></a>建立並設定專案

1. 建立 WPF 應用程式專案，名為`HostingAxInWpf`。

2. 將 Windows Form 控制項程式庫專案加入方案，並將專案命名`WmpAxLib`。

3. 在 WmpAxLib 專案中加入名為 wmp.dll，Windows Media Player 組件的參考。

4. 開啟**工具箱**。

5. 以滑鼠右鍵按一下**工具箱**，然後按一下**選擇項目**。

6. 按一下  **COM 元件**索引標籤上，選取**Windows Media Player**控制項，然後再按**確定**。

     Windows Media Player 控制項加入至**工具箱**。

7. 在 [方案總管] 中，以滑鼠右鍵按一下**UserControl1**檔案，然後再按一下**重新命名**。

8. 將名稱變更為`WmpAxControl.vb`或`WmpAxControl.cs`，取決於語言。

9. 如果提示您重新命名所有參考時，請按一下**是**。

## <a name="creating-the-activex-control"></a>建立 ActiveX 控制項
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 會自動產生<xref:System.Windows.Forms.AxHost>Microsoft ActiveX 控制項時，控制項會加入至設計介面的包裝函式類別。 下列程序會建立名為 AxInterop.WMPLib.dll managed 組件。

### <a name="to-create-the-activex-control"></a>若要建立 ActiveX 控制項

1. 在 Windows Form 設計工具中開啟 WmpAxControl.vb 或 WmpAxControl.cs。

2. 從**工具箱**，將 Windows Media Player 控制項加入設計介面。

3. 在 屬性 視窗中，設定 Windows Media Player 控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。

4. 建置 WmpAxLib 控制項程式庫專案。

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>裝載 WPF 頁面上的 ActiveX 控制項

### <a name="to-host-the-activex-control"></a>若要裝載 ActiveX 控制項

1. 在 HostingAxInWpf 專案中加入所產生的 ActiveX 互通性組件的參考。

     這個組件名為 AxInterop.WMPLib.dll，並已新增至 WmpAxLib 專案的偵錯資料夾中，當您匯入 Windows Media Player 控制項。

2. 加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。

3. 將參考加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名為 System.Windows.Forms.dll 組件。

4. WPF Designer 中開啟 MainWindow.xaml。

5. 名稱<xref:System.Windows.Controls.Grid>項目`grid1`。

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. 在 設計 檢視或 XAML 檢視中，選取 <xref:System.Windows.Window>項目。

7. 在 屬性 視窗中，按一下**事件** 索引標籤。

8. 按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。

9. 插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。

     此程式碼建立的執行個體<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項，並將執行個體加入`AxWindowsMediaPlayer`為其子系的控制項。

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
