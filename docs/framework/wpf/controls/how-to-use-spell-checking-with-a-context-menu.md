---
title: "如何：使用內容功能表的拼字檢查"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 257f343a7fa01e251159797a83e89b533292b6b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>如何：使用內容功能表的拼字檢查
根據預設，當您啟用編輯控制項中的拼字檢查就像<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>，您取得內容功能表中的拼字檢查的選項。 例如，當使用者以滑鼠右鍵按一下拼錯的字，他們會取得一組選項或拼字建議**全部忽略**。 不過，當您覆寫預設內容功能表，以您自己的自訂內容功能表，這項功能將會遺失，而且您需要撰寫程式碼以重新啟用拼字檢查功能的內容功能表。 下列範例示範如何啟用此<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列範例所示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]會建立<xref:System.Windows.Controls.TextBox>與用來實作快顯功能表某些事件。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列範例會示範實作快顯功能表的程式碼。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 使用以達成此程式碼<xref:System.Windows.Controls.RichTextBox>類似。 傳遞至參數中的主要差異在於`GetSpellingError`方法。 如<xref:System.Windows.Controls.TextBox>，將插入號位置的整數索引：  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 如<xref:System.Windows.Controls.RichTextBox>，傳遞<xref:System.Windows.Documents.TextPointer>指定插入號位置：  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>另請參閱  
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [在文字編輯控制項中啟用拼字檢查](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [在文字方塊使用自訂內容功能表](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
