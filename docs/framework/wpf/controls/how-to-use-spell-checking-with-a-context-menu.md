---
title: "如何：使用內容功能表的拼字檢查 | Microsoft Docs"
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
  - "在文字方塊中啟用拼字檢查 [WPF]"
  - "在文字方塊中重新啟用拼字檢查 [WPF]"
  - "具有內容功能表的拼字檢查 [WPF]"
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：使用內容功能表的拼字檢查
根據預設，當您在編輯控制項 \(例如 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox>\) 中啟用拼字檢查時，拼字檢查選項便會出現在內容功能表中。  例如，當使用者以滑鼠右鍵按一下拼錯的文字時，他們會取得一組拼字建議或 \[**全部忽略**\] 的選項。  不過，當您使用自己的自訂內容功能表覆寫預設內容功能表時，這項功能就會失效，而且您必須撰寫程式碼，以重新啟用內容功能表中的拼字檢查功能。  下列範例示範如何在 <xref:System.Windows.Controls.TextBox> 上啟用這項功能。  
  
## 範例  
 下列範例顯示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 使用用來實作內容功能表的幾項事件建立 <xref:System.Windows.Controls.TextBox>。  
  
 [!code-xml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## 範例  
 下列範例顯實作內容功能表的程式碼。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 對 <xref:System.Windows.Controls.RichTextBox> 執行這項動作的程式碼十分類似。  主要差異是傳遞到 `GetSpellingError` 方法的參數。  針對 <xref:System.Windows.Controls.TextBox>，請傳遞插入號 \(Caret\) 位置的整數索引：  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 針對 <xref:System.Windows.Controls.RichTextBox>，請傳遞指定插入號位置的 <xref:System.Windows.Documents.TextPointer>：  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## 請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [在文字編輯控制項中啟用拼字檢查](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)   
 [在文字方塊使用自訂內容功能表](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)