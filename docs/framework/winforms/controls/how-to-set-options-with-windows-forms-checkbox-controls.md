---
title: "如何：使用 Windows Form CheckBox 控制項設定選項 | Microsoft Docs"
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
  - "checked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "核取方塊, 設定選項的方法"
  - "CheckBox 控制項 [Windows Form], 核取狀態"
  - "CheckBox 控制項 [Windows Form], 設定選項的方法"
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form CheckBox 控制項設定選項
Windows Form <xref:System.Windows.Forms.CheckBox> 控制項是用來提供使用者 True\/False 或 Yes\/No 選項。  控制項被選取後會顯示核取記號。  
  
### 若要使用 CheckBox 控制項設定選項  
  
1.  檢查 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性值以決定其狀態，並使用該值來設定選項。  
  
     在下列程式碼範例中，當引發 <xref:System.Windows.Forms.CheckBox> 控制項的 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件時，若已選取該核取方塊，則表單的 <xref:System.Windows.Forms.Control.AllowDrop%2A> 屬性會設定為 `false`。  這在當您要限制使用者互動的情況下很有用。  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.CheckBox>   
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [如何：回應 Windows Form CheckBox 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox 控制項](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)