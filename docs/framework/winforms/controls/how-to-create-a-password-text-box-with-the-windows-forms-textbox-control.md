---
title: 作法：使用 Windows Forms TextBox 控制項建立密碼文字方塊
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
ms.openlocfilehash: 56391777c75db288c33d1b2192355be0df50f7ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046113"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="d5939-102">作法：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="d5939-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="d5939-103">[密碼] 方塊是一個 Windows Forms 文字方塊, 會在使用者輸入字串時顯示預留位置字元。</span><span class="sxs-lookup"><span data-stu-id="d5939-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="d5939-104">若要建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="d5939-104">To create a password text box</span></span>

1. <span data-ttu-id="d5939-105">將<xref:System.Windows.Forms.TextBox>控制項<xref:System.Windows.Forms.TextBox.PasswordChar%2A>的屬性設定為特定字元。</span><span class="sxs-lookup"><span data-stu-id="d5939-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="d5939-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A>屬性會指定顯示在文字方塊中的字元。</span><span class="sxs-lookup"><span data-stu-id="d5939-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="d5939-107">例如, 如果您想要在 [密碼] 方塊中顯示星號, 請指定<xref:System.Windows.Forms.TextBox.PasswordChar%2A> \* 做為屬性視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5939-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="d5939-108">然後, 不論使用者在文字方塊中輸入什麼字元, 都會顯示星號。</span><span class="sxs-lookup"><span data-stu-id="d5939-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="d5939-109">選擇性<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d5939-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="d5939-110">屬性會決定文字方塊中可輸入的字元數目。</span><span class="sxs-lookup"><span data-stu-id="d5939-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="d5939-111">如果超過最大長度, 系統就會發出嗶聲, 而且文字方塊不會接受任何其他字元。</span><span class="sxs-lookup"><span data-stu-id="d5939-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="d5939-112">請注意, 您可能不想要這麼做, 因為密碼的最大長度可能會用於嘗試猜測密碼的駭客。</span><span class="sxs-lookup"><span data-stu-id="d5939-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="d5939-113">下列程式碼範例示範如何初始化文字方塊, 以接受長度最多14個字元的字串, 並顯示星號來取代字串。</span><span class="sxs-lookup"><span data-stu-id="d5939-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="d5939-114">此`InitializeMyControl`程式不會自動執行, 必須呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d5939-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d5939-115">在文字方塊上使用屬性有助於確保其他人在觀察到使用者輸入時,無法判斷使用者的密碼。<xref:System.Windows.Forms.TextBox.PasswordChar%2A></span><span class="sxs-lookup"><span data-stu-id="d5939-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="d5939-116">此安全性措施並不涵蓋任何類型的儲存或傳輸, 因為您的應用程式邏輯而可能發生的密碼。</span><span class="sxs-lookup"><span data-stu-id="d5939-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="d5939-117">因為輸入的文字不會以任何方式加密, 所以您應該將它視為任何其他機密資料。</span><span class="sxs-lookup"><span data-stu-id="d5939-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="d5939-118">雖然它不會像這樣, 但仍會將密碼視為純文字字串 (除非您已執行一些額外的安全性措施)。</span><span class="sxs-lookup"><span data-stu-id="d5939-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d5939-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5939-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="d5939-120">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="d5939-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="d5939-121">如何：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="d5939-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="d5939-122">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="d5939-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="d5939-123">如何：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="d5939-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="d5939-124">如何：選取 Windows Forms TextBox 控制項中的文字</span><span class="sxs-lookup"><span data-stu-id="d5939-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="d5939-125">如何：在 Windows Forms TextBox 控制項中查看多行</span><span class="sxs-lookup"><span data-stu-id="d5939-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="d5939-126">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="d5939-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
