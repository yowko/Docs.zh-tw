---
title: "如何：建立唯讀文字方塊 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "唯讀文字方塊"
  - "文字方塊, 唯讀"
  - "TextBox 控制項 [Windows Form], 唯讀"
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立唯讀文字方塊 (Windows Form)
你可以將可編輯的 Windows Form 文字方塊轉換為唯讀控制項。  例如，文字方塊可以顯示一個通常會被編輯、但目前由於應用程式的狀態而不會被編輯的值。  
  
### 若要建立唯讀文字方塊  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 屬性設定為 `true`。  即使將屬性設為 `true`，使用者依然可以捲動和將文字方塊中的文字反白，而不會變更文字。  在文字方塊中你可以使用 \[**複製**\] 命令，但不能使用 \[**剪下**\] 和 \[**貼上**\] 命令。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 屬性只會影響執行階段時的使用者互動。  在執行階段期間，你仍然可以藉著變更文字方塊的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性，以程式設計的方式來改變文字方塊的內容。  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [如何：檢視 Windows Form TextBox 控制項中的多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)