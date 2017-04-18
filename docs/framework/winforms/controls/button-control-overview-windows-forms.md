---
title: "Button 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "Button"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Button 控制項 [Windows Form], 關於 Button 控制項"
  - "按鈕, 關於按鈕"
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Button 控制項概觀 (Windows Form)
使用者可以按一下 Windows Form <xref:System.Windows.Forms.Button> 控制項來執行動作。  當按一下按鈕時，看起來就像是按下又放開按鈕一樣。  每當使用者按一下按鈕時，就會叫用 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  您可以在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中放入程式碼，以執行任何選擇的動作。  
  
 按鈕上所顯示的文字包含在 <xref:System.Windows.Forms.Control.Text%2A> 屬性中。  如果您的文字寬度超過按鈕的寬度，則會換行到下一行；  然而，如果控制項無法容納文字的整個高度，則會予以裁剪。  如需詳細資訊，請參閱 [如何：設定由 Windows Form 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)。  <xref:System.Windows.Forms.Control.Text%2A> 屬性可包含便捷鍵 \(Access Key\)，使用者可以按下 ALT 鍵和便捷鍵來「按一下」控制項。  如需詳細資訊，請參閱 [如何：建立 Windows Form 控制項的便捷鍵](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。  文字的外觀是由 <xref:System.Windows.Forms.Control.Font%2A> 屬性和 <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> 屬性所控制。  
  
 <xref:System.Windows.Forms.Button> 控制項也可以使用 <xref:System.Windows.Forms.ButtonBase.Image%2A> 和 <xref:System.Windows.Forms.ButtonBase.ImageList%2A> 屬性來顯示影像。  如需詳細資訊，請參閱 [如何：設定由 Windows Form 控制項所顯示的影像](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.Button>   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [選取 Windows Form Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)   
 [如何：使用設計工具將 Windows Form 按鈕指定為取消按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)