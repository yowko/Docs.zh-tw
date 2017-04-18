---
title: "如何：設定 TextBox 控制項的文字內容 | Microsoft Docs"
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
  - "文字內容, 設定"
  - "TextBox 控制項, 設定文字內容"
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：設定 TextBox 控制項的文字內容
這個範例顯示如何使用 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性設定 <xref:System.Windows.Controls.TextBox> 控制項的初始文字內容。  
  
 **附註**：雖然範例的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 版本可以使用 `<TextBox.Text>` 標記括住每個按鈕的 <xref:System.Windows.Controls.TextBox> 內容，但這不是必要動作，因為 <xref:System.Windows.Controls.TextBox> 會將 <xref:System.Windows.Markup.ContentPropertyAttribute> 屬性 \(Attribute\) 套用至 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性 \(Property\)。  如需詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
## 範例  
 [!code-xml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## 範例  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)