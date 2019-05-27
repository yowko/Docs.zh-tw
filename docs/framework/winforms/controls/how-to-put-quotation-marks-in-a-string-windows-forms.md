---
title: 作法：將引號放入字串中 (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 0148f9fde9d69bb1605776f1ab617079be96b59e
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053458"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>HOW TO：將引號放入字串中 (Windows Forms)
您有時可能想要將引號 (" ") 放入文字字串中。 例如:   
  
 She said, "You deserve a treat!"  
  
 或者，您也可以使用<xref:Microsoft.VisualBasic.ControlChars.Quote>欄位做為常數。  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>將引號放入您的程式碼中的字串  
  
1. 在 Visual Basic 中，插入資料列中的兩個引號當作內嵌引號。 在視覺效果C#和 Visual C++，插入逸出序列\\"當作內嵌的引號。 例如，若要建立前置字串，請使用下列程式碼。  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     -或-  
  
2. 針對引號插入 ASCII 或 Unicode 字元。 在 Visual Basic 中，使用 ASCII 字元 (34)。 在視覺效果C#，使用 Unicode 字元 (\u0022)。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  在此範例中，您無法使用 \u0022，因為不能使用表明是基本字元集中字元的通用字元名稱。 否則，您會產生 c3851。 如需詳細資訊，請參閱[編譯器錯誤 C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)。  
  
     -或-  
  
3. 您也可以定義字元的常數，並且在需要時使用它。  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows Forms TextBox 控制項中的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在 Windows Forms TextBox 控制項中選取文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows Forms TextBox 控制項中檢視多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
