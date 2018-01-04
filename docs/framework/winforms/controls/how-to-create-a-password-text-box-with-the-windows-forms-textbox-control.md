---
title: "如何：使用 Windows Form TextBox 控制項建立密碼文字方塊"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fe8c3c6ac3c0f47f5e78aa7ff3242a0c69c7f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="93c09-102">如何：使用 Windows Form TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="93c09-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="93c09-103">密碼方塊是 Windows 表單文字方塊顯示預留位置字元，而使用者輸入的字串。</span><span class="sxs-lookup"><span data-stu-id="93c09-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="93c09-104">若要建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="93c09-104">To create a password text box</span></span>  
  
1.  <span data-ttu-id="93c09-105">設定<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性<xref:System.Windows.Forms.TextBox>控制項的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="93c09-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="93c09-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性會指定顯示在文字方塊中的字元。</span><span class="sxs-lookup"><span data-stu-id="93c09-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="93c09-107">例如，如果您希望顯示在 密碼 方塊中，指定 * 的<xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="93c09-107">For example, if you want asterisks displayed in the password box, specify * for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="93c09-108">然後，不論何種使用者會在文字方塊中輸入的字元，會顯示一個星號。</span><span class="sxs-lookup"><span data-stu-id="93c09-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2.  <span data-ttu-id="93c09-109">（選擇性）設定<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="93c09-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="93c09-110">屬性會決定可以在文字方塊中輸入多少個字元。</span><span class="sxs-lookup"><span data-stu-id="93c09-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="93c09-111">如果超過最大長度時，系統會發出嗶聲，文字方塊不接受任何多個字元。</span><span class="sxs-lookup"><span data-stu-id="93c09-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="93c09-112">請注意，您可能不想要執行這項操作，因為密碼的最大長度可能會用來決定駭客嘗試猜測密碼。</span><span class="sxs-lookup"><span data-stu-id="93c09-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="93c09-113">下列程式碼範例示範如何初始化文字方塊中，將會接受最多 14 個字元長的字串，並且以星號取代字串。</span><span class="sxs-lookup"><span data-stu-id="93c09-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="93c09-114">`InitializeMyControl`程序將不會自動執行，它必須進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="93c09-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="93c09-115">使用<xref:System.Windows.Forms.TextBox.PasswordChar%2A>文字方塊上的屬性可以協助確保其他人將無法判斷使用者的密碼，如果它們觀察到使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="93c09-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="93c09-116">此安全性措施並不包含任何類型的儲存或傳送的密碼，可能是因為應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="93c09-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="93c09-117">因為輸入的文字不以任何方式加密，您應該將其視為機密資料。</span><span class="sxs-lookup"><span data-stu-id="93c09-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="93c09-118">即使沒有出現在這種情況，密碼已仍視為純文字字串 （除非您已實作其他安全性措施）。</span><span class="sxs-lookup"><span data-stu-id="93c09-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93c09-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="93c09-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="93c09-120">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="93c09-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="93c09-121">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="93c09-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="93c09-122">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="93c09-122">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="93c09-123">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="93c09-123">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="93c09-124">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="93c09-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="93c09-125">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="93c09-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="93c09-126">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="93c09-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
