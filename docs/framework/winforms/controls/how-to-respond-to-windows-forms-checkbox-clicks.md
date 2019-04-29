---
title: HOW TO：回應 Windows Forms 核取方塊的按一下動作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: ce616f45ceaa3db117c6981d2987ac09bba7b3fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912934"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>HOW TO：回應 Windows Forms 核取方塊的按一下動作
每當使用者按一下 Windows Form<xref:System.Windows.Forms.CheckBox>控制項，<xref:System.Windows.Forms.Control.Click>就會發生事件。 您可以編寫您的應用程式，以執行某些動作的核取方塊狀態而定。  
  
### <a name="to-respond-to-checkbox-clicks"></a>若要回應 CheckBox 按一下動作  
  
1. 在 <xref:System.Windows.Forms.Control.Click>事件處理常式，使用<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性來判斷控制項的狀態，並執行任何必要的動作。  
  
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
    >  如果使用者試著按兩下<xref:System.Windows.Forms.CheckBox>控制項，將會個別處理每按一下，也就是說，<xref:System.Windows.Forms.CheckBox>控制項不支援按兩下事件。  
  
    > [!NOTE]
    >  當<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>屬性是`true`（預設值），<xref:System.Windows.Forms.CheckBox>自動選取或清除時按一下它。 否則，您必須手動設定<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性時<xref:System.Windows.Forms.Control.Click>就會發生事件。  
  
     您也可以使用<xref:System.Windows.Forms.CheckBox>控制項來決定採取的動作。  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>按一下來決定所要採取的動作時核取方塊  
  
1. 若要查詢的值中使用 case 陳述式<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性來決定所要採取的動作。 當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`，則<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性可能會傳回三個可能的值，代表要核取方塊，方塊未選取，或是第三個不定狀態顯示此方塊以呈現暗灰色無法使用，表示選項的外觀。  
  
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
    >  當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`，則<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性會傳回`true`同時<xref:System.Windows.Forms.CheckState.Checked>和<xref:System.Windows.Forms.CheckState.Indeterminate>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox 控制項概觀](checkbox-control-overview-windows-forms.md)
- [如何：設定使用 Windows Form 核取方塊控制項的選項](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox 控制項](checkbox-control-windows-forms.md)
