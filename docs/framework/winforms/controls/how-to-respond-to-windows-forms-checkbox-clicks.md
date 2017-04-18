---
title: "如何：回應 Windows Form CheckBox 按一下動作 | Microsoft Docs"
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
  - "核取方塊, 回應事件"
  - "CheckBox 控制項 [Windows Form], Click 事件"
  - "Click 事件, CheckBox 控制項"
  - "按兩下"
  - "事件 [Windows Form], Click 事件"
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：回應 Windows Form CheckBox 按一下動作
每當使用者按一下 Windows Form <xref:System.Windows.Forms.CheckBox> 控制項時，便會發生 <xref:System.Windows.Forms.Control.Click> 事件。  您可以將應用程式設計成根據核取方塊的狀態執行一些動作。  
  
### 若要回應 CheckBox 按一下動作  
  
1.  在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，使用 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性來決定控制項的狀態，並執行任何必要的動作。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  如果使用者嘗試按兩下 <xref:System.Windows.Forms.CheckBox> 控制項，則每個按一下滑鼠的動作將會被分別處理，也就是說 <xref:System.Windows.Forms.CheckBox> 控制項不支援按兩下事件。  
  
    > [!NOTE]
    >  當 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 屬性為 `true` \(預設值\) 時，按一下該屬性便會自動選取或清除 <xref:System.Windows.Forms.CheckBox>。  否則，您必須在發生 <xref:System.Windows.Forms.Control.Click> 事件時，以手動方式設定 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性。  
  
     您也可以使用 <xref:System.Windows.Forms.CheckBox> 控制項以決定動作的過程。  
  
### 若要在按一下核取方塊時決定動作的過程  
  
1.  使用 Case 陳述式來查詢 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性值，以決定動作的過程。  當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設為 `true` 時，<xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性可能會傳回三個可能的值，分別代表核取的方塊、未核取的方塊或不定狀態；在不定狀態時，方塊會顯示為暗灰色的 \(Dimmed\) 外觀，表示無法使用該選項。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為 `true` 時，<xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性會為 <xref:System.Windows.Forms.CheckState> 和 <xref:System.Windows.Forms.CheckState> 傳回 `true`。  
  
## 請參閱  
 <xref:System.Windows.Forms.CheckBox>   
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [如何：使用 Windows Form CheckBox 控制項設定選項](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [CheckBox 控制項](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)