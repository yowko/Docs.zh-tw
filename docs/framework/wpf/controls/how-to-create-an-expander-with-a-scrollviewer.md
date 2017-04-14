---
title: "如何：使用 ScrollViewer 建立 Expander | Microsoft Docs"
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
  - "控制項 [WPF], 展開工具"
  - "控制項 [WPF], ScrollViewer"
  - "Expander 控制項, 建立"
  - "ScrollViewer 控制項, Expander 控制項"
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 ScrollViewer 建立 Expander
本範例顯示如何建立含有複雜內容 \(例如影像和文字\) 的 <xref:System.Windows.Controls.Expander> 控制項。  本範例也會將 <xref:System.Windows.Controls.Expander> 的內容放在 <xref:System.Windows.Controls.ScrollViewer> 控制項。  
  
## 範例  
 下列範例顯示如何建立 <xref:System.Windows.Controls.Expander>。  本範例使用含有影像與文字的 <xref:System.Windows.Controls.Primitives.BulletDecorator> 控制項，以便定義 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>。  <xref:System.Windows.Controls.ScrollViewer> 控制項會提供捲動展開內容的方法。  
  
 請注意，本範例會於 <xref:System.Windows.Controls.ScrollViewer> 上設定 <xref:System.Windows.FrameworkElement.Height%2A> 屬性，而非於內容上設定該屬性。  如果 <xref:System.Windows.FrameworkElement.Height%2A> 已設定於內容上，則 <xref:System.Windows.Controls.ScrollViewer> 不會允許使用者捲動內容。  <xref:System.Windows.FrameworkElement.Width%2A> 屬性已設定於 <xref:System.Windows.Controls.Expander> 控制項上，而且此設定會套用至 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> 與展開的內容。  
  
 [!code-xml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Expander>   
 [Expander 概觀](../../../../docs/framework/wpf/controls/expander-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)