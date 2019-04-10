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
ms.openlocfilehash: 9487d4f82878ffefe17c576b16f654293ef01106
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316501"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="1be0f-102">HOW TO：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="1be0f-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="1be0f-103">您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件，以在使用者輸入無效的資料時顯示錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="1be0f-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="1be0f-104">您必須擁有至少兩個控制項其間索引標籤，並藉此叫用的驗證程式碼以在表單上。</span><span class="sxs-lookup"><span data-stu-id="1be0f-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="1be0f-105">控制項的值無效時顯示錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="1be0f-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="1be0f-106">新增兩個控制項 — 例如，文字方塊中，Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="1be0f-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="1be0f-107">新增<xref:System.Windows.Forms.ErrorProvider>元件至表單。</span><span class="sxs-lookup"><span data-stu-id="1be0f-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="1be0f-108">選取第一個控制項，然後將程式碼加入其<xref:System.Windows.Forms.Control.Validating>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1be0f-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="1be0f-109">為了讓此程式碼才能正常執行，程序必須連接到事件。</span><span class="sxs-lookup"><span data-stu-id="1be0f-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="1be0f-110">如需詳細資訊，請參閱[如何：在執行階段建立 Windows Forms 事件處理常式](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="1be0f-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="1be0f-111">下列程式碼測試使用者輸入; 的資料的有效性如果資料無效，<xref:System.Windows.Forms.ErrorProvider.SetError%2A>呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1be0f-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="1be0f-112">第一個引數<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法會指定哪一個控制項旁邊顯示圖示。</span><span class="sxs-lookup"><span data-stu-id="1be0f-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="1be0f-113">第二個引數是要顯示的錯誤文字。</span><span class="sxs-lookup"><span data-stu-id="1be0f-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="1be0f-114">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1be0f-114">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="1be0f-115">執行專案。</span><span class="sxs-lookup"><span data-stu-id="1be0f-115">Run the project.</span></span> <span data-ttu-id="1be0f-116">在第一個控制項，然後第二個索引標籤中輸入無效 （在此範例中，非數字） 的資料。</span><span class="sxs-lookup"><span data-stu-id="1be0f-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="1be0f-117">顯示錯誤圖示時，請指向它以查看錯誤文字的滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="1be0f-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be0f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1be0f-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="1be0f-119">ErrorProvider 元件概觀</span><span class="sxs-lookup"><span data-stu-id="1be0f-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="1be0f-120">HOW TO：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤</span><span class="sxs-lookup"><span data-stu-id="1be0f-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
