---
title: HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊
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
ms.openlocfilehash: ab5df1233c16a7ce076efa817fb14808b588ebcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746745"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊
密碼方塊是 Windows Form 的文字方塊中，會顯示預留位置字元，而使用者輸入字串。  
  
### <a name="to-create-a-password-text-box"></a>若要建立密碼文字方塊  
  
1. 設定<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性<xref:System.Windows.Forms.TextBox>控制項的特殊字元。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性會指定顯示在文字方塊中的字元。 例如，如果您想在 密碼 方塊中顯示的星號，請指定 * 的<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性 視窗中的屬性。 然後，不論何種使用者類型在文字方塊中的字元，會顯示一個星號。  
  
2. （選擇性）設定<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>屬性。 屬性會決定可以在文字方塊中輸入的幾個字元。 如果超過最大長度時，系統會發出嗶聲，文字方塊不接受任何更多的字元。 請注意，您可能不想要這樣做為密碼的最大長度可能是使用的駭客嘗試猜測密碼。  
  
     下列程式碼範例示範如何初始化將會接受最多 14 個字元長的字串，並顯示星號取代字串的文字方塊。 `InitializeMyControl`程序將不會自動執行; 它必須先呼叫。  
  
    > [!IMPORTANT]
    >  使用<xref:System.Windows.Forms.TextBox.PasswordChar%2A>文字方塊上的屬性可以協助確保其他人不會判斷使用者的密碼，如果他們發現到使用者輸入。 此安全性措施不包含任何類型的儲存體或傳輸的密碼，可能是因為您的應用程式邏輯。 因為輸入的文字不以任何方式加密，您應該將其視為任何其他機密資料。 即使它不會因此出現，密碼是仍被視為純文字字串 （除非您已實作某些其他安全性量值）。  
  
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
- [如何：將引號放入字串](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows Forms TextBox 控制項中選取文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows Forms TextBox 控制項中檢視多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
