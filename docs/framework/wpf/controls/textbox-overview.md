---
title: TextBox 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 9fbae5ac4de4c78a1086bcbd9bfc9e01eb597fb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186635"
---
# <a name="textbox-overview"></a>TextBox 概觀
該<xref:System.Windows.Controls.TextBox>類使您能夠顯示或編輯未格式化的文本。 的常見用途<xref:System.Windows.Controls.TextBox>是編輯表單中未格式化的文本。 例如，要求使用者名、電話號碼等的表單將使用<xref:System.Windows.Controls.TextBox>控制項進行文本輸入。 本主題介紹類<xref:System.Windows.Controls.TextBox>，並提供如何在 C#[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中使用它的示例。  

<a name="textbox_or_richtextbox"></a>
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 和<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.RichTextBox>都允許使用者輸入文本，但這兩個控制項用於不同的方案。 A<xref:System.Windows.Controls.TextBox>需要較少的系統資源，<xref:System.Windows.Controls.RichTextBox>因此，當僅需要編輯純文字（即表單中的用法）時，它是理想的選擇。 當使用者<xref:System.Windows.Controls.RichTextBox>需要編輯格式化的文本、圖像、表格或其他支援的內容時，是更好的選擇。 例如，最好使用<xref:System.Windows.Controls.RichTextBox>完成需要格式設置的文檔、文章或博客。 下表總結了<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBox>的主要特徵。  
  
|控制|即時拼字檢查|操作功能表|格式化命令（Ctr+B） <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>|<xref:System.Windows.Documents.FlowDocument>內容，如圖像、段落、表格等。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|  
  
> [!NOTE]
> 儘管<xref:System.Windows.Controls.TextBox>不支援格式化相關編輯命令（如<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>Ctr_B），但許多基本命令都受這兩個控制項（如<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>） 的支援。 如需相關資訊，請參閱 <xref:System.Windows.Documents.EditingCommands>。  
  
 下面各節<xref:System.Windows.Controls.TextBox>介紹了支援的功能。 有關 的詳細資訊<xref:System.Windows.Controls.RichTextBox>，請參閱[富文字方塊概述](richtextbox-overview.md)。  
  
### <a name="real-time-spellchecking"></a>即時拼字檢查  
 您可以在<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>中啟用即時拼寫檢查。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![帶有拼寫&#45;檢查的文字方塊](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### <a name="context-menu"></a>操作功能表  
 預設情況下，當<xref:System.Windows.Controls.RichTextBox>使用者<xref:System.Windows.Controls.TextBox>按右鍵控制項內部時，兩者都有一個內容功能表。 操作功能表可以讓使用者剪下、複製或貼上 (請見下圖)。  
  
 ![具有內容功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_CoNtext_Menu")  
  
 您可以建立自訂操作功能表來覆寫預設行為。 如需詳細資訊，請參閱[搭配 TextBox 使用自訂操作功能表](how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>
## <a name="creating-textboxes"></a>建立 TextBox  
 A<xref:System.Windows.Controls.TextBox>可以是一條高線，也可以由多條線組成。 單行<xref:System.Windows.Controls.TextBox>最適合輸入少量純文字（即"名稱"、"電話號碼"等）。 下面的示例演示如何創建單行<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您還可以創建 允許使用者輸入<xref:System.Windows.Controls.TextBox>多行文本的 。 例如，如果您的表單要求使用者繪製履歷草圖，則您想要使用支援多行文本的 。 <xref:System.Windows.Controls.TextBox> 下面的示例演示如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定義自動展開以適應多<xref:System.Windows.Controls.TextBox>行文本的控制項。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 將<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性設置為`Wrap`使文本在到達<xref:System.Windows.Controls.TextBox>控制項邊緣時換行到新行，如有必要，自動展開<xref:System.Windows.Controls.TextBox>控制項以包括新行的空間。  
  
 將<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性設置為在`true`按下 RETURN 鍵時插入新行，如有必要，再次自動展開<xref:System.Windows.Controls.TextBox>以包括新行的空間。  
  
 屬性<xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>向<xref:System.Windows.Controls.TextBox>中添加捲軸，以便在<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.TextBox>展開超出包含它的框架或視窗的大小時，可以滾動流覽 的內容。  
  
 有關與 使用 相關的不同任務的詳細資訊，<xref:System.Windows.Controls.TextBox>請參閱["如何執行主題](textbox-how-to-topics.md)"。  
  
<a name="editing_commands"></a>
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常，<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>該事件應用於檢測 或<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.RichTextBox>更改中的文本，而不是<xref:System.Windows.UIElement.KeyDown>如您所料。 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## <a name="see-also"></a>另請參閱

- [如何使用主題](textbox-how-to-topics.md)
- [RichTextBox 概觀](richtextbox-overview.md)
