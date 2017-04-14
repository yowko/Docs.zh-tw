---
title: "如何：擷取 RichTextBox 的文字內容 | Microsoft Docs"
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
  - "內容, 擷取"
  - "擷取文字內容"
  - "RichTextBox 控制項, 擷取文字內容"
  - "文字內容, 擷取"
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：擷取 RichTextBox 的文字內容
本範例示範如何以純文字格式擷取 <xref:System.Windows.Controls.RichTextBox> 的內容。  
  
## 範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 程式碼會描述一個含簡單內容的具名 <xref:System.Windows.Controls.RichTextBox> 控制項。  
  
 [!code-xml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## 範例  
 下列程式碼會實作使用 <xref:System.Windows.Controls.RichTextBox> 當做引數的方法，並傳回表示 <xref:System.Windows.Controls.RichTextBox> 之純文字內容的字串。  
  
 此方法會使用 <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> 和 <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> 指定要擷取的內容範圍，藉以從 <xref:System.Windows.Controls.RichTextBox> 的內容建立新的 <xref:System.Windows.Documents.TextRange>。  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> 和 <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> 屬性都會傳回 <xref:System.Windows.Documents.TextPointer> 而且都可以在表示 <xref:System.Windows.Controls.RichTextBox> 內容的基礎 FlowDocument 上存取。  <xref:System.Windows.Documents.TextRange> 提供一個 Text 屬性，此屬性會以字串形式傳回 <xref:System.Windows.Documents.TextRange> 的純文字部分。  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## 請參閱  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)