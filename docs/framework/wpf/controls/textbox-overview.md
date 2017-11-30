---
title: "TextBox 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], TextBox
- TextBox control [WPF], about TextBox control
ms.assetid: 1ba6dc5b-11a7-4247-9213-36c6729ee35f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1116093ddcd95c99deac8a1e1b14fef3b0a458f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-overview"></a>TextBox 概觀
<xref:System.Windows.Controls.TextBox>類別可讓您顯示或編輯未格式化的文字。 常見用法<xref:System.Windows.Controls.TextBox>正在編輯未格式化的文字，在表單中。 例如，要求使用者的名稱、 電話號碼，表單等會使用<xref:System.Windows.Controls.TextBox>文字輸入控制項。 本主題將介紹<xref:System.Windows.Controls.TextBox>類別，並提供有關如何使用中的範例[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和[!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)]。  
  
 
  
<a name="textbox_or_richtextbox"></a>   
## <a name="textbox-or-richtextbox"></a>TextBox 或 RichTextBox？  
 同時<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>允許使用者輸入文字，但兩個控制項使用不同的情況。 A<xref:System.Windows.Controls.TextBox>需要較少的系統資源則<xref:System.Windows.Controls.RichTextBox>因此理想當時才需要編輯只能使用純文字 （亦即，在表單中的使用）。 A<xref:System.Windows.Controls.RichTextBox>是較佳選擇時所需的使用者編輯格式化的文字、 影像、 資料表或其他支援內容。 例如，編輯文件、 文件或需要格式化的部落格映像，等最佳方式是使用<xref:System.Windows.Controls.RichTextBox>。 下表摘要說明主要功能<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.TextBox>。  
  
|控制項|即時拼字檢查|操作功能表|格式等命令<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)|<xref:System.Windows.Documents.FlowDocument>類似影像、 段落、 資料表等內容。|  
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.TextBox>|是|是|否|否。|  
|<xref:System.Windows.Controls.RichTextBox>|是|是|是 (請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|是 (請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md))|  
  
> [!NOTE]
>  雖然<xref:System.Windows.Controls.TextBox>並支援格式相關編輯命令類似<xref:System.Windows.Documents.EditingCommands.ToggleBold%2A>(Ctr + B)，例如許多基本命令支援這兩個控制項<xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>。 如需詳細資訊，請參閱 <xref:System.Windows.Documents.EditingCommands>。  
  
 支援的功能<xref:System.Windows.Controls.TextBox>以下各節涵蓋了。 如需有關<xref:System.Windows.Controls.RichTextBox>，請參閱[RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)。  
  
### <a name="real-time-spellchecking"></a>即時拼字檢查  
 您可以啟用中的即時拼字檢查<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>。 啟用拼字檢查時，拼錯的文字下方會出現紅色線條 (請見下圖)。  
  
 ![具有拼字檢查功能的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")  
  
 若要了解如何啟用拼字檢查，請參閱[在文字編輯控制項中啟用拼字檢查](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)。  
  
### <a name="context-menu"></a>操作功能表  
 根據預設，同時<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.RichTextBox>有使用者以滑鼠右鍵按一下控制項內部時，會出現內容功能表。 操作功能表可以讓使用者剪下、複製或貼上 (請見下圖)。  
  
 ![具有操作功能表的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")  
  
 您可以建立自訂操作功能表來覆寫預設行為。 如需詳細資訊，請參閱[搭配 TextBox 使用自訂操作功能表](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)。  
  
<a name="creating_textboxes"></a>   
## <a name="creating-textboxes"></a>建立 TextBox  
 A<xref:System.Windows.Controls.TextBox>可以是單一線條的高度，或構成多行。 單行<xref:System.Windows.Controls.TextBox>最適合 （也就輸入純文字的資訊量很少表單中的「名稱」、「電話號碼」等)。 下列範例示範如何建立單一行<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[TextBoxMiscSnippets_snip#BasicTextBoxExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/basictextboxexample.xaml#basictextboxexamplewholepage)]  
  
 您也可以建立<xref:System.Windows.Controls.TextBox>，可讓使用者輸入多行文字。 例如，如果使用者的背景草圖要求您的表單，您會想要使用<xref:System.Windows.Controls.TextBox>支援多行文字。 下列範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義<xref:System.Windows.Controls.TextBox>會自動擴展以容納多行文字的控制項。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
 設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性`Wrap`文字的換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，自動展開<xref:System.Windows.Controls.TextBox>出空間給新的一行，視需要加入的控制項。  
  
 設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性`true`導致 RETURN 鍵按下時，再次自動展開要插入新行<xref:System.Windows.Controls.TextBox>來視需要加入新行的空間。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>可以捲動，即透過如果<xref:System.Windows.Controls.TextBox>展開超過框架或將它關閉的視窗。  
  
 如需有關使用相關聯的不同工作<xref:System.Windows.Controls.TextBox>，請參閱[的使用說明主題](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)。  
  
<a name="editing_commands"></a>   
## <a name="detect-when-content-changes"></a>偵測內容變更  
 通常<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>事件應該用來偵測每次中的文字<xref:System.Windows.Controls.TextBox>或<xref:System.Windows.Controls.RichTextBox>變更，而不是<xref:System.Windows.UIElement.KeyDown>如您所預期。 如需範例，請參閱[偵測 TextBox 中的文字變更](../../../../docs/framework/wpf/controls/how-to-detect-when-text-in-a-textbox-has-changed.md)。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明主題](../../../../docs/framework/wpf/controls/textbox-how-to-topics.md)  
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
