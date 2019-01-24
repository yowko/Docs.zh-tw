---
title: HOW TO：在 Windows Forms TextBox 控制項中選取文字
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
ms.openlocfilehash: df2aec3ff108c0106f29e453a93b06c60e67c6af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649410"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="51293-102">HOW TO：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="51293-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="51293-103">您可以在 Windows Forms 中，以程式設計方式選取文字<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="51293-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="51293-104">比方說，如果您建立函式，以搜尋特定字串的文字時，您可以選取要以視覺化方式警示找到的字串位置的讀取器的文字。</span><span class="sxs-lookup"><span data-stu-id="51293-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="51293-105">若要以程式設計方式選取文字</span><span class="sxs-lookup"><span data-stu-id="51293-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="51293-106">設定<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>至您想要選取的文字開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="51293-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="51293-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>屬性指出插入點的文字字串內的數字，0 是最左邊位置。</span><span class="sxs-lookup"><span data-stu-id="51293-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="51293-108">如果<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>屬性設定為值等於或大於的字元數在文字方塊中，將插入點後面的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="51293-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="51293-109">設定<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性，以您想要選取的文字的長度。</span><span class="sxs-lookup"><span data-stu-id="51293-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="51293-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性是一個數字的值，設定插入點的寬度。</span><span class="sxs-lookup"><span data-stu-id="51293-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="51293-111">設定<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>更大的數字 0 會導致該要選取的字元數，比從目前的插入點。</span><span class="sxs-lookup"><span data-stu-id="51293-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="51293-112">（選擇性）存取選取的文字，透過<xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="51293-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="51293-113">選取以下的程式碼的文字內容方塊時的控制項<xref:System.Windows.Forms.Control.Enter>就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="51293-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="51293-114">這個範例會檢查文字方塊是否為值<xref:System.Windows.Forms.TextBox.Text%2A>不是屬性`null`或空字串。</span><span class="sxs-lookup"><span data-stu-id="51293-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="51293-115">當文字方塊取得焦點時，會選取目前的文字在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="51293-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="51293-116">`TextBox1_Enter`事件處理常式必須繫結至控制項; 如需詳細資訊，請參閱[How to:在執行階段建立 Windows Forms 事件處理常式](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="51293-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="51293-117">若要測試此範例中，請按 Tab 鍵，直到文字方塊具有焦點為止。</span><span class="sxs-lookup"><span data-stu-id="51293-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="51293-118">如果您按一下文字方塊中，文字會是未選取。</span><span class="sxs-lookup"><span data-stu-id="51293-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51293-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51293-119">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="51293-120">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="51293-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="51293-121">如何：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="51293-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="51293-122">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="51293-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="51293-123">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="51293-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="51293-124">如何：將引號放入字串</span><span class="sxs-lookup"><span data-stu-id="51293-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="51293-125">如何：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="51293-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="51293-126">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="51293-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
