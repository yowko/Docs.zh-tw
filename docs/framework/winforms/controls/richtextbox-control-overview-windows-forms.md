---
title: "RichTextBox 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RichTextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "RichTextBox 控制項 [Windows Form], 關於 RichTextBox 控制項"
  - "文字方塊, 關於文字方塊"
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# RichTextBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項是用來顯示、輸入及管理具有格式的文字。  <xref:System.Windows.Forms.RichTextBox> 控制項的功能與 <xref:System.Windows.Forms.TextBox> 控制項相同，但它還能夠顯示字型、色彩及連結，也能從檔案載入文字和內嵌影像以及尋找指定的字元。  <xref:System.Windows.Forms.RichTextBox> 控制項通常是用來提供類似文書處理應用程式 \(例如 Microsoft Word\) 的文字管理和顯示功能。  就像 <xref:System.Windows.Forms.TextBox> 控制項一樣，<xref:System.Windows.Forms.RichTextBox> 控制項也可以顯示捲軸，但與 <xref:System.Windows.Forms.TextBox> 控制項不同的是，它的預設設定是視需要顯示水平和垂直捲軸，且具有其他的捲軸設定。  
  
## 使用 RichTextBox 控制項  
 如同 <xref:System.Windows.Forms.TextBox> 控制項，所顯示的文字是由 <xref:System.Windows.Forms.RichTextBox.Text%2A> 屬性來設定。  <xref:System.Windows.Forms.RichTextBox> 控制項具有好幾個格式化文字的屬性。  如需詳細資訊，請參閱 [如何：為 Windows Form RichTextBox 控制項設定字型屬性](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) 和 [如何：使用 Windows Form RichTextBox 控制項設定縮排、首行縮排和分項段落](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)。  若要管理檔案，<xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 和 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> 方法能夠顯示和寫入多種檔案格式，包括純文字、Unicode 純文字及 Rich Text 格式 \(RTF\)。  可能的檔案格式都列在 [RichTextBoxStreamType 列舉型別](frlrfSystemWindowsFormsRichTextBoxStreamTypeClassTopic) \(Enumeration\) 中。  您可以使用 <xref:System.Windows.Forms.RichTextBox.Find%2A> 方法來尋找文字或特定字元的字串。  
  
 您也可以使用 <xref:System.Windows.Forms.RichTextBox> 控制項來建立 Web 樣式的連結，方式是將 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> 屬性設定為 `true`，並撰寫處理 <xref:System.Windows.Forms.RichTextBox.LinkClicked> 事件的程式碼。  如需詳細資訊，請參閱 [如何：使用 Windows Form RichTextBox 控制項顯示 Web 樣式連結](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)。  您可以將 <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> 屬性設定為 `true`，藉此防止使用者管理控制項當中部分或全部的文字。  
  
 藉由呼叫 <xref:System.Windows.Forms.TextBoxBase.Undo%2A> 和 <xref:System.Windows.Forms.RichTextBox.Redo%2A> 方法，您可以復原和取消復原 <xref:System.Windows.Forms.RichTextBox> 控制項中大部分的編輯作業。  <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> 方法讓您可判斷是否可將使用者已復原的上一個作業重新套用至控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)