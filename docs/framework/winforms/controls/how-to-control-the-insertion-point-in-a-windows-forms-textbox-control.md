---
title: HOW TO：控制 Windows Forms TextBox 控制項的插入點
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
ms.openlocfilehash: 43fdb023f19aa988dfef3dcd68443d6f59808472
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341318"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="95f27-102">HOW TO：控制 Windows Forms TextBox 控制項的插入點</span><span class="sxs-lookup"><span data-stu-id="95f27-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="95f27-103">當 Windows Forms<xref:System.Windows.Forms.TextBox>控制項第一次收到焦點時，文字方塊內的預設值插入至任何現有的文字的左邊。</span><span class="sxs-lookup"><span data-stu-id="95f27-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="95f27-104">使用者可以移動與鍵盤或滑鼠的插入點。</span><span class="sxs-lookup"><span data-stu-id="95f27-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="95f27-105">如果文字方塊將會遺失，並重新取得焦點，將會插入點，使用者最後放置的任一處它。</span><span class="sxs-lookup"><span data-stu-id="95f27-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="95f27-106">在某些情況下，此行為可以令人不安給使用者。</span><span class="sxs-lookup"><span data-stu-id="95f27-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="95f27-107">在文字處理應用程式，使用者可能預期任何現有的文字之後，會出現新的字元。</span><span class="sxs-lookup"><span data-stu-id="95f27-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="95f27-108">在資料進入應用程式中，使用者可能預期新的字元取代任何現有的項目。</span><span class="sxs-lookup"><span data-stu-id="95f27-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="95f27-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>和<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性可讓您修改以符合您用途的行為。</span><span class="sxs-lookup"><span data-stu-id="95f27-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="95f27-110">若要控制 TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="95f27-110">To control the insertion point in a TextBox control</span></span>  
  
1. <span data-ttu-id="95f27-111">將 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="95f27-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="95f27-112">零將插入點左邊的第一個字元。</span><span class="sxs-lookup"><span data-stu-id="95f27-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2. <span data-ttu-id="95f27-113">（選擇性）設定<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>屬性，以您想要選取的文字的長度。</span><span class="sxs-lookup"><span data-stu-id="95f27-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="95f27-114">下列程式碼一律會傳回為 0 的插入點。</span><span class="sxs-lookup"><span data-stu-id="95f27-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="95f27-115">`TextBox1_Enter`事件處理常式必須繫結至控制項; 如需詳細資訊，請參閱[建立 Windows Forms 中的事件處理常式](../creating-event-handlers-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="95f27-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="95f27-116">進行預設為可見的插入點</span><span class="sxs-lookup"><span data-stu-id="95f27-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="95f27-117"><xref:System.Windows.Forms.TextBox>插入點位於預設顯示在新的格式只有當<xref:System.Windows.Forms.TextBox>控制項是在定位順序中第一個。</span><span class="sxs-lookup"><span data-stu-id="95f27-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="95f27-118">只有當您提供的插入點，將會出現，否則為<xref:System.Windows.Forms.TextBox>鍵盤或滑鼠焦點。</span><span class="sxs-lookup"><span data-stu-id="95f27-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="95f27-119">若要依預設，新的表單上顯示文字 方塊中的插入點</span><span class="sxs-lookup"><span data-stu-id="95f27-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="95f27-120">設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.Control.TabIndex%2A>屬性設`0`。</span><span class="sxs-lookup"><span data-stu-id="95f27-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f27-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f27-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="95f27-122">TextBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="95f27-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="95f27-123">HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="95f27-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="95f27-124">HOW TO：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="95f27-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="95f27-125">HOW TO：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="95f27-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="95f27-126">HOW TO：選取 Windows Forms TextBox 控制項的文字</span><span class="sxs-lookup"><span data-stu-id="95f27-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="95f27-127">HOW TO：檢視 Windows Forms TextBox 控制項中的多行</span><span class="sxs-lookup"><span data-stu-id="95f27-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="95f27-128">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="95f27-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
