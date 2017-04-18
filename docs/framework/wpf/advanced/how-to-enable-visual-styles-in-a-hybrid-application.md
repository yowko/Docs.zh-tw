---
title: "如何：在混合應用程式中啟用視覺化樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "混合應用程式 [WPF 互通性]"
  - "視覺化樣式 [Windows Form]"
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：在混合應用程式中啟用視覺化樣式
本主題顯示如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式中所裝載 \(Host\) 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項上啟用 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式。  
  
 如果應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法，而且應用程式是在 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 中執行時，大部分的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項都會自動使用視覺化樣式。  如需詳細資訊，請參閱 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)。  
  
 如需本主題中所說明之工作的完整程式碼清單，請參閱[在混合式應用程式中啟用視覺化樣式範例](http://go.microsoft.com/fwlink/?LinkID=159986) \(英文\)。  
  
## 啟用 Windows Form 視覺化樣式  
  
#### 若要啟用 Windows Form 視覺化樣式  
  
1.  建立名為 `HostingWfWithVisualStyles` 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式專案。  
  
2.  在 \[方案總管\] 中加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  按兩下 \[工具箱\] 中的 <xref:System.Windows.Controls.Grid> 圖示，將 <xref:System.Windows.Controls.Grid> 項目放在設計介面上。  
  
4.  在 \[屬性\] 視窗中，將 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的值設定為 \[**Auto**\]。  
  
5.  在 \[設計\] 檢視或 \[XAML\] 檢視中，選取 <xref:System.Windows.Window>。  
  
6.  按一下 \[屬性\] 視窗中的 \[**事件**\] 索引標籤。  
  
7.  按兩下 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
8.  在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，插入下列程式碼以處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. 按 F5 建置並執行應用程式。  
  
     會使用視覺化樣式繪製 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
## 停用 Windows Form 視覺化樣式  
 若要停用視覺化樣式，只需移除對 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法的呼叫即可。  
  
#### 若要停用 Windows Form 視覺化樣式  
  
1.  在程式碼編輯器中開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
2.  將對 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法的呼叫標記為註解。  
  
3.  按 F5 建置並執行應用程式。  
  
     會使用預設系統樣式繪製 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>   
 <xref:System.Windows.Forms.VisualStyles>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)   
 [逐步解說：在 WPF 中裝載 Windows Form 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)