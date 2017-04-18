---
title: "如何：取得 Visual 的位移 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "從視覺物件取得位移值"
  - "位移值, 從視覺物件擷取"
  - "從視覺物件擷取位移值"
  - "視覺物件, 擷取位移值"
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：取得 Visual 的位移
這些範例示範如何擷取視覺物件相對於其父代 \(Parent\)、任何祖系或子代 \(Descendant\) 的位移 \(Offset\) 值。  
  
## 範例  
 下列範例顯示以 <xref:System.Windows.FrameworkElement.Margin%2A> 值 4 定義的 <xref:System.Windows.Controls.TextBlock>。  
  
 [!code-xml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 下列程式碼範例顯示如何使用 <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> 方法，擷取 <xref:System.Windows.Controls.TextBlock> 的位移。  位移值含在傳回的 <xref:System.Windows.Vector> 值中。  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 位移會將 <xref:System.Windows.FrameworkElement.Margin%2A> 值計算在內。  在這個案例中，<xref:System.Windows.Vector.X%2A> 是 4，而 <xref:System.Windows.Vector.Y%2A> 也是 4。  
  
 傳回的位移值相對於 <xref:System.Windows.Media.Visual> 的父代。  如果要傳回與 <xref:System.Windows.Media.Visual> 之父代無關的位移值，請使用 <xref:System.Windows.Media.Visual.TransformToAncestor%2A> 方法。  
  
## 取得相對於祖系的位移  
 下列標記範例顯示以巢狀方式放在兩個 <xref:System.Windows.Controls.StackPanel> 物件內的 <xref:System.Windows.Controls.TextBlock>。  
  
 [!code-xml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 下圖顯示標記的結果。  
  
 ![物件的位移值](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset\_01")  
兩個 StackPanel 內的巢狀 TextBlock  
  
 下列程式碼範例示範如何使用 <xref:System.Windows.Media.Visual.TransformToAncestor%2A> 方法擷取 <xref:System.Windows.Controls.TextBlock> 相對於包含 <xref:System.Windows.Window> 的位移。  位移值含在傳回的 <xref:System.Windows.Media.GeneralTransform> 值中。  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 位移會將包含 <xref:System.Windows.Window> 內所有物件的 <xref:System.Windows.FrameworkElement.Margin%2A> 值計算在內。  在這個案例中，<xref:System.Windows.Vector.X%2A> 是 28 \(16 \+ 8 \+ 4\)，而 <xref:System.Windows.Vector.Y%2A> 也是 28。  
  
 傳回的位移值相對於 <xref:System.Windows.Media.Visual> 的祖系。  如果要傳回與 <xref:System.Windows.Media.Visual> 之祖系無關的位移值，請使用 <xref:System.Windows.Media.Visual.TransformToDescendant%2A> 方法。  
  
## 取得相對於子代的位移  
 下列標記範例顯示包含在<xref:System.Windows.Controls.StackPanel> 物件內的 <xref:System.Windows.Controls.TextBlock>。  
  
 [!code-xml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 在下列程式碼範例中，示範了如何使用 <xref:System.Windows.Media.Visual.TransformToDescendant%2A> 方法，擷取 <xref:System.Windows.Controls.StackPanel> 相對於其子 <xref:System.Windows.Controls.TextBlock> 的位移。  位移值含在傳回的 <xref:System.Windows.Media.GeneralTransform> 值中。  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 位移會將所有物件的 <xref:System.Windows.FrameworkElement.Margin%2A> 值納入考量。  在這個案例中，<xref:System.Windows.Vector.X%2A> 是 \-4，而 <xref:System.Windows.Vector.Y%2A> 也是 \-4。  位移值是負值，因為父物件相對於其子物件的位移是負的。  
  
## 請參閱  
 <xref:System.Windows.Media.Visual>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)