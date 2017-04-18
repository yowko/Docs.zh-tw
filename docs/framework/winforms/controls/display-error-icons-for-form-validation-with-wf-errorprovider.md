---
title: "如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "錯誤圖示"
  - "錯誤訊息, 顯示圖示"
  - "ErrorProvider 元件 [Windows Form], 顯示錯誤圖示"
  - "錯誤 [Windows Form], 顯示給使用者"
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示
您可以使用 Windows Form <xref:System.Windows.Forms.ErrorProvider> 元件，在使用者輸入無效資料時顯示錯誤圖示。  表單中至少需要有兩個控制項，才能在它們之間按 TAB 鍵切換，以及叫用 \(Invoke\) 驗證程式碼。  
  
### 若要在控制項值無效時顯示錯誤圖示  
  
1.  在 Windows Form 中加入兩個控制項，例如，文字方塊。  
  
2.  將 <xref:System.Windows.Forms.ErrorProvider> 元件加入至表單中。  
  
3.  選取第一個控制項，並將程式碼加入它的 <xref:System.Windows.Forms.Control.Validating> 事件處理常式。  為了讓這段程式碼正確地執行，必須將此程序連接至事件。  如需詳細資訊，請參閱 [如何：建立 Windows Form 的執行階段事件處理常式](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     下列程式碼測試使用者輸入的資料之有效性；如果資料無效，則呼叫 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法。  <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法的第一個引數指定要在旁邊顯示圖示的控制項。  第二個引數是要顯示錯誤文字。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  執行專案。  在第一個控制項中輸入無效 \(在這個例子中，輸入非數字\) 資料，接著按下 Tab 鍵切換至第二個控制項。  當錯誤圖示顯示後，將滑鼠指標指向圖示來查看錯誤文字。  
  
## 請參閱  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>   
 [ErrorProvider 元件概觀](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)