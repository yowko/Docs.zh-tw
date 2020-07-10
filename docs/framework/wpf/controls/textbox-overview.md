---
title: TextBox 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 86b2cf8cb0c72186fd92bdad0af6bf5bd3fa9f3f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174428"
---
# <a name="textbox-overview"></a>TextBox 概觀
<xref:System.Windows.Controls.TextBox>類別可讓您顯示或編輯未格式化的文字。 的常見用法 <xref:System.Windows.Controls.TextBox> 是在表單中編輯未格式化的文字。 例如，要求使用者名稱、電話號碼等的表單會使用 <xref:System.Windows.Controls.TextBox> 控制項來輸入文字。 本主題介紹 <xref:System.Windows.Controls.TextBox> 類別，並提供如何在和 c # 中使用它的範例 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 <xref:System.Windows.Controls.TextBox>和都 <xref:System.Windows.Controls.RichTextBox> 可讓使用者輸入文字，但在不同的案例中會使用兩個控制項。 A <xref:System.Windows.Controls.TextBox> 需要較少的系統資源， <xref:System.Windows.Controls.RichTextBox> 如此一來，只有在只需要編輯純文字時，才是理想的選擇 (也就是表單) 中的使用方式。 <xref:System.Windows.Controls.RichTextBox>當使用者需要編輯格式化的文字、影像、資料表或其他支援的內容時，是較好的選擇。 例如，編輯需要格式化、影像等的檔、發行項或 blog，最好是使用來完成 <xref:System.Windows.Controls.RichTextBox> 。 下表摘要說明和的主要功能 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。  
  
|控制|即時拼字檢查|操作功能表|格式化命令，例如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B) |<xref:System.Windows.Documents.FlowDocument>影像、段落、資料表等內容|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|  
  
> [!NOTE]
> 雖然不 <xref:System.Windows.Controls.TextBox> 支援格式化相關的編輯命令（如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr + B) ），但這兩個控制項都支援許多基本命令，例如 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> 。 如需相關資訊，請參閱 <xref:System.Windows.Documents.EditingCommands> 。  
  
 <xref:System.Windows.Controls.TextBox>下列各節涵蓋支援的功能。 如需的詳細資訊 <xref:System.Windows.Controls.RichTextBox> ，請參閱[RichTextBox 總覽](richtextbox-overview.md)。  
  
### <a name="real-time-spellchecking"></a>即時拼字檢查  
 您可以在或中啟用即時拼寫檢查 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![具有拼寫&#45;檢查的 Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### <a name="context-menu"></a>操作功能表  
 根據預設， <xref:System.Windows.Controls.TextBox> 和都會 <xref:System.Windows.Controls.RichTextBox> 有一個內容功能表，當使用者在控制項內按一下滑鼠右鍵時，就會出現此功能表。 操作功能表可以讓使用者剪下、複製或貼上 (請見下圖)。  
  
 ![具有內容功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_CoNtext_Menu")  
  
 您可以建立自訂操作功能表來覆寫預設行為。 如需詳細資訊，請參閱[搭配 TextBox 使用自訂操作功能表](how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>建立 TextBox  
 <xref:System.Windows.Controls.TextBox>可以是高度的單行或組成多行。 單一行 <xref:System.Windows.Controls.TextBox> 最適合用來在表單) 中輸入少量的純文字 (例如「名稱」、「電話號碼」等等。 下列範例顯示如何建立單行 <xref:System.Windows.Controls.TextBox> 。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您也可以建立 <xref:System.Windows.Controls.TextBox> ，讓使用者輸入多行文字。 例如，如果您的表單要求使用者的自傳草圖，您會想要使用 <xref:System.Windows.Controls.TextBox> 支援多行文字的。 下列範例示範如何使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 來定義 <xref:System.Windows.Controls.TextBox> 會自動展開以容納多行文字的控制項。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 將 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 屬性設定為，會在 `Wrap` 到達控制項的邊緣時，讓文字換行至新的一行，並視 <xref:System.Windows.Controls.TextBox> 需要自動展開 <xref:System.Windows.Controls.TextBox> 控制項以包含新行的空間。  
  
 當 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> `true` 按下 enter 鍵時，將屬性設定為會插入新的一行，然後再次自動展開 <xref:System.Windows.Controls.TextBox> 以包含新行的空間（如有需要）。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性會將捲軸加入至 <xref:System.Windows.Controls.TextBox> ，因此， <xref:System.Windows.Controls.TextBox> 如果展開的內容 <xref:System.Windows.Controls.TextBox> 超出環繞其範圍的框架或視窗大小，就可以滾動到。  
  
 如需與使用相關聯之不同工作的詳細資訊 <xref:System.Windows.Controls.TextBox> ，請參閱 how [to 主題](textbox-how-to-topics.md)。  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 應該使用事件來偵測或中的文字何時 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 變更，而不是 <xref:System.Windows.UIElement.KeyDown> 您預期的情況。 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## <a name="see-also"></a>另請參閱

- [操作說明主題](textbox-how-to-topics.md)
- [RichTextBox 概觀](richtextbox-overview.md)
