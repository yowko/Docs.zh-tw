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
ms.openlocfilehash: 02638ab59c0ba1c0eb0f8090be118b3d5a9111f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="09673-102">如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="09673-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="09673-103">您可以使用 Windows Form<xref:System.Windows.Forms.ErrorProvider>元件，以顯示錯誤圖示，當使用者輸入無效的資料。</span><span class="sxs-lookup"><span data-stu-id="09673-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="09673-104">您必須擁有至少兩個索引標籤它們之間，並藉此叫用的驗證程式碼以表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="09673-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="09673-105">控制項的值就是不正確時顯示錯誤圖示</span><span class="sxs-lookup"><span data-stu-id="09673-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="09673-106">加入兩個控制項 — 例如，文字方塊中，加入 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="09673-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="09673-107">新增<xref:System.Windows.Forms.ErrorProvider>元件至表單。</span><span class="sxs-lookup"><span data-stu-id="09673-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="09673-108">選取第一個控制項，並將程式碼加入其<xref:System.Windows.Forms.Control.Validating>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="09673-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="09673-109">為了讓此程式碼正確執行，此程序必須連接到事件。</span><span class="sxs-lookup"><span data-stu-id="09673-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="09673-110">如需詳細資訊，請參閱[How to： 建立事件處理常式在執行時間適用於 Windows Form](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="09673-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="09673-111">下列程式碼測試使用者輸入; 資料的有效性如果資料無效，<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="09673-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="09673-112">第一個引數<xref:System.Windows.Forms.ErrorProvider.SetError%2A>方法會指定哪一個控制項旁顯示圖示。</span><span class="sxs-lookup"><span data-stu-id="09673-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="09673-113">第二個引數是要顯示的錯誤文字。</span><span class="sxs-lookup"><span data-stu-id="09673-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="09673-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="09673-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="09673-115">執行專案。</span><span class="sxs-lookup"><span data-stu-id="09673-115">Run the project.</span></span> <span data-ttu-id="09673-116">在第一個控制項，然後第二個索引標籤中輸入無效 （在此範例中，非數字） 的資料。</span><span class="sxs-lookup"><span data-stu-id="09673-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="09673-117">當出現錯誤圖示時，指向它以查看錯誤文字的滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="09673-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09673-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09673-118">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [<span data-ttu-id="09673-119">ErrorProvider 元件概觀</span><span class="sxs-lookup"><span data-stu-id="09673-119">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="09673-120">操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤</span><span class="sxs-lookup"><span data-stu-id="09673-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
