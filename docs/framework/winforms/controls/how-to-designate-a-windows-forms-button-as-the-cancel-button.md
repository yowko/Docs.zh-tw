---
title: "如何：將 Windows Form 中的 Button 指定為取消按鈕 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], 指定為取消按鈕"
  - "按鈕, 取消按鈕"
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將 Windows Form 中的 Button 指定為取消按鈕
在任何 Windows Form 中，您可以將 <xref:System.Windows.Forms.Button> 控制項指定為取消按鈕。  每當使用者按下 ESC 鍵，則不管表單上的哪個控制項擁有焦點，都會按一下取消按鈕。  這類按鈕通常都利用程式設計，讓使用者不需認可任何動作就能快速結束作業。  
  
### 若要指定取消按鈕  
  
1.  將表單的 <xref:System.Windows.Forms.Form.CancelButton%2A> 屬性設為適當的 <xref:System.Windows.Forms.Button> 控制項。  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Form.CancelButton%2A>   
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [選取 Windows Form Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [如何：回應 Windows Form Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [如何：將 Windows Form 中的 Button 指定為接受按鈕](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)