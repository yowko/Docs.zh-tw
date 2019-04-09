---
title: TextBox 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
ms.openlocfilehash: 577a12a0c04e5e3bfbfecb2c45263b684f0ffc17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162642"
---
# <a name="textbox-overview"></a>TextBox 概觀
<xref:System.Windows.Controls.TextBox>類別可讓您顯示或編輯未格式化的文字。 常見用法<xref:System.Windows.Controls.TextBox>編輯表單中的未格式化的文字。 例如，要求使用者的名稱、 電話號碼格式等會使用<xref:System.Windows.Controls.TextBox>文字輸入控制項。 本主題將介紹<xref:System.Windows.Controls.TextBox>類別，並提供範例，示範如何使用它在這兩[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和C#。  

<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 兩者<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>允許使用者輸入文字，但兩個控制項使用不同的情況。 A<xref:System.Windows.Controls.TextBox>需要較少的系統資源則<xref:System.Windows.Controls.RichTextBox>因此只能使用純文字需要進行編輯時很理想 （亦即，在表單中的使用量）。 A<xref:System.Windows.Controls.RichTextBox>是較好的選擇時所需的使用者編輯格式化的文字、 影像、 資料表或其他支援的內容。 例如，編輯文件、 文件或需要格式化的部落格映像、 使用最適合完成等<xref:System.Windows.Controls.RichTextBox>。 下表摘要說明主要的功能<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBox>。  
  
|控制項|即時拼字檢查|操作功能表|之類的格式化命令<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)|<xref:System.Windows.Documents.FlowDocument> 例如影像、 段落、 資料表等內容。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|是 (請參閱 [RichTextBox 概觀](richtextbox-overview.md))|  
  
> [!NOTE]
>  雖然<xref:System.Windows.Controls.TextBox>支援格式化相關編輯命令類似的運作<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)，例如許多基本命令支援這兩個控制項<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>。 如需詳細資訊，請參閱 <xref:System.Windows.Documents.EditingCommands>。  
  
 支援的功能<xref:System.Windows.Controls.TextBox>下列各節所述。 如需詳細資訊<xref:System.Windows.Controls.RichTextBox>，請參閱 < [RichTextBox 概觀](richtextbox-overview.md)。  
  
### <a name="real-time-spellchecking"></a>即時拼字檢查  
 您可以啟用即時拼字檢查，在<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![具有拼字檢查功能的 TextBox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### <a name="context-menu"></a>操作功能表  
 根據預設，同時<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>有使用者以滑鼠右鍵按一下控制項內部時，會出現內容功能表。 操作功能表可以讓使用者剪下、複製或貼上 (請見下圖)。  
  
 ![具有操作功能表的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 您可以建立自訂操作功能表來覆寫預設行為。 如需詳細資訊，請參閱[搭配 TextBox 使用自訂操作功能表](how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>建立 TextBox  
 A<xref:System.Windows.Controls.TextBox>可以是單行或由多行組成。 單行<xref:System.Windows.Controls.TextBox>最適合用於輸入少量的純文字 （也就表單中的「名稱」、「電話號碼」等)。 下列範例示範如何建立單行<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您也可以建立<xref:System.Windows.Controls.TextBox>，可讓使用者輸入多行文字。 例如，如果您的表單要求使用者概略的自傳，您會想要使用<xref:System.Windows.Controls.TextBox>支援多行文字。 下列範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定義<xref:System.Windows.Controls.TextBox>自動擴充以容納多行文字的控制項。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性設定為`Wrap`會導致文字自動換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，會自動展開<xref:System.Windows.Controls.TextBox>控制項以容納新的一行，如有必要。  
  
 設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性設定為`true`RETURN 鍵按下時，會自動再次展開要插入新行<xref:System.Windows.Controls.TextBox>以容納新的一行，如有必要。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至的捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>捲動如果<xref:System.Windows.Controls.TextBox>擴充框架或視窗的大小超過。  
  
 如需有關使用相關聯的不同工作<xref:System.Windows.Controls.TextBox>，請參閱 < [how to 主題](textbox-how-to-topics.md)。  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件應該用來偵測中的文字<xref:System.Windows.Controls.TextBox>或是<xref:System.Windows.Controls.RichTextBox>有所變更，而不是<xref:System.Windows.UIElement.KeyDown>跟您預期的一樣。 如需範例，請參閱[偵測 TextBox 中的文字變更](how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO 主題](textbox-how-to-topics.md)
- [RichTextBox 概觀](richtextbox-overview.md)
