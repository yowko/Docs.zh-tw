---
title: RichTextBox 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742403"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項用於顯示、輸入和操作格式化的文字。 <xref:System.Windows.Forms.RichTextBox> 控制項會執行 <xref:System.Windows.Forms.TextBox> 控制項的所有工作，但也可以顯示字型、色彩和連結;從檔案載入文字和內嵌影像;並尋找指定的字元。 <xref:System.Windows.Forms.RichTextBox> 控制項通常用來提供文字操作和顯示功能，類似于 word 處理應用程式（例如 Microsoft Word）。 就像 <xref:System.Windows.Forms.TextBox> 控制項一樣，<xref:System.Windows.Forms.RichTextBox> 控制項也可以顯示捲軸;但與 <xref:System.Windows.Forms.TextBox> 控制項不同的是，它的預設設定是視需要顯示水準和垂直捲動條，而且有其他捲軸設定。  
  
## <a name="working-with-the-richtextbox-control"></a>使用 RichTextBox 控制項  
 如同 <xref:System.Windows.Forms.TextBox> 控制項，顯示的文字是由 <xref:System.Windows.Forms.RichTextBox.Text%2A> 屬性所設定。 <xref:System.Windows.Forms.RichTextBox> 控制項有許多屬性可將文字格式化。 如需這些屬性的詳細資訊，請參閱[如何：為 Windows Forms RichTextBox 控制項設定字型屬性](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)和[如何：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)。 若要操作檔案，<xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 和 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> 方法可以顯示和寫入多種檔案格式，包括純文字、Unicode 純文字和 Rtf 格式（RTF）。 可能的檔案格式會列在 <xref:System.Windows.Forms.RichTextBoxStreamType>中。 您可以使用 <xref:System.Windows.Forms.RichTextBox.Find%2A> 方法來尋找文字或特定字元的字串。  
  
 您也可以將 <xref:System.Windows.Forms.RichTextBox> 控制項用於 Web 樣式連結，方法是將 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> 屬性設定為 `true` 並撰寫程式碼來處理 <xref:System.Windows.Forms.RichTextBox.LinkClicked> 事件。 如需詳細資訊，請參閱[如何：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)。 您可以藉由將 [<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A>] 屬性設定為 [`true`]，防止使用者操作控制項中的部分或全部文字。  
  
 您可以藉由呼叫 <xref:System.Windows.Forms.TextBoxBase.Undo%2A> 和 <xref:System.Windows.Forms.RichTextBox.Redo%2A> 方法，來復原和重做 <xref:System.Windows.Forms.RichTextBox> 控制項中大部分的編輯作業。 <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> 方法可讓您判斷使用者已復原的最後一個作業是否可以重新套用至控制項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
