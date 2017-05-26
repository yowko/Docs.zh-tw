---
title: "RichTextBox 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "控制項, RichTextBox"
  - "RichTextBox 控制項 [WPF], 關於 RichTextBox 控制項"
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# RichTextBox 概觀
<xref:System.Windows.Controls.RichTextBox> 控制項可讓您顯示或編輯非固定格式內容，包括段落、影像、表格等等。  本主題介紹 <xref:System.Windows.Controls.TextBox> 類別，並提供如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和 [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] 中使用的範例。  
  
   
  
<a name="textbox_or_richtextbox"></a>   
## TextBox 或是 RichTextBox  
 <xref:System.Windows.Controls.RichTextBox> 與 <xref:System.Windows.Controls.TextBox> 皆可讓使用者編輯文字，但這兩個控制項適用於不同的案例中。  當使用者需要編輯格式化文字、影像、表格或其他豐富的內容時，<xref:System.Windows.Controls.RichTextBox> 是比較好的選擇。  例如，編輯需要格式化、影像等等的文件、文章或網誌時，最好使用 <xref:System.Windows.Controls.RichTextBox> 來完成。  <xref:System.Windows.Controls.TextBox> 需要的系統資源比 <xref:System.Windows.Controls.RichTextBox> 少，因此在只需要編輯純文字時 \(例如  表單用途\)，這是比較理想的選擇。  如需 <xref:System.Windows.Controls.TextBox> 的詳細資訊，請參閱 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)。  下表摘要說明 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.RichTextBox> 的主要功能。  
  
|控制項|即時拼字檢查|內容功能表|<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\) 之類的格式化命令|影像、段落、表格之類的 <xref:System.Windows.Documents.FlowDocument> 內容|  
|---------|------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是|是|  
  
 **注意**：雖然 <xref:System.Windows.Controls.TextBox> 不支援 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\) 之類的格式化相關編輯命令，但是這兩個控制項都支援許多基本命令，如 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>。  
  
 稍後會詳細說明上表中的功能。  
  
<a name="creating_a_richtextbox"></a>   
## 建立 RichTextBox  
 下列程式碼顯示如何建立可供使用者編輯豐富內容的 <xref:System.Windows.Controls.RichTextBox>。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]  
  
 具體來說，以 <xref:System.Windows.Controls.RichTextBox> 編輯的內容即為非固定格式內容。  非固定格式內容可包含許多項目類型，包括格式化文字、影像、清單與表格等。  如需非固定格式文件的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  若要包含非固定格式內容，<xref:System.Windows.Controls.RichTextBox> 必須裝載 \(Host\) <xref:System.Windows.Documents.FlowDocument> 物件，再由此物件包含可編輯的內容。  為了以 <xref:System.Windows.Controls.RichTextBox> 示範非固定格式內容，下列程式碼將顯示如何使用段落與某些粗體文字建立 <xref:System.Windows.Controls.RichTextBox>。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]  
  
 [!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
 [!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]  
  
 下圖顯示這個範例的呈現情形。  
  
 ![具有內容的 RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-content.png "Editing\_RichTextBox\_with\_Content")  
  
 <xref:System.Windows.Documents.Paragraph> 與 <xref:System.Windows.Documents.Bold> 等項目可決定 <xref:System.Windows.Controls.RichTextBox> 內之內容的顯示方式。  當使用者編輯 <xref:System.Windows.Controls.RichTextBox> 內容時，將會變更這個非固定格式內容。  若想進一步了解非固定格式內容的功能及其使用方式，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
 **注意**：<xref:System.Windows.Controls.RichTextBox> 內的非固定格式內容展現的行為與其他控制項中的非固定格式內容不完全相同。  例如，<xref:System.Windows.Controls.RichTextBox> 中並沒有欄位，因此不會有自動調整大小的行為。  此外，<xref:System.Windows.Controls.RichTextBox> 內並沒有搜尋、檢視模式、頁面巡覽與縮放等內建功能。  
  
<a name="realtime_spellechecking"></a>   
## 即時拼字檢查  
 您可以在 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 中啟用即時拼字檢查。  啟用拼字檢查時，拼錯的文字下方會出現紅色線條 \(請見下圖\)。  
  
 ![具有拼字檢查功能的 Textbox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱 [在文字編輯控制項中啟用拼字檢查](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
<a name="context_menu"></a>   
## 內容功能表  
 根據預設，<xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.RichTextBox> 都具有使用者於控制項內以滑鼠右鍵按一下即會顯示的內容功能表。  內容功能表可以讓使用者剪下、複製或貼上文字 \(請見下圖\)。  
  
 ![具有內容功能表的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 您可以建立自訂的內容功能表來覆寫預設的功能表。  如需詳細資訊，請參閱 [在 RichTextBox 中放置自訂內容功能表](../../../../docs/framework/wpf/controls/how-to-position-a-custom-context-menu-in-a-richtextbox.md)。  
  
<a name="detect_when_content_changes"></a>   
## 編輯命令  
 編輯命令可讓使用者對 <xref:System.Windows.Controls.RichTextBox> 內的可編輯內容進行格式化。  除了基本的編輯命令外，<xref:System.Windows.Controls.RichTextBox> 還包含 <xref:System.Windows.Controls.TextBox> 不支援的格式化命令。  例如，在 <xref:System.Windows.Controls.RichTextBox> 內編輯時，使用者可以按 Ctr\+B 切換粗體文字格式。  如需可用命令的完整清單，請參閱 <xref:System.Windows.Documents.EditingCommands>。  除了使用鍵盤快速鍵以外，您也可以將命令與按鈕等其他控制項產生關聯。  下列範例顯示如何建立簡單的工具列，讓使用者可利用其中的按鈕變更文字格式。  
  
 [!code-xml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]  
  
 下圖顯示這個範例的顯示情形。  
  
 ![具有工具列的 RichTextBox](../../../../docs/framework/wpf/controls/media/editing-richtextbox-with-toobar.png "Editing\_RichTextBox\_with\_TooBar")  
  
<a name="editing_commands"></a>   
## 偵測內容變更  
 通常，每當 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 中的文字有所變更時，就應使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件來偵測，而不是如您預期的 <xref:System.Windows.UIElement.KeyDown>。  如需範例，請參閱 [偵測 TextBox 中的文字何時變更](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
<a name="save_load_and_print_richtextbox_content"></a>   
## 儲存、載入和列印 RichTextBox 內容  
 下列範例顯示如何將 <xref:System.Windows.Controls.RichTextBox> 的內容儲存至檔案、將該內容重新載入 <xref:System.Windows.Controls.RichTextBox>，以及列印內容。  以下是此範例的標記。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
 此範例的程式碼後置如下。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## 請參閱  
 [HOW TO 主題](../../../../docs/framework/wpf/controls/richtextbox-how-to-topics.md)   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)