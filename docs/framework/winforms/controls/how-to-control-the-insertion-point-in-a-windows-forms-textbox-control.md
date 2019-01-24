---
title: HOW TO：控制 Windows Forms TextBox 控制項中的插入點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 6ed49cac8341551dd0900a8468990e314a16e7b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660186"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>HOW TO：控制 Windows Forms TextBox 控制項中的插入點
當 Windows Forms<xref:System.Windows.Forms.TextBox>控制項第一次收到焦點時，文字方塊內的預設值插入至任何現有的文字的左邊。 使用者可以移動與鍵盤或滑鼠的插入點。 如果文字方塊將會遺失，並重新取得焦點，將會插入點，使用者最後放置的任一處它。  
  
 在某些情況下，此行為可以令人不安給使用者。 在文字處理應用程式，使用者可能預期任何現有的文字之後，會出現新的字元。 在資料進入應用程式中，使用者可能預期新的字元取代任何現有的項目。 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>和<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性可讓您修改以符合您用途的行為。  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>若要控制 TextBox 控制項中的插入點  
  
1.  將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為適當值。 零將插入點左邊的第一個字元。  
  
2.  （選擇性）設定<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性，以您想要選取的文字的長度。  
  
     下列程式碼一律會傳回為 0 的插入點。 `TextBox1_Enter`事件處理常式必須繫結至控制項; 如需詳細資訊，請參閱[建立 Windows Forms 中的事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>進行預設為可見的插入點  
 <xref:System.Windows.Forms.TextBox>插入點位於預設顯示在新的格式只有當<xref:System.Windows.Forms.TextBox>控制項是在定位順序中第一個。 只有當您提供的插入點，將會出現，否則為<xref:System.Windows.Forms.TextBox>鍵盤或滑鼠焦點。  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>若要依預設，新的表單上顯示文字 方塊中的插入點  
  
-   設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.Control.TabIndex%2A>屬性設`0`。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：將引號放入字串](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows Forms TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows Forms TextBox 控制項中檢視多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
