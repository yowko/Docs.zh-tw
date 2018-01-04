---
title: "如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 738ca9670635f78e8cb04318b192127184766c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示
您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件，以顯示錯誤圖示，當使用者輸入無效的資料。 您必須擁有至少兩個索引標籤它們之間，並藉此叫用的驗證程式碼以表單上的控制項。  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>控制項的值就是不正確時顯示錯誤圖示  
  
1.  加入兩個控制項 — 例如，文字方塊中，加入 Windows Form。  
  
2.  新增<xref:System.Windows.Forms.ErrorProvider>元件至表單。  
  
3.  選取第一個控制項，並將程式碼加入其<xref:System.Windows.Forms.Control.Validating>事件處理常式。 為了讓此程式碼正確執行，此程序必須連接到事件。 如需詳細資訊，請參閱[How to： 建立事件處理常式在執行時間適用於 Windows Form](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     下列程式碼測試使用者輸入; 資料的有效性如果資料無效，<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法呼叫。 第一個引數<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法會指定哪一個控制項旁顯示圖示。 第二個引數是要顯示的錯誤文字。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  執行專案。 在第一個控制項，然後第二個索引標籤中輸入無效 （在此範例中，非數字） 的資料。 當出現錯誤圖示時，指向它以查看錯誤文字的滑鼠指標。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [ErrorProvider 元件概觀](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
