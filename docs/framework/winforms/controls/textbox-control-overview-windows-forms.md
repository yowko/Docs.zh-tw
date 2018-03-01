---
title: "TextBox 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="4cc62-102">TextBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4cc62-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="4cc62-103">Windows Form 的文字方塊會用來從使用者取得輸入或顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="4cc62-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="4cc62-104"><xref:System.Windows.Forms.TextBox>控制項通常用於編輯的文字，不過它也可以設定為唯讀。</span><span class="sxs-lookup"><span data-stu-id="4cc62-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="4cc62-105">文字方塊可以顯示多行、 文字換行到控制項的大小和加入基本的格式。</span><span class="sxs-lookup"><span data-stu-id="4cc62-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="4cc62-106"><xref:System.Windows.Forms.TextBox>控制項提供單一的格式樣式的文字顯示，或輸入控制項。</span><span class="sxs-lookup"><span data-stu-id="4cc62-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="4cc62-107">若要顯示多種類型的格式化的文字，請使用<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="4cc62-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="4cc62-108">如需詳細資訊，請參閱[RichTextBox 控制項概觀](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="4cc62-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="4cc62-109">使用 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="4cc62-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="4cc62-110">控制項所顯示的文字包含於<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4cc62-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="4cc62-111">根據預設，您可以輸入最多 2048年個字元，在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="4cc62-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="4cc62-112">如果您設定<xref:System.Windows.Forms.TextBox.Multiline%2A>屬性`true`，您可以輸入最多 32 KB 的文字。</span><span class="sxs-lookup"><span data-stu-id="4cc62-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="4cc62-113"><xref:System.Windows.Forms.TextBox.Text%2A>屬性可以在 [屬性] 視窗中，以在執行階段的執行階段程式碼，或由使用者輸入的設計階段設定。</span><span class="sxs-lookup"><span data-stu-id="4cc62-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="4cc62-114">可以在執行階段擷取的文字方塊中目前的內容，藉由讀取<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4cc62-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="4cc62-115">下列程式碼範例會設定在執行階段控制項中的文字。</span><span class="sxs-lookup"><span data-stu-id="4cc62-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="4cc62-116">`InitializeMyControl`程序將不會自動執行，它必須進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="4cc62-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cc62-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cc62-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="4cc62-118">操作說明：控制 Windows Forms TextBox 控制項中的插入點</span><span class="sxs-lookup"><span data-stu-id="4cc62-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="4cc62-119">操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊</span><span class="sxs-lookup"><span data-stu-id="4cc62-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="4cc62-120">操作說明：建立唯讀文字方塊</span><span class="sxs-lookup"><span data-stu-id="4cc62-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="4cc62-121">操作說明：將引號放入字串中</span><span class="sxs-lookup"><span data-stu-id="4cc62-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="4cc62-122">操作說明：在 Windows Forms TextBox 控制項中選取文字</span><span class="sxs-lookup"><span data-stu-id="4cc62-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="4cc62-123">操作說明：在 Windows Forms TextBox 控制項中檢視多行</span><span class="sxs-lookup"><span data-stu-id="4cc62-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="4cc62-124">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="4cc62-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
