---
title: TextBox 控制項概觀 (Windows Form)
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
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932544"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="07439-102">TextBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="07439-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="07439-103">Windows Form 文字方塊用來從使用者取得輸入，或顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="07439-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="07439-104"><xref:System.Windows.Forms.TextBox>控制項通常使用於可編輯的文字，雖然它可以也成為唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="07439-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="07439-105">文字方塊可以顯示多行、 文字換行到控制項的大小和加入基本的格式。</span><span class="sxs-lookup"><span data-stu-id="07439-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="07439-106"><xref:System.Windows.Forms.TextBox>控制項提供單一的格式樣式顯示，或輸入控制項的文字。</span><span class="sxs-lookup"><span data-stu-id="07439-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="07439-107">若要顯示多種類型的格式化文字，請使用<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="07439-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="07439-108">如需詳細資訊，請參閱 < [RichTextBox 控制項概觀](richtextbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="07439-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="07439-109">使用 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="07439-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="07439-110">控制項所顯示的文字包含在<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="07439-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="07439-111">根據預設，您可以輸入最多 2048年個字元，在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="07439-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="07439-112">如果您設定<xref:System.Windows.Forms.TextBox.Multiline%2A>屬性設`true`，您可以輸入最多 32 KB 的文字。</span><span class="sxs-lookup"><span data-stu-id="07439-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="07439-113"><xref:System.Windows.Forms.TextBox.Text%2A>屬性可以在 [屬性] 視窗中，以在執行階段程式碼，或由使用者輸入，在執行階段的設計階段設定。</span><span class="sxs-lookup"><span data-stu-id="07439-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="07439-114">目前文字方塊的內容可以在執行階段擷取，請閱讀<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="07439-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="07439-115">下列程式碼範例會設定在執行階段控制項中的文字。</span><span class="sxs-lookup"><span data-stu-id="07439-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="07439-116">`InitializeMyControl`程序將不會自動執行; 它必須先呼叫。</span><span class="sxs-lookup"><span data-stu-id="07439-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07439-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07439-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="07439-118">如何：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="07439-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="07439-119">如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="07439-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="07439-120">如何：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="07439-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="07439-121">如何：將引號放入字串</span><span class="sxs-lookup"><span data-stu-id="07439-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="07439-122">如何：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="07439-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="07439-123">如何：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="07439-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="07439-124">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="07439-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
