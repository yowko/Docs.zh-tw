---
title: "如何：從 TextBox 取得線條集合 | Microsoft Docs"
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
  - "線條, 取得集合"
  - "TextBox 控制項, 取得文字行集合"
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：從 TextBox 取得線條集合
本範例示範如何從 <xref:System.Windows.Controls.TextBox> 取得文字行集合。  
  
## 範例  
 下列範例顯示使用 <xref:System.Windows.Controls.TextBox> 當做引數的簡單方法，並傳回包含 **TextBox** 中文字行的 <xref:System.Collections.Specialized.StringCollection>。  其使用 <xref:System.Windows.Controls.TextBox.LineCount%2A> 屬性判斷 **TextBox** 中目前包含的行數，然後再使用 <xref:System.Windows.Controls.TextBox.GetLineText%2A> 方法擷取每一行並將它加入行集合中。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)