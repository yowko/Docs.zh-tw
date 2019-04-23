---
title: RichTextBox 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 9aa0d33b3cb2c15ba9c1cb7e7d7be9a3125f66d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162707"
---
# <a name="richtextbox-overview"></a>RichTextBox 概觀
<xref:System.Windows.Controls.RichTextBox>控制項可讓您顯示或編輯非固定格式內容，包括段落、 影像、 資料表等等。 本主題將介紹<xref:System.Windows.Controls.TextBox>類別，並提供範例，示範如何使用它在這兩[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和C#。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 兩者<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Controls.TextBox>允許使用者編輯文字，不過，不同的案例中使用兩個控制項。 A<xref:System.Windows.Controls.RichTextBox>時所需的使用者編輯格式化的文字、 影像、 表格或其他豐富的內容是較好的選擇。 例如，編輯文件、 文件或需要格式化的部落格映像、 使用最適合完成等<xref:System.Windows.Controls.RichTextBox>。 A<xref:System.Windows.Controls.TextBox>需要較少的系統資源則<xref:System.Windows.Controls.RichTextBox>僅純文字格式必須為編輯 （也就是表單中的使用量） 時相當理想。 請參閱[TextBox 概觀](textbox-overview.md)如需有關<xref:System.Windows.Controls.TextBox>。 下表摘要說明的主要特色<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>。  
  
|控制項|即時拼字檢查|操作功能表|之類的格式化命令<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)|<xref:System.Windows.Documents.FlowDocument> 例如影像、 段落、 資料表等內容。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是|是|  
  
 **注意：** 雖然<xref:System.Windows.Controls.TextBox>不支援之類的格式化相關的命令<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)，例如許多基本命令支援這兩個控制項<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>。  
  
 稍後會更詳細說明上表中的功能。  
  
<a name="creating_a_richtextbox"></a>   
## <a name="creating-a-richtextbox"></a>建立 RichTextBox  
 下列程式碼示範如何建立<xref:System.Windows.Controls.RichTextBox>使用者可以編輯豐富的內容中。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 具體來說，在 編輯內容<xref:System.Windows.Controls.RichTextBox>是非固定格式內容。 非固定格式內容可以包含許多型別的元素，包括格式化文字、影像、清單及表格。 如需有關非固定格式文件的深入資訊，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。 為了包含非固定格式內容<xref:System.Windows.Controls.RichTextBox>主機<xref:System.Windows.Documents.FlowDocument>物件，其中又包含可編輯的內容。 為了示範中的非固定格式內容<xref:System.Windows.Controls.RichTextBox>，下列程式碼示範如何建立<xref:System.Windows.Controls.RichTextBox>具有段落及一些粗體文字。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 下圖顯示此範例的轉譯方式。  
  
 ![具有內容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")  
  
 項目要<xref:System.Windows.Documents.Paragraph>並<xref:System.Windows.Documents.Bold>判斷如何內容內<xref:System.Windows.Controls.RichTextBox>隨即出現。 當使用者編輯<xref:System.Windows.Controls.RichTextBox>內容，他們會變更這個非固定格式內容。 若要深入了解非固定格式內容的功能及如何與其搭配運作，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。  
  
 **注意：** 非固定格式內容內<xref:System.Windows.Controls.RichTextBox>完全和其他控制項中所包含的非固定格式內容行為不。 例如，沒有資料行中的<xref:System.Windows.Controls.RichTextBox>和因此沒有自動調整大小行為。 此外，內建功能，例如搜尋、 檢視模式、 頁面導覽和縮放內也不提供<xref:System.Windows.Controls.RichTextBox>。  
  
<a name="realtime_spellechecking"></a>   
## <a name="real-time-spell-checking"></a>即時拼字檢查  
 您可以即時中啟用拼字檢查<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![具有拼字檢查功能的 TextBox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
<a name="context_menu"></a>   
## <a name="context-menu"></a>操作功能表  
 根據預設，同時<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>有使用者以滑鼠右鍵按一下控制項內部時，會出現內容功能表。 使用者可以使用此操作功能表來剪下、複製或貼上 (請見下圖)。  
  
 ![具有操作功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 您可以建立自己的自訂操作功能表來覆寫預設的操作功能表。 如需詳細資訊，請參閱[在 RichTextBox 中放置自訂內容功能表](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。  
  
<a name="detect_when_content_changes"></a>   
## <a name="editing-commands"></a>編輯命令  
 編輯命令讓使用者可編輯的內容內格式化<xref:System.Windows.Controls.RichTextBox>。 除了基本編輯命令，<xref:System.Windows.Controls.RichTextBox>包含格式化命令<xref:System.Windows.Controls.TextBox>不支援。 例如，在編輯時<xref:System.Windows.Controls.RichTextBox>，使用者可以按 Ctr + B 來切換粗體文字格式設定。 請參閱<xref:System.Windows.Documents.EditingCommands>如需可用命令的完整清單。 除了使用鍵盤快速鍵之外，您還可以將命令與其他控制項 (例如按鈕) 連接。 下列範例示範如何建立一個簡單的工具列，其中包含使用者可用來變更文字格式設定的按鈕。  
  
 [!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 下圖顯示此範例的顯示方式。  
  
 ![具有工具列的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_Content")  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件應該用來偵測中的文字<xref:System.Windows.Controls.TextBox>或是<xref:System.Windows.Controls.RichTextBox>而不是變更<xref:System.Windows.UIElement.KeyDown>跟您預期的一樣。 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## <a name="save-load-and-print-richtextbox-content"></a>儲存、載入和列印 RichTextBox 內容  
 下列範例示範如何將儲存的內容<xref:System.Windows.Controls.RichTextBox>檔案，以載入該內容的恢復為<xref:System.Windows.Controls.RichTextBox>，以及列印內容。 以下是此範例的標記。  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 以下是此範例的程式碼後置。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [HOW-TO 主題](richtextbox-how-to-topics.md)
- [TextBox 概觀](textbox-overview.md)
