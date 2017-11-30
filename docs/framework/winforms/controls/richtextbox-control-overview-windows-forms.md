---
title: "RichTextBox 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4278f569a789ca6e8466e0b8e71557446b63955e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.RichTextBox>控制項用來顯示、 輸入及管理具有格式的文字。 <xref:System.Windows.Forms.RichTextBox>控制項執行的所有項目<xref:System.Windows.Forms.TextBox>控制項，但它可以也顯示字型、 色彩和連結; 文字和內嵌的影像從載入檔案，並尋找指定的字元。 <xref:System.Windows.Forms.RichTextBox>控制項通常用來提供操作文字，並顯示類似於文書處理應用程式，例如 Microsoft Word 的功能。 像<xref:System.Windows.Forms.TextBox>控制項，<xref:System.Windows.Forms.RichTextBox>控制項可以顯示捲軸，但不同的是<xref:System.Windows.Forms.TextBox>控制它的預設值是要顯示水平與垂直捲軸，如有需要以及它還有其他捲軸設定。  
  
## <a name="working-with-the-richtextbox-control"></a>使用 RichTextBox 控制項  
 如同<xref:System.Windows.Forms.TextBox>控制項，顯示的文字設定<xref:System.Windows.Forms.RichTextBox.Text%2A>屬性。 <xref:System.Windows.Forms.RichTextBox>控制項具有格式化文字的多個屬性。 如需這些屬性的詳細資訊，請參閱[如何：為 Windows Forms RichTextBox 控制項設定字型屬性](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)和[如何：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)。 若要管理檔案、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A>和<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法可以顯示並寫入多個檔案格式，包括純文字、 Unicode 純文字格式和 Rich Text Format (RTF)。 可能的檔案格式會列在<xref:System.Windows.Forms.RichTextBoxStreamType>。 您可以使用<xref:System.Windows.Forms.RichTextBox.Find%2A>方法來尋找文字或特定的字元字串。  
  
 您也可以使用<xref:System.Windows.Forms.RichTextBox>控制項，以便設定 Web 樣式連結<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>屬性`true`撰寫程式碼以處理<xref:System.Windows.Forms.RichTextBox.LinkClicked>事件。 如需詳細資訊，請參閱[如何：使用 Windows Forms RichTextBox 控制項顯示 Web 樣式連結](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)。 您可以防止使用者藉由設定操作部分或全部控制項中文字<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A>屬性`true`。  
  
 您可以復原和取消復原中大部分的編輯作業<xref:System.Windows.Forms.RichTextBox>藉由呼叫控制項<xref:System.Windows.Forms.TextBoxBase.Undo%2A>和<xref:System.Windows.Forms.RichTextBox.Redo%2A>方法。 <xref:System.Windows.Forms.RichTextBox.CanRedo%2A>方法可讓您判斷是否已在復原使用者最後一項作業可以重新套用到控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
