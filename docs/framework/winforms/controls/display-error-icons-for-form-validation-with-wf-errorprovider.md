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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="5903f-102">如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="5903f-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="5903f-103">當使用者輸入不正確資料時，您可以使用 Windows Forms <xref:System.Windows.Forms.ErrorProvider> 元件來顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="5903f-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="5903f-104">您在表單上必須至少有兩個控制項，才能在兩者之間定位，並藉此叫用驗證程式代碼。</span><span class="sxs-lookup"><span data-stu-id="5903f-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="5903f-105">當控制項的值無效時顯示錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="5903f-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="5903f-106">將兩個控制項（例如文字方塊）新增至 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="5903f-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="5903f-107">將 <xref:System.Windows.Forms.ErrorProvider> 元件新增至表單。</span><span class="sxs-lookup"><span data-stu-id="5903f-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="5903f-108">選取第一個控制項，並將程式碼加入其 <xref:System.Windows.Forms.Control.Validating> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5903f-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="5903f-109">為了讓此程式碼能夠正常執行，必須連接到事件。</span><span class="sxs-lookup"><span data-stu-id="5903f-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="5903f-110">如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="5903f-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="5903f-111">下列程式碼會測試使用者所輸入資料的有效性;如果資料無效，則會呼叫 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5903f-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="5903f-112"><xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法的第一個引數會指定要在其旁邊顯示圖示的控制項。</span><span class="sxs-lookup"><span data-stu-id="5903f-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="5903f-113">第二個引數是要顯示的錯誤文字。</span><span class="sxs-lookup"><span data-stu-id="5903f-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="5903f-114">（視覺C#效果， C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5903f-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="5903f-115">執行專案。</span><span class="sxs-lookup"><span data-stu-id="5903f-115">Run the project.</span></span> <span data-ttu-id="5903f-116">將不正確（在此範例中為非數值）資料輸入到第一個控制項，然後按 tab 鍵前往第二個控制項。</span><span class="sxs-lookup"><span data-stu-id="5903f-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="5903f-117">當錯誤圖示顯示時，請使用滑鼠指標指向它，以查看錯誤文字。</span><span class="sxs-lookup"><span data-stu-id="5903f-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5903f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5903f-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="5903f-119">ErrorProvider 元件概觀</span><span class="sxs-lookup"><span data-stu-id="5903f-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="5903f-120">操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤</span><span class="sxs-lookup"><span data-stu-id="5903f-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
