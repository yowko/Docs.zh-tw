---
title: 在 TextBox 控制項中選取文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745311"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="282a6-102">如何：在 Windows Form TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="282a6-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="282a6-103">您可以在 [Windows Forms <xref:System.Windows.Forms.TextBox>] 控制項中以程式設計方式選取文字。</span><span class="sxs-lookup"><span data-stu-id="282a6-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="282a6-104">例如，如果您建立的函式會搜尋特定字串的文字，您可以選取文字，以視覺方式警示找到之字串位置的讀取器。</span><span class="sxs-lookup"><span data-stu-id="282a6-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="282a6-105">以程式設計方式選取文字</span><span class="sxs-lookup"><span data-stu-id="282a6-105">To select text programmatically</span></span>  
  
1. <span data-ttu-id="282a6-106">將 [<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>] 屬性設為您要選取之文字的開頭。</span><span class="sxs-lookup"><span data-stu-id="282a6-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="282a6-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性是一個數位，表示文字字串內的插入點，其中0是最左邊的位置。</span><span class="sxs-lookup"><span data-stu-id="282a6-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="282a6-108">如果 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為等於或大於文字方塊中字元數的值，則插入點會放在最後一個字元之後。</span><span class="sxs-lookup"><span data-stu-id="282a6-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="282a6-109">將 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性設為您想要選取之文字的長度。</span><span class="sxs-lookup"><span data-stu-id="282a6-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="282a6-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 屬性是設定插入點寬度的數值。</span><span class="sxs-lookup"><span data-stu-id="282a6-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="282a6-111">將 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 設定為大於0的數位，會使選取的字元數從目前的插入點開始。</span><span class="sxs-lookup"><span data-stu-id="282a6-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="282a6-112">選擇性透過 <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> 屬性存取選取的文字。</span><span class="sxs-lookup"><span data-stu-id="282a6-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="282a6-113">當控制項的 <xref:System.Windows.Forms.Control.Enter> 事件發生時，下列程式碼會選取文字方塊的內容。</span><span class="sxs-lookup"><span data-stu-id="282a6-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="282a6-114">這個範例會檢查文字方塊是否有不 `null` 的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性或空字串的值。</span><span class="sxs-lookup"><span data-stu-id="282a6-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="282a6-115">當文字方塊收到焦點時，就會選取文字方塊中目前的文字。</span><span class="sxs-lookup"><span data-stu-id="282a6-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="282a6-116">`TextBox1_Enter` 事件處理常式必須系結至控制項。如需詳細資訊，請參閱[如何：在執行時間建立事件處理常式以進行 Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="282a6-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="282a6-117">若要測試此範例，請按下 Tab 鍵，直到文字方塊具有焦點為止。</span><span class="sxs-lookup"><span data-stu-id="282a6-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="282a6-118">如果您在文字方塊中按一下，文字就會取消選取。</span><span class="sxs-lookup"><span data-stu-id="282a6-118">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="282a6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="282a6-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="282a6-120">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="282a6-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="282a6-121">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="282a6-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="282a6-122">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="282a6-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="282a6-123">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="282a6-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="282a6-124">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="282a6-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="282a6-125">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="282a6-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="282a6-126">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="282a6-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
