---
title: 如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: 789a0a25c65185b101ef427ff62871fa490c7f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
Windows Form 的常見用法<xref:System.Windows.Forms.RichTextBox>控制項已格式化文字的字型選項或段落樣式等屬性。 您的應用程式可能需要追蹤的文字格式設定用來顯示工具列，就像許多文書處理應用程式中的任何變更。  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>若要回應的格式屬性變更  
  
1.  在撰寫程式碼<xref:System.Windows.Forms.RichTextBox.SelectionChanged>事件處理常式執行適當動作的屬性值而定。 下列範例會變更工具列按鈕的值而定的外觀<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。 當插入點移動控制項中，將只會更新工具列按鈕。  
  
     以下範例假設的表單具有<xref:System.Windows.Forms.RichTextBox>控制項和<xref:System.Windows.Forms.ToolBar>包含的工具列按鈕控制項。 如需工具列和工具列按鈕的詳細資訊，請參閱[How to： 將按鈕加入 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)。  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
