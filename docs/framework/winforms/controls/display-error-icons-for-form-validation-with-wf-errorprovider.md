---
title: HOW TO：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示
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
ms.openlocfilehash: 39dd77fee36b172f6c38746bfe970094ec9edb4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223546"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>HOW TO：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示
您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件，以在使用者輸入無效的資料時顯示錯誤圖示。 您必須擁有至少兩個控制項其間索引標籤，並藉此叫用的驗證程式碼以在表單上。  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>控制項的值無效時顯示錯誤圖示  
  
1.  新增兩個控制項 — 例如，文字方塊中，Windows 表單。  
  
2.  新增<xref:System.Windows.Forms.ErrorProvider>元件至表單。  
  
3.  選取第一個控制項，然後將程式碼加入其<xref:System.Windows.Forms.Control.Validating>事件處理常式。 為了讓此程式碼才能正常執行，程序必須連接到事件。 如需詳細資訊，請參閱[如何：在執行階段建立 Windows Forms 事件處理常式](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     下列程式碼測試使用者輸入; 的資料的有效性如果資料無效，<xref:System.Windows.Forms.ErrorProvider.SetError%2A>呼叫方法。 第一個引數<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法會指定哪一個控制項旁邊顯示圖示。 第二個引數是要顯示的錯誤文字。  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  執行專案。 在第一個控制項，然後第二個索引標籤中輸入無效 （在此範例中，非數字） 的資料。 顯示錯誤圖示時，請指向它以查看錯誤文字的滑鼠指標。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider 元件概觀](errorprovider-component-overview-windows-forms.md)
- [HOW TO：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
