---
title: "逐步解說：在 WPF 中裝載 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce6920e8a6cea08f4aba083b99d56b4252409827
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>逐步解說：在 WPF 中裝載 Windows Form 控制項
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供具有豐富功能集的許多控制項。 不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上的控制項，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。 比方說，您可能必須在現有了大筆投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供唯一的功能。  
  
 本逐步解說會示範如何裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>上控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上，使用程式碼。  
  
 本逐步解說中的工作的完整程式碼清單，請參閱[裝載 Windows Form 控制項中 WPF 範例](http://go.microsoft.com/fwlink/?LinkID=160057)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>裝載 Windows Forms 控制項  
  
#### <a name="to-host-the-maskedtextbox-control"></a>裝載 MaskedTextBox 控制項  
  
1.  建立 WPF 應用程式專案，名為`HostingWfInWpf`。  
  
2.  加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4.  名稱<xref:System.Windows.Controls.Grid>元素`grid1`。  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。  
  
6.  在 屬性 視窗中，按一下**事件** 索引標籤。  
  
7.  按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
8.  插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. 在檔案頂端，加入下列`Imports`或`using`陳述式。  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [逐步解說：使用 XAML 在 WPF 中裝載 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows Form 控制項和對等 WPF 控制項](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057) (在 WPF 中裝載 Windows Forms 控制項的範例)
