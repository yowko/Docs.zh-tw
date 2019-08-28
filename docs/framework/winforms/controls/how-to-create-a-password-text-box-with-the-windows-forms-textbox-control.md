---
title: 作法：使用 Windows Forms TextBox 控制項建立密碼文字方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 56391777c75db288c33d1b2192355be0df50f7ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046113"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>作法：使用 Windows Forms TextBox 控制項建立密碼文字方塊

[密碼] 方塊是一個 Windows Forms 文字方塊, 會在使用者輸入字串時顯示預留位置字元。

### <a name="to-create-a-password-text-box"></a>若要建立密碼文字方塊

1. 將<xref:System.Windows.Forms.TextBox>控制項<xref:System.Windows.Forms.TextBox.PasswordChar%2A>的屬性設定為特定字元。

    <xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性會指定顯示在文字方塊中的字元。 例如, 如果您想要在 [密碼] 方塊中顯示星號, 請指定<xref:System.Windows.Forms.TextBox.PasswordChar%2A> * 做為屬性視窗中的屬性。 然後, 不論使用者在文字方塊中輸入什麼字元, 都會顯示星號。

2. 選擇性<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>設定屬性。 屬性會決定文字方塊中可輸入的字元數目。 如果超過最大長度, 系統就會發出嗶聲, 而且文字方塊不會接受任何其他字元。 請注意, 您可能不想要這麼做, 因為密碼的最大長度可能會用於嘗試猜測密碼的駭客。

    下列程式碼範例示範如何初始化文字方塊, 以接受長度最多14個字元的字串, 並顯示星號來取代字串。 此`InitializeMyControl`程式不會自動執行, 必須呼叫它。

    > [!IMPORTANT]
    > 在文字方塊上使用屬性有助於確保其他人在觀察到使用者輸入時,無法判斷使用者的密碼。<xref:System.Windows.Forms.TextBox.PasswordChar%2A> 此安全性措施並不涵蓋任何類型的儲存或傳輸, 因為您的應用程式邏輯而可能發生的密碼。 因為輸入的文字不會以任何方式加密, 所以您應該將它視為任何其他機密資料。 雖然它不會像這樣, 但仍會將密碼視為純文字字串 (除非您已執行一些額外的安全性措施)。

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows Forms TextBox 控制項中的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：選取 Windows Forms TextBox 控制項中的文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows Forms TextBox 控制項中查看多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
