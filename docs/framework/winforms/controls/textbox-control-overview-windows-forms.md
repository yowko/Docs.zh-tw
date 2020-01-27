---
title: TextBox 控制項概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742801"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="ba733-102">TextBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="ba733-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="ba733-103">Windows Forms 文字方塊可用來取得使用者的輸入或顯示文字。</span><span class="sxs-lookup"><span data-stu-id="ba733-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="ba733-104"><xref:System.Windows.Forms.TextBox> 控制項通常用於可編輯的文字，不過它也可以設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="ba733-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="ba733-105">文字方塊可以顯示多行、將文字換成控制項的大小，以及新增基本格式。</span><span class="sxs-lookup"><span data-stu-id="ba733-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="ba733-106"><xref:System.Windows.Forms.TextBox> 控制項會針對顯示或輸入控制項的文字提供單一格式樣式。</span><span class="sxs-lookup"><span data-stu-id="ba733-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="ba733-107">若要顯示多種類型的格式化文字，請使用 <xref:System.Windows.Forms.RichTextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ba733-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ba733-108">如需詳細資訊，請參閱[RichTextBox 控制項總覽](richtextbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="ba733-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="ba733-109">使用 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="ba733-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="ba733-110">控制項所顯示的文字會包含在 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="ba733-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="ba733-111">根據預設，您最多可以在文字方塊中輸入2048個字元。</span><span class="sxs-lookup"><span data-stu-id="ba733-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="ba733-112">如果您將 [<xref:System.Windows.Forms.TextBox.Multiline%2A>] 屬性設定為 [`true`]，則最多可以輸入 32 KB 的文字。</span><span class="sxs-lookup"><span data-stu-id="ba733-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="ba733-113"><xref:System.Windows.Forms.TextBox.Text%2A> 屬性可以在設計階段使用 [屬性] 視窗、在程式碼中的執行時間，或在執行時間由使用者輸入設定。</span><span class="sxs-lookup"><span data-stu-id="ba733-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="ba733-114">您可以藉由讀取 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性，在執行時間抓取文字方塊的目前內容。</span><span class="sxs-lookup"><span data-stu-id="ba733-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="ba733-115">下列程式碼範例會在執行時間設定控制項中的文字。</span><span class="sxs-lookup"><span data-stu-id="ba733-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="ba733-116">`InitializeMyControl` 程式不會自動執行;必須呼叫它。</span><span class="sxs-lookup"><span data-stu-id="ba733-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba733-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba733-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="ba733-118">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="ba733-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="ba733-119">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="ba733-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ba733-120">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="ba733-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="ba733-121">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="ba733-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="ba733-122">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="ba733-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ba733-123">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="ba733-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="ba733-124">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="ba733-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
