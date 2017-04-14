---
title: "如何：使用 IScrollInfo 介面捲動內容 | Microsoft Docs"
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
  - "捲動內容"
  - "ScrollViewer 控制項, 捲動內容"
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 IScrollInfo 介面捲動內容
本範例說明如何使用 <xref:System.Windows.Controls.Primitives.IScrollInfo> 介面捲動內容。  
  
## 範例  
 下列範例會示範 <xref:System.Windows.Controls.Primitives.IScrollInfo> 介面的功能。  此範例會在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中建立 <xref:System.Windows.Controls.StackPanel> 項目，並將它巢狀在父 <xref:System.Windows.Controls.ScrollViewer> 中。  <xref:System.Windows.Controls.StackPanel> 的子項目可以使用 <xref:System.Windows.Controls.Primitives.IScrollInfo> 介面定義的方法，以邏輯方式捲動，並轉換為程式碼中  <xref:System.Windows.Controls.StackPanel> \(`sp1`\) 的執行個體。  
  
 [!code-xml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中的每個 <xref:System.Windows.Controls.Button> 都會觸發關聯的自訂方法，此方法會控制 <xref:System.Windows.Controls.StackPanel> 中的捲動行為。  下列範例顯示如何使用 <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> 和 <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> 方法，並以非特定方式顯示如何使用 <xref:System.Windows.Controls.Primitives.IScrollInfo> 類別定義的所有定位方法。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## 請參閱  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 <xref:System.Windows.Controls.StackPanel>   
 [ScrollViewer 概觀](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)