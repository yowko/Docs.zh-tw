---
title: "如何：以程式設計方式變更 TextWrapping 屬性 | Microsoft Docs"
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
  - "文件, 以程式設計方式變更 TextWrapping 屬性"
  - "TextWrapping 屬性, 以程式設計方式變更"
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：以程式設計方式變更 TextWrapping 屬性
## 範例  
 下列程式碼範例會顯示如何以程式設計的方式變更 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> 屬性的值。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，有三個 <xref:System.Windows.Controls.Button> 項目放在 <xref:System.Windows.Controls.StackPanel> 項目內。<xref:System.Windows.Controls.Button> 的每一個 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件都會對應程式碼中的事件處理常式。  事件處理常式會使用與 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> 值相同的名稱，該值會在按下按鈕時套用至 `txt2`。  此外，`txt1` \(未在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中顯示的 <xref:System.Windows.Controls.TextBlock>\) 中的文字會更新，以反映屬性中的變更。  
  
 [!code-xml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>   
 <xref:System.Windows.TextWrapping>