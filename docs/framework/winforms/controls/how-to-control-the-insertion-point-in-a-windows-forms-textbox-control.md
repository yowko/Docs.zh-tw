---
title: 控制 TextBox 控制項中的插入點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742199"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="72fc3-102">如何：控制 Windows Form TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="72fc3-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="72fc3-103">當 Windows Forms <xref:System.Windows.Forms.TextBox> 控制項第一次收到焦點時，文字方塊內的預設插入會在任何現有文字的左邊。</span><span class="sxs-lookup"><span data-stu-id="72fc3-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="72fc3-104">使用者可以使用鍵盤或滑鼠移動插入點。</span><span class="sxs-lookup"><span data-stu-id="72fc3-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="72fc3-105">如果文字方塊遺失，然後重新取得焦點，則插入點就會是使用者最後一次放置的位置。</span><span class="sxs-lookup"><span data-stu-id="72fc3-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="72fc3-106">在某些情況下，可以將此行為令人不安給使用者。</span><span class="sxs-lookup"><span data-stu-id="72fc3-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="72fc3-107">在文字處理應用程式中，使用者可能會預期新的字元會出現在任何現有的文字之後。</span><span class="sxs-lookup"><span data-stu-id="72fc3-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="72fc3-108">在資料輸入應用程式中，使用者可能會預期新的字元會取代任何現有的專案。</span><span class="sxs-lookup"><span data-stu-id="72fc3-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="72fc3-109">[<xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>] 和 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性可讓您修改行為，以符合您的目的。</span><span class="sxs-lookup"><span data-stu-id="72fc3-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="72fc3-110">控制 TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="72fc3-110">To control the insertion point in a TextBox control</span></span>  
  
1. <span data-ttu-id="72fc3-111">將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="72fc3-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="72fc3-112">零會將插入點立即放在第一個字元的左邊。</span><span class="sxs-lookup"><span data-stu-id="72fc3-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2. <span data-ttu-id="72fc3-113">選擇性將 [<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>] 屬性設為您想要選取之文字的長度。</span><span class="sxs-lookup"><span data-stu-id="72fc3-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="72fc3-114">下列程式碼一律會將插入點傳回0。</span><span class="sxs-lookup"><span data-stu-id="72fc3-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="72fc3-115">`TextBox1_Enter` 事件處理常式必須系結至控制項。如需詳細資訊，請參閱[在 Windows Forms 中建立事件處理常式](../creating-event-handlers-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="72fc3-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="72fc3-116">預設會顯示插入點</span><span class="sxs-lookup"><span data-stu-id="72fc3-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="72fc3-117">只有在 [<xref:System.Windows.Forms.TextBox>] 控制項是定位順序的第一個位置時，預設會在新的表單中顯示 <xref:System.Windows.Forms.TextBox> 插入點。</span><span class="sxs-lookup"><span data-stu-id="72fc3-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="72fc3-118">否則，只有當您使用鍵盤或滑鼠來提供 <xref:System.Windows.Forms.TextBox> 焦點時，才會顯示插入點。</span><span class="sxs-lookup"><span data-stu-id="72fc3-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="72fc3-119">若要讓文字方塊插入點在新表單上預設為可見</span><span class="sxs-lookup"><span data-stu-id="72fc3-119">To make the text box insertion point visible by default on a new form</span></span>  
  
- <span data-ttu-id="72fc3-120">將 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定為 [`0`]。</span><span class="sxs-lookup"><span data-stu-id="72fc3-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fc3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72fc3-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="72fc3-122">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="72fc3-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="72fc3-123">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="72fc3-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="72fc3-124">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="72fc3-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="72fc3-125">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="72fc3-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="72fc3-126">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="72fc3-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="72fc3-127">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="72fc3-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="72fc3-128">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="72fc3-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
