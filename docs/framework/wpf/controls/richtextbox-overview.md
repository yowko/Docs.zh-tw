---
title: RichTextBox 概觀
description: '瞭解 Windows Presentation Foundation RichTextBox 控制項如何讓使用者顯示或編輯文字、影像和資料表這類內容。 請參閱 XAML 和 c # 範例。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166240"
---
# <a name="richtextbox-overview"></a>RichTextBox 概觀

<xref:System.Windows.Controls.RichTextBox>控制項可讓您顯示或編輯流程內容，包括段落、影像、資料表等等。 本主題介紹 <xref:System.Windows.Controls.TextBox> 類別，並提供如何在和 c # 中使用它的範例 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？

<xref:System.Windows.Controls.RichTextBox>和都 <xref:System.Windows.Controls.TextBox> 可讓使用者編輯文字，但在不同的案例中會使用這兩個控制項。 <xref:System.Windows.Controls.RichTextBox>當使用者需要編輯格式化的文字、影像、資料表或其他豐富內容時，是較好的選擇。 例如，編輯需要格式化、影像等的檔、發行項或 blog，最好是使用來完成 <xref:System.Windows.Controls.RichTextBox> 。 A <xref:System.Windows.Controls.TextBox> 需要較少的系統資源 <xref:System.Windows.Controls.RichTextBox> ，而且在只需要編輯純文字（也就是表單的使用方式）時非常理想。 如需的詳細資訊，請參閱[TextBox 總覽](textbox-overview.md) <xref:System.Windows.Controls.TextBox> 。 下表摘要說明和的主要功能 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。

|控制|即時拼字檢查|操作功能表|格式化命令，例如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （Ctr + B）|<xref:System.Windows.Documents.FlowDocument>影像、段落、資料表等內容|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|是|是|否|不會。|
|<xref:System.Windows.Controls.RichTextBox>|是|是|是|是|

> [!NOTE]
> 雖然不 <xref:System.Windows.Controls.TextBox> 支援格式化相關 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> 的命令（如（Ctr + B）），但這兩個控制項都支援許多基本命令，例如 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> 。

稍後會更詳細說明上表中的功能。

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>建立 RichTextBox

下列程式碼示範如何建立 <xref:System.Windows.Controls.RichTextBox> 使用者可以在中編輯豐富內容的。

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

具體而言，在中編輯的內容 <xref:System.Windows.Controls.RichTextBox> 是「流動內容」。 非固定格式內容可以包含許多型別的元素，包括格式化文字、影像、清單及表格。 如需有關非固定格式文件的深入資訊，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。 為了包含非固定格式內容，會 <xref:System.Windows.Controls.RichTextBox> 主控 <xref:System.Windows.Documents.FlowDocument> 物件，而後者又包含可編輯的內容。 為了示範中的流程內容 <xref:System.Windows.Controls.RichTextBox> ，下列程式碼顯示如何 <xref:System.Windows.Controls.RichTextBox> 使用段落和一些粗體文字來建立。

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

下圖顯示此範例的轉譯方式。

![具有內容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

和之類 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Bold> 的元素會決定中的內容如何 <xref:System.Windows.Controls.RichTextBox> 出現。 當使用者編輯 <xref:System.Windows.Controls.RichTextBox> 內容時，會變更此流程內容。 若要深入了解非固定格式內容的功能及如何與其搭配運作，請參閱[非固定格式文件概觀](../advanced/flow-document-overview.md)。

> [!NOTE]
> 內的 <xref:System.Windows.Controls.RichTextBox> 非固定格式內容，其行為與其他控制項中所包含的流程內容完全相同。 例如，中沒有任何資料行， <xref:System.Windows.Controls.RichTextBox> 因此不會自動調整大小行為。 此外，內建功能（例如搜尋、視圖模式、頁面流覽和縮放）無法在中使用 <xref:System.Windows.Controls.RichTextBox> 。

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>即時拼字檢查

您可以在或中啟用即時拼寫檢查 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。

![具有拼寫&#45;檢查的 Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。

<a name="context_menu"></a>

## <a name="context-menu"></a>操作功能表

根據預設， <xref:System.Windows.Controls.TextBox> 和都會 <xref:System.Windows.Controls.RichTextBox> 有一個內容功能表，當使用者在控制項內按一下滑鼠右鍵時，就會出現此功能表。 使用者可以使用此操作功能表來剪下、複製或貼上 (請見下圖)。

![具有內容功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_CoNtext_Menu")

您可以建立自己的自訂操作功能表來覆寫預設的操作功能表。 如需詳細資訊，請參閱[在 RichTextBox 中放置自訂內容功能表](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>編輯命令

編輯命令可讓使用者在內設定可編輯內容的格式 <xref:System.Windows.Controls.RichTextBox> 。 除了基本的編輯命令之外， <xref:System.Windows.Controls.RichTextBox> 還包括不支援的格式化命令 <xref:System.Windows.Controls.TextBox> 。 例如，在中編輯時 <xref:System.Windows.Controls.RichTextBox> ，使用者可以按 Ctr + B 來切換粗體文字格式。 <xref:System.Windows.Documents.EditingCommands>如需可用命令的完整清單，請參閱。 除了使用鍵盤快速鍵之外，您還可以將命令與其他控制項 (例如按鈕) 連接。 下列範例示範如何建立一個簡單的工具列，其中包含使用者可用來變更文字格式設定的按鈕。

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

下圖顯示此範例的顯示方式。

![具有工具列的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>偵測內容變更

通常 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 應該使用事件來偵測中的文字， <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 變更，而不是 <xref:System.Windows.UIElement.KeyDown> 您預期的方式。 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>儲存、載入和列印 RichTextBox 內容

下列範例示範如何將的內容儲存至檔案 <xref:System.Windows.Controls.RichTextBox> 、將該內容載入回 <xref:System.Windows.Controls.RichTextBox> ，並列印內容。 以下是此範例的標記。

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

以下是此範例的程式碼後置。

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>另請參閱

- [操作說明主題](richtextbox-how-to-topics.md)
- [TextBox 概觀](textbox-overview.md)
