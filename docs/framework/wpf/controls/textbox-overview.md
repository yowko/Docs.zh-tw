---
title: TextBox 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 46600fd1a3023a80d49fae6f020279be6131916a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951478"
---
# <a name="textbox-overview"></a>TextBox 概觀
<xref:System.Windows.Controls.TextBox>類別可讓您顯示或編輯未格式化的文字。 的常見用法<xref:System.Windows.Controls.TextBox>是在表單中編輯未格式化的文字。 例如, 要求使用者名稱、電話號碼等的表單會使用<xref:System.Windows.Controls.TextBox>控制項來輸入文字。 本主題介紹<xref:System.Windows.Controls.TextBox>類別, 並提供如何[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]在和C#中使用它的範例。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 <xref:System.Windows.Controls.TextBox> 和<xref:System.Windows.Controls.RichTextBox>都可讓使用者輸入文字, 但在不同的案例中會使用兩個控制項。 A <xref:System.Windows.Controls.TextBox>需要較少的系統資源<xref:System.Windows.Controls.RichTextBox> , 如此一來, 當只需要編輯純文字 (亦即, 表單中的使用方式) 時, 這是理想的選擇。 當使用者需要編輯格式化的文字、影像、資料表或其他支援的內容時,是較好的選擇。<xref:System.Windows.Controls.RichTextBox> 例如, 編輯需要格式化、影像等的檔、發行項或 blog, 最好是使用<xref:System.Windows.Controls.RichTextBox>來完成。 下表摘要說明<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBox>的主要功能。  
  
|控制項|即時拼字檢查|操作功能表|格式化命令, <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>例如 (Ctr + B)|<xref:System.Windows.Documents.FlowDocument>影像、段落、資料表等內容|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|資料分割|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|  
  
> [!NOTE]
> 雖然<xref:System.Windows.Controls.TextBox>不支援格式化相關的編輯<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>命令 (如 (Ctr + B)), 但這兩個控制項都支援許多<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>基本命令, 例如。 如需詳細資訊，請參閱 <xref:System.Windows.Documents.EditingCommands>。  
  
 下列各節<xref:System.Windows.Controls.TextBox>涵蓋支援的功能。 如需的詳細<xref:System.Windows.Controls.RichTextBox>資訊, 請參閱[RichTextBox 總覽](richtextbox-overview.md)。  
  
### <a name="real-time-spellchecking"></a>即時拼字檢查  
 您可以在<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>中啟用即時拼寫檢查。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![具有拼字檢查功能的 TextBox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### <a name="context-menu"></a>操作功能表  
 根據預設, 和<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>都會有一個內容功能表, 當使用者在控制項內按一下滑鼠右鍵時, 就會出現此功能表。 操作功能表可以讓使用者剪下、複製或貼上 (請見下圖)。  
  
 ![具有操作功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 您可以建立自訂操作功能表來覆寫預設行為。 如需詳細資訊，請參閱[搭配 TextBox 使用自訂操作功能表](how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>建立 TextBox  
 <xref:System.Windows.Controls.TextBox>可以是高度的單行或組成多行。 單行<xref:System.Windows.Controls.TextBox>最適合用來輸入少量的純文字 (亦即,表單中的「名稱」、「電話號碼」等)。 下列範例顯示如何建立單行<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您也可以建立<xref:System.Windows.Controls.TextBox> , 讓使用者輸入多行文字。 例如, 如果您的表單要求使用者的自傳草圖, 您會想要使用<xref:System.Windows.Controls.TextBox>支援多行文字的。 下列範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來<xref:System.Windows.Controls.TextBox>定義會自動展開以容納多行文字的控制項。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 將屬性設定為`Wrap` , 會在到達<xref:System.Windows.Controls.TextBox>控制項的邊緣時, 讓文字換行至新的一行, 並視<xref:System.Windows.Controls.TextBox>需要自動展開控制項以包含新行的空間。 <xref:System.Windows.Controls.TextBox.TextWrapping%2A>  
  
 當按下 enter `true`鍵時, 將<xref:System.Windows.Controls.TextBox>屬性設定為會插入新的一行, 然後再次自動展開以包含新行的空間 (如有需要)。 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>  
  
 屬性會將捲軸加入<xref:System.Windows.Controls.TextBox>至, 因此, 如果展開的<xref:System.Windows.Controls.TextBox>內容超出環繞其範圍的框架或視窗大小, 就可以滾動到。 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>  
  
 如需與使用<xref:System.Windows.Controls.TextBox>相關聯之不同工作的詳細資訊, 請參閱 how [to 主題](textbox-how-to-topics.md)。  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常應該使用<xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox>事件來偵測<xref:System.Windows.UIElement.KeyDown>或中的文字何時變更, 而不是您預期的情況。 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## <a name="see-also"></a>另請參閱

- [HOW-TO 主題](textbox-how-to-topics.md)
- [RichTextBox 概觀](richtextbox-overview.md)
