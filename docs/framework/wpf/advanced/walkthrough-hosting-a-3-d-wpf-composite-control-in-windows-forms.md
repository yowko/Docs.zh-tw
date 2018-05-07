---
title: 逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a9aca5d1aff1057d85509be517bb352b4b27bf9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項
本逐步解說示範如何建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項，以及裝載在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項和表單使用<xref:System.Windows.Forms.Integration.ElementHost>控制項。  
  
 在本逐步解說，您將實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> ，其中包含兩個的子控制項。 <xref:System.Windows.Controls.UserControl>三維 (3d) 圓錐圖會顯示。 呈現 3d 物件會更為容易，因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]比使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。 因此，它可以理解主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>類別以建立在 3d 圖形[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。  
  
-   建立 Windows 表單主應用程式專案。  
  
-   裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>。  
  
 在此逐步解說中所述的工作的完整程式碼清單，請參閱[裝載 Windows Form 範例中的 3d WPF 複合控制項](http://go.microsoft.com/fwlink/?LinkID=160001)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>建立使用者控制項  
  
#### <a name="to-create-the-usercontrol"></a>若要建立使用者控制項  
  
1.  建立 WPF 使用者控制項程式庫專案，名為`HostingWpfUserControlInWf`。  
  
2.  開啟 usercontrol1.xaml 檔案中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
3.  產生的程式碼取代為下列程式碼。  
  
     此程式碼定義<xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>，其中包含兩個的子控制項。 第一個子系控制項是<xref:System.Windows.Controls.Label?displayProperty=nameWithType>控制; 第二個是<xref:System.Windows.Controls.Viewport3D>顯示 3d 圓錐控制項。  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>建立 Windows Forms 主專案  
  
#### <a name="to-create-the-host-project"></a>建立主專案  
  
1.  新增 Windows 應用程式專案，名為`WpfUserControlHost`至方案。 如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  在方案總管 中，加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。  
  
3.  將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件：  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  加入 `HostingWpfUserControlInWf` 專案的參考。  
  
5.  在 [方案總管] 中，設定`WpfUserControlHost`專案是啟始專案。  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>裝載 Windows Presentation Foundation 使用者控制項  
  
#### <a name="to-host-the-usercontrol"></a>若要裝載使用者控制項  
  
1.  在 Windows Form 設計工具中，開啟 [Form1]。  
  
2.  在 [屬性] 視窗中，按一下**事件**，然後按兩下<xref:System.Windows.Forms.Form.Load>事件建立事件處理常式。  
  
     以新產生的程式碼編輯器中開啟`Form1_Load`事件處理常式。  
  
3.  在 Form1.cs 中的程式碼取代為下列程式碼。  
  
     `Form1_Load`事件處理常式中建立的執行個體`UserControl1`並加入為原<xref:System.Windows.Forms.Integration.ElementHost>子控制項的控制項的集合。 <xref:System.Windows.Forms.Integration.ElementHost>控制項會加入至表單的子控制項的集合。  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [裝載 Windows Form 範例中的 WPF 複合控制項](http://go.microsoft.com/fwlink/?LinkID=160001)
