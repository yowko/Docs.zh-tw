---
title: 使用 ErrorProvider 元件顯示表單驗證的錯誤圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745905"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示
當使用者輸入不正確資料時，您可以使用 Windows Forms <xref:System.Windows.Forms.ErrorProvider> 元件來顯示錯誤圖示。 您在表單上必須至少有兩個控制項，才能在兩者之間定位，並藉此叫用驗證程式代碼。  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>當控制項的值無效時顯示錯誤圖示  
  
1. 將兩個控制項（例如文字方塊）新增至 Windows Form。  
  
2. 將 <xref:System.Windows.Forms.ErrorProvider> 元件新增至表單。  
  
3. 選取第一個控制項，並將程式碼加入其 <xref:System.Windows.Forms.Control.Validating> 事件處理常式。 為了讓此程式碼能夠正常執行，必須連接到事件。 如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     下列程式碼會測試使用者所輸入資料的有效性;如果資料無效，則會呼叫 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法。 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法的第一個引數會指定要在其旁邊顯示圖示的控制項。 第二個引數是要顯示的錯誤文字。  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     （視覺C#效果， C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. 執行專案。 將不正確（在此範例中為非數值）資料輸入到第一個控制項，然後按 tab 鍵前往第二個控制項。 當錯誤圖示顯示時，請使用滑鼠指標指向它，以查看錯誤文字。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider 元件概觀](errorprovider-component-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
