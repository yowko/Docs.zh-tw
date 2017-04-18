---
title: "如何：使用 ScrollViewer 的內容捲動方法 | Microsoft Docs"
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
  - "IScrollInfo 介面"
  - "捲動方法"
  - "ScrollViewer 控制項, 捲動方法"
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 ScrollViewer 的內容捲動方法
本範例說明如何使用 <xref:System.Windows.Controls.ScrollViewer> 項目的捲動方法。  這些方法可在 <xref:System.Windows.Controls.ScrollViewer> 提供逐行或逐頁捲動的功能。  
  
## 範例  
 下列範例會建立一個名為 `sv1` 的 <xref:System.Windows.Controls.ScrollViewer>，其中裝載一個子 <xref:System.Windows.Controls.TextBlock> 項目。  由於 <xref:System.Windows.Controls.TextBlock> 大於父 <xref:System.Windows.Controls.ScrollViewer>，捲軸將會出現以供捲動。  表示各種捲動方法的 <xref:System.Windows.Controls.Button> 項目會固定在左側的另一個 <xref:System.Windows.Controls.StackPanel> 中。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中的每個 <xref:System.Windows.Controls.Button> 都會呼叫一個相關的自訂方法，該方法會控制 <xref:System.Windows.Controls.ScrollViewer> 中的捲動行為。  
  
 [!code-xml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 下列範例使用了 <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> 和 <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> 方法。  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.StackPanel>