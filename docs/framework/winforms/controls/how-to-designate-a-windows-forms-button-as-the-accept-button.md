---
title: "如何：將 Windows Form 中的 Button 指定為接受按鈕 | Microsoft Docs"
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
  - "Windows Form 上的接受按鈕"
  - "Button 控制項 [Windows Form], 指定為預設值"
  - "按鈕, Windows Form 上的預設值"
  - "Windows Form 控制項, 表單上的預設按鈕"
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將 Windows Form 中的 Button 指定為接受按鈕
在任何 Windows Form 中，您可以將 <xref:System.Windows.Forms.Button> 控制項指定為接受按鈕，也稱為預設按鈕。  每當使用者按下 ENTER 鍵，則無論表單上的哪個控制項擁有焦點 \(Focus\)，都會按一下預設按鈕  
  
> [!NOTE]
>  這種情況的例外狀況是當具有焦點的控制項是另一個按鈕時 \(在該種情況下，具有焦點的按鈕會被按一下\)，或者是當該具有焦點的控制項是多行的文字方塊或是會截獲 ENTER 鍵的自訂控制項時。  
  
### 若要指定接受按鈕  
  
1.  將表單的 <xref:System.Windows.Forms.Form.AcceptButton%2A> 屬性設為適當的 <xref:System.Windows.Forms.Button> 控制項。  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>   
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [選取 Windows Form Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [如何：將 Windows Form 中的 Button 指定為取消按鈕](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)