---
title: "TextBox 概觀 | Microsoft Docs"
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
  - "控制項, TextBox"
  - "TextBox 控制項, 關於 TextBox 控制項"
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# TextBox 概觀
<xref:System.Windows.Controls.TextBox> 類別可以讓您顯示或編輯未格式化的文字。  <xref:System.Windows.Controls.TextBox> 的一般用途是編輯表單中未格式化的文字。  例如，要求使用者填入姓名、電話號碼等資訊的表單會使用 <xref:System.Windows.Controls.TextBox> 控制項提供使用者輸入文字。  本主題介紹 <xref:System.Windows.Controls.TextBox> 類別，並提供如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和 [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] 中使用的範例。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="textbox_or_richtextbox"></a>   
## TextBox 或是 RichTextBox  
 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.RichTextBox> 都能夠讓使用者輸入文字，但是這兩個控制項適用於不同的情況。  <xref:System.Windows.Controls.TextBox> 需要的系統資源比 <xref:System.Windows.Controls.RichTextBox> 少，因此當只需要編輯純文字時 \(例如表單用途\) 時是比較理想的選擇。  <xref:System.Windows.Controls.RichTextBox> 在需要使用者編輯格式化文字、影像、表格或其他支援的內容時是比較好的選擇。  例如，編輯需要格式化、影像等等的文件、文章或網誌時，最好使用 <xref:System.Windows.Controls.RichTextBox> 來完成。  下表摘要說明 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBox> 的主要功能。  
  
|控制項|即時拼字檢查|內容功能表|<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\) 之類的格式化命令|影像、段落、表格之類的 <xref:System.Windows.Documents.FlowDocument> 內容|  
|---------|------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|有 \(請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)\)|有 \(請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)\)|  
  
> [!NOTE]
>  雖然 <xref:System.Windows.Controls.TextBox> 不支援像 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> \(Ctr\+B\) 之類的格式化相關編輯命令，但是這兩個控制項都支援許多基本命令，像是 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>。  如需詳細資訊，請參閱 <xref:System.Windows.Documents.EditingCommands>。  
  
 下列章節涵蓋 <xref:System.Windows.Controls.TextBox> 支援的功能。  如需 <xref:System.Windows.Controls.RichTextBox> 的詳細資訊，請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)。  
  
### 即時拼字檢查  
 您可以在 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 中啟用即時拼字檢查。  啟用拼字檢查時，拼錯的文字下方會出現紅色線條 \(請見下圖\)。  
  
 ![具有拼字檢查功能的 Textbox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing\_TextBox\_with\_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱 [在文字編輯控制項中啟用拼字檢查](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### 內容功能表  
 根據預設，<xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.RichTextBox> 都具有使用者於控制項內以滑鼠右鍵按一下即會顯示的內容功能表。  內容功能表可以讓使用者剪下、複製或貼上文字 \(請見下圖\)。  
  
 ![具有內容功能表的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing\_TextBox\_with\_Context\_Menu")  
  
 您可以建立自訂的內容功能表來覆寫預設的行為。  如需詳細資訊，請參閱 [在文字方塊使用自訂內容功能表](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>   
## 建立 TextBox  
 <xref:System.Windows.Controls.TextBox> 可以是單行或由多行組成。  單行 <xref:System.Windows.Controls.TextBox> 對於輸入少量的純文字來說效果最佳 \(例如，  表單中的 \[名稱\]、  \[電話號碼\] 等\)。  下列範例顯示如何建立單行 <xref:System.Windows.Controls.TextBox>。  
  
 [!code-xml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您也可以建立能讓使用者輸入多行文字的 <xref:System.Windows.Controls.TextBox>。  例如，如果您的表單要求使用者填入概略的自傳，即可以使用支援多行文字的 <xref:System.Windows.Controls.TextBox>。  下列範例會顯示如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義 <xref:System.Windows.Controls.TextBox> 控制項，該控制項會自動擴充以容納多行文字。  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 如果將 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 屬性設為 `Wrap`，會使得文字在碰到 <xref:System.Windows.Controls.TextBox> 控制項的邊緣時換行，必要時會自動擴充 <xref:System.Windows.Controls.TextBox> 控制項，以包含給新行的空間。  
  
 如果將 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 屬性設為 `true`，會使得在按下 RETURN 鍵時插入新行，同樣地，必要時會自動擴充 <xref:System.Windows.Controls.TextBox> 以包含給新行的空間。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> 屬性會將捲軸加入至 <xref:System.Windows.Controls.TextBox>，以在 <xref:System.Windows.Controls.TextBox> 的內容 <xref:System.Windows.Controls.TextBox> 擴充超過外圍框架或視窗的大小時，可以加以捲動。  
  
 如需與使用 <xref:System.Windows.Controls.TextBox> 相關之不同工作的詳細資訊，請參閱 [HOW TO 主題](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)。  
  
<a name="editing_commands"></a>   
## 偵測內容變更  
 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.RichTextBox> 中的文字變更通常應該是由 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件來偵測，而不是您可能以為的 <xref:System.Windows.UIElement.KeyDown> 事件。  如需範例，請參閱 [偵測 TextBox 中的文字何時變更](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## 請參閱  
 [HOW TO 主題](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)