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
ms.openlocfilehash: dd52313e9100f9c6a1141b53ccc5a23a4b54410a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789924"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>如何：在混合應用程式中啟用視覺化樣式
本主題說明如何在裝載于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型應用程式的 Windows Forms 控制項上啟用視覺化樣式。  
  
 如果您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法，大部分的 Windows Forms 控制項都會自動使用視覺化樣式。 如需詳細資訊，請參閱[使用視覺化樣式轉譯控制項](../../winforms/controls/rendering-controls-with-visual-styles.md)。  
  
 如需本主題中所述工作的完整程式代碼清單，請參閱[在混合式應用程式中啟用視覺化樣式範例](https://go.microsoft.com/fwlink/?LinkID=159986)。  
  
## <a name="enabling-windows-forms-visual-styles"></a>啟用 Windows Forms 視覺化樣式  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>啟用 Windows Forms 視覺化樣式  
  
1. 建立名為 `HostingWfWithVisualStyles`[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式專案。  
  
2. 在 [方案總管] 中，加入下列組件的參考。  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. 在 [工具箱] 中，按兩下 [<xref:System.Windows.Controls.Grid>] 圖示，將 <xref:System.Windows.Controls.Grid> 元素放在設計介面上。  
  
4. 在屬性視窗中，將 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的值設定為 [**自動**]。  
  
5. 在設計檢視或 XAML 視圖中，選取 <xref:System.Windows.Window>。  
  
6. 在 屬性視窗中，按一下 **事件** 索引標籤。  
  
7. 按兩下 [<xref:System.Windows.FrameworkElement.Loaded>] 事件。
  
8. 在 Mainwindow.xaml 或 MainWindow.xaml.cs 中，插入下列程式碼來處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. 按 F5 建置並執行應用程式。  
  
     Windows Forms 控制項會以視覺化樣式繪製。  
  
## <a name="disabling-windows-forms-visual-styles"></a>停用 Windows Forms 視覺化樣式  
 若要停用視覺化樣式，只要移除對 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法的呼叫即可。  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>停用 Windows Forms 視覺化樣式  
  
1. 在程式碼編輯器中，開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
2. 將 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法的呼叫標記為批註。  
  
3. 按 F5 建置並執行應用程式。  
  
     Windows Forms 控制項是以預設系統樣式繪製。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [使用視覺化樣式呈現控制項](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
