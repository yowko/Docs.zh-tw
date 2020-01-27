---
title: 在 TextBox 控制項中選取文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745311"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>如何：在 Windows Form TextBox 控制項中選取文字
您可以在 [Windows Forms <xref:System.Windows.Forms.TextBox>] 控制項中以程式設計方式選取文字。 例如，如果您建立的函式會搜尋特定字串的文字，您可以選取文字，以視覺方式警示找到之字串位置的讀取器。  
  
### <a name="to-select-text-programmatically"></a>以程式設計方式選取文字  
  
1. 將 [<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>] 屬性設為您要選取之文字的開頭。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性是一個數位，表示文字字串內的插入點，其中0是最左邊的位置。 如果 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為等於或大於文字方塊中字元數的值，則插入點會放在最後一個字元之後。  
  
2. 將 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性設為您想要選取之文字的長度。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性是設定插入點寬度的數值。 將 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 設定為大於0的數位，會使選取的字元數從目前的插入點開始。  
  
3. 選擇性透過 <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> 屬性存取選取的文字。  
  
     當控制項的 <xref:System.Windows.Forms.Control.Enter> 事件發生時，下列程式碼會選取文字方塊的內容。 這個範例會檢查文字方塊是否有不 `null` 的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性或空字串的值。 當文字方塊收到焦點時，就會選取文字方塊中目前的文字。 `TextBox1_Enter` 事件處理常式必須系結至控制項。如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     若要測試此範例，請按下 Tab 鍵，直到文字方塊具有焦點為止。 如果您在文字方塊中按一下，文字就會取消選取。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [操作說明：控制 Windows Forms TextBox 控制項中的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [操作說明：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [操作說明：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [操作說明：在 Windows Forms TextBox 控制項中檢視多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
