---
title: HOW TO：使用操作功能表的拼字檢查
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 72b24c386eb99140c9c2729688994b81f92e1a6f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192975"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>HOW TO：使用操作功能表的拼字檢查
根據預設，當您啟用編輯控制項中的拼字檢查像是<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>，您取得操作功能表中的拼字檢查的選項。 比方說，當使用者以滑鼠右鍵按一下拼錯的字，他們會取得一組拼字建議或選擇**全部略過**。 不過，當您覆寫預設的內容功能表，以您自己的自訂內容功能表，這項功能將會遺失，而且您需要撰寫程式碼，以重新啟用快顯功能表的拼字檢查功能。 下列範例示範如何在啟用此<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>範例  
 下列範例所示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來建立<xref:System.Windows.Controls.TextBox>與用來實作快顯功能表的某些事件。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>範例  
 下列範例顯示實作快顯功能表的程式碼。  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 用來執行此程式碼<xref:System.Windows.Controls.RichTextBox>類似。 傳遞至參數中的主要差異在於`GetSpellingError`方法。 針對<xref:System.Windows.Controls.TextBox>，將插入號位置的整數索引：  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 針對<xref:System.Windows.Controls.RichTextBox>，傳遞<xref:System.Windows.Documents.TextPointer>指定插入號位置：  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
- [在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [在文字方塊使用自訂內容功能表](how-to-use-a-custom-context-menu-with-a-textbox.md)
