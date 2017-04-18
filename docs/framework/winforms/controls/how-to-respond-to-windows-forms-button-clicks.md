---
title: "如何：回應 Windows Form Button 按一下動作 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], Click 回應"
  - "按鈕, 回應 Click 事件"
  - "Click 事件, Button 控制項"
  - "Click 事件, 回應"
  - "按兩下"
  - "事件 [Windows Form], Click 事件"
  - "範例 [Windows Form], 控制項"
  - "MouseDown 事件"
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：回應 Windows Form Button 按一下動作
Windows Form <xref:System.Windows.Forms.Button> 控制項的最基本用途是在按一下按鈕後，執行某些程式碼。  
  
 按一下 <xref:System.Windows.Forms.Button> 控制項也會產生許多其他的事件，例如 <xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件。  如果您想要附加這些相關事件的事件處理常式，請確定它們的動作不會彼此衝突。  例如，如果按一下按鈕會清除使用者在文字方塊輸入的資訊，則將滑鼠游標移到按鈕上時，應該不會用這些目前已不存在的資訊來顯示工具提示。  
  
 如果使用者嘗試按兩下 <xref:System.Windows.Forms.Button> 控制項，則每個按一下滑鼠的動作將被分別處理；換言之，此控制項不支援按兩下事件。  
  
### 若要回應按一下按鈕的動作  
  
-   在按鈕的`Click` <xref:System.EventHandler> 中撰寫要執行的程式碼。  `Button1_Click` 必須繫結至控制項。  如需詳細資訊，請參閱[如何：建立 Windows Form 的執行階段事件處理常式](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp#  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## 請參閱  
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [選取 Windows Form Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)