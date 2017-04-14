---
title: "如何：設定項目的高度屬性 | Microsoft Docs"
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
  - "高度屬性"
  - "Panel 控制項, 項目的高度屬性"
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：設定項目的高度屬性
## 範例  
 本範例會以視覺化方式顯示 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 四個與高度相關的屬性在呈現行為方面的差異。  
  
 <xref:System.Windows.FrameworkElement> 類別會公開四個屬性，描述項目的高度特性。  這四個屬性可能會衝突，因此若發生衝突，優先採用的值會決定如下：<xref:System.Windows.FrameworkElement.MinHeight%2A> 值優先於 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 值，而後者又優先於 <xref:System.Windows.FrameworkElement.Height%2A> 值。  第四個屬性 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 屬於唯讀屬性，會回報隨配置處理序互動所決定的實際高度。  
  
 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會將 <xref:System.Windows.Shapes.Rectangle> 項目 \(`rect1`\) 繪製為 <xref:System.Windows.Controls.Canvas> 的子項。  您可以使用一系列的 <xref:System.Windows.Controls.ListBox> 項目 \(表示 <xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A> 與 <xref:System.Windows.FrameworkElement.Height%2A> 的屬性值\)，變更<xref:System.Windows.Shapes.Rectangle> 的高度屬性。  利用這種方式，每個屬性的優先順序就能以視覺化方式顯示。  
  
 [!code-xml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例會處理 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件所引發的事件。  每個處理常式會採用 <xref:System.Windows.Controls.ListBox> 的輸入、將值剖析為 <xref:System.Double>，然後將值套用到指定的高度相關屬性。  高度值也會轉換成字串，並寫入各種 <xref:System.Windows.Controls.TextBlock> 項目 \(所選取的 XAML 中並不會顯示這些項目的定義\)。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整範例，請參閱[高度屬性範例](http://go.microsoft.com/fwlink/?LinkID=159993) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>   
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>   
 <xref:System.Windows.FrameworkElement.MinHeight%2A>   
 <xref:System.Windows.FrameworkElement.Height%2A>   
 [設定項目的寬度屬性](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [高度屬性範例](http://go.microsoft.com/fwlink/?LinkID=159993)