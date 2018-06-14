---
title: 如何：在混合應用程式中啟用視覺化樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 2d714ad020f2f7b6a6343c8f8e3901b59dfd23a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545619"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>如何：在混合應用程式中啟用視覺化樣式
本主題說明如何啟用[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]上的視覺樣式[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項裝載於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。  
  
 如果您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法中，大部分的程式[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上執行您的應用程式時，控制項將會自動使用視覺化樣式[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]。 如需詳細資訊，請參閱[視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)。  
  
 如本主題中所述的工作的完整程式碼清單，請參閱[啟用混合式應用程式範例中的視覺化樣式](http://go.microsoft.com/fwlink/?LinkID=159986)。  
  
## <a name="enabling-windows-forms-visual-styles"></a>啟用 Windows Forms 視覺化樣式  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>啟用 Windows Forms 視覺化樣式  
  
1.  建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式專案，名為`HostingWfWithVisualStyles`。  
  
2.  在 [方案總管] 中，加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  在 [工具箱] 中按兩下<xref:System.Windows.Controls.Grid>圖示，以放置<xref:System.Windows.Controls.Grid>設計介面上的項目。  
  
4.  在 [屬性] 視窗中設定的值<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>屬性**自動**。  
  
5.  在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>。  
  
6.  在 屬性 視窗中，按一下**事件** 索引標籤。  
  
7.  按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。
  
8.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. 按 F5 鍵建置並執行應用程式。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]使用視覺化樣式繪製控制項。  
  
## <a name="disabling-windows-forms-visual-styles"></a>停用 Windows Forms 視覺化樣式  
 若要停用視覺化樣式，只要移除呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>停用 Windows Forms 視覺化樣式  
  
1.  在程式碼編輯器中，開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
2.  註解的呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。  
  
3.  按 F5 鍵建置並執行應用程式。  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]與預設系統樣式繪製控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
