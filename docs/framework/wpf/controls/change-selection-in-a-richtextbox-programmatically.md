---
title: "以程式設計方式變更 RichTextBox 中的選項 | Microsoft Docs"
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
  - "變更 RichTextBox 中的選取範圍 [WPF]"
  - "變更文字方塊中的選取範圍 [WPF]"
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 以程式設計方式變更 RichTextBox 中的選項
這個範例顯示如何以程式設計方式變更 <xref:System.Windows.Controls.RichTextBox> 中的目前選取範圍。  這個選取範圍與使用者利用使用者介面選取的內容相同。  
  
## 範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 程式碼會描述一個含簡單內容的具名 <xref:System.Windows.Controls.RichTextBox> 控制項。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## 範例  
 下列程式碼會以程式設計方式在使用者於 <xref:System.Windows.Controls.RichTextBox> 內按一下時選取任意文字。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## 請參閱  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)