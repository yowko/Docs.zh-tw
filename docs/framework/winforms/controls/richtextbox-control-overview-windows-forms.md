---
title: RichTextBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0827c1919597e9eb85bfa41721676008b76564d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201594"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項用來顯示、 輸入和操作具有格式的文字。 <xref:System.Windows.Forms.RichTextBox>控制一切<xref:System.Windows.Forms.TextBox>控制項，但它也顯示字型、 色彩和連結; 從檔案載入文字和內嵌的影像即可尋找指定的字元。 <xref:System.Windows.Forms.RichTextBox>控制項通常用來提供文字操作和顯示功能類似於文書處理應用程式，例如 Microsoft Word。 像是<xref:System.Windows.Forms.TextBox>控制項中，<xref:System.Windows.Forms.RichTextBox>控制項可以顯示捲軸，但不同於<xref:System.Windows.Forms.TextBox>視需要顯示水平與垂直捲軸的控制項，其預設值是和它具有其他捲軸設定。  
  
## <a name="working-with-the-richtextbox-control"></a>使用 RichTextBox 控制項  
 如同<xref:System.Windows.Forms.TextBox>控制項，顯示的文字設定<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性。 <xref:System.Windows.Forms.RichTextBox>控制項具有格式化文字的多個屬性。 如需有關這些屬性的詳細資訊，請參閱[How to:為 Windows Forms RichTextBox 控制項設定字型屬性](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)和[How to:設定縮排、 首行縮排和分項段落與 Windows Forms RichTextBox 控制項](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)。 若要操作的檔案，<xref:System.Windows.Forms.RichTextBox.LoadFile%2A>和<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法可以顯示並寫入包括純文字、 Unicode 純文字和 Rich Text Format (RTF) 的多種檔案格式。 可能的檔案格式會列在<xref:System.Windows.Forms.RichTextBoxStreamType>。 您可以使用<xref:System.Windows.Forms.RichTextBox.Find%2A>方法來尋找文字或特定字元字串。  
  
 您也可以使用<xref:System.Windows.Forms.RichTextBox>藉由設定的 Web 樣式連結的控制<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性設`true`撰寫程式碼來處理和<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件。 如需詳細資訊，請參閱[如何：顯示 Web 樣式連結與 Windows Forms RichTextBox 控制項](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)。 您可以防止使用者藉由設定操作部分或全部控制項中的文字<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A>屬性設`true`。  
  
 您可以復原和取消復原中的大部分編輯作業<xref:System.Windows.Forms.RichTextBox>控制項，藉由呼叫<xref:System.Windows.Forms.TextBoxBase.Undo%2A>和<xref:System.Windows.Forms.RichTextBox.Redo%2A>方法。 <xref:System.Windows.Forms.RichTextBox.CanRedo%2A>方法可讓您判斷是否將使用者已復原的最後一個作業可以套用到控制項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
