---
title: 控制 TextBox 控制項中的插入點
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
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742199"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>如何：控制 Windows Form TextBox 控制項的插入點
當 Windows Forms <xref:System.Windows.Forms.TextBox> 控制項第一次收到焦點時，文字方塊內的預設插入會在任何現有文字的左邊。 使用者可以使用鍵盤或滑鼠移動插入點。 如果文字方塊遺失，然後重新取得焦點，則插入點就會是使用者最後一次放置的位置。  
  
 在某些情況下，可以將此行為令人不安給使用者。 在文字處理應用程式中，使用者可能會預期新的字元會出現在任何現有的文字之後。 在資料輸入應用程式中，使用者可能會預期新的字元會取代任何現有的專案。 [<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>] 和 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性可讓您修改行為，以符合您的目的。  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>控制 TextBox 控制項中的插入點  
  
1. 將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為適當值。 零會將插入點立即放在第一個字元的左邊。  
  
2. 選擇性將 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性設為您想要選取之文字的長度。  
  
     下列程式碼一律會將插入點傳回0。 `TextBox1_Enter` 事件處理常式必須系結至控制項。如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](../creating-event-handlers-in-windows-forms.md)。  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>預設會顯示插入點  
 只有在 [<xref:System.Windows.Forms.TextBox>] 控制項是定位順序的第一個位置時，預設會在新的表單中顯示 <xref:System.Windows.Forms.TextBox> 插入點。 否則，只有當您使用鍵盤或滑鼠來提供 <xref:System.Windows.Forms.TextBox> 焦點時，才會顯示插入點。  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>若要讓文字方塊插入點在新表單上預設為可見  
  
- 將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定為 [`0`]。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [操作說明：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [操作說明：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [操作說明：在 Windows Forms TextBox 控制項中選取文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [操作說明：在 Windows Forms TextBox 控制項中檢視多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
