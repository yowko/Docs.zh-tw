---
title: "如何：修改文字的印刷樣式 | Microsoft Docs"
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
  - "設定 Typography 屬性"
  - "Typography 屬性, 設定"
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：修改文字的印刷樣式
下列範例以 <xref:System.Windows.Documents.Paragraph> 為例，顯示如何設定 <xref:System.Windows.Documents.TextElement.Typography%2A> 屬性。  
  
## 範例  
 [!code-xml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：已變更印刷的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement\_Typog")  
  
 相反地，下圖顯示具有預設印制樣式屬性的類似範例如何呈現。  
  
 ![螢幕擷取畫面：已變更印刷的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement\_Typog\_Default")  
  
## 範例  
 下列範例顯示如何以程式設計的方式設定 <xref:System.Windows.Controls.TextBox.Typography%2A> 屬性。  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## 請參閱  
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)