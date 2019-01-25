---
title: Visual Basic 中的物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 046119664fc0277a6a5305d0cf086b4438b13f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685460"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="23e69-102">Visual Basic 中的物件變數</span><span class="sxs-lookup"><span data-stu-id="23e69-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="23e69-103">除了直接將值儲存，變數可以參考的物件。</span><span class="sxs-lookup"><span data-stu-id="23e69-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="23e69-104">您指派給變數物件的任何值指派給變數相同的原因：</span><span class="sxs-lookup"><span data-stu-id="23e69-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="23e69-105">變數的名稱通常是較短且更容易記住比方法和屬性來存取物件本身所需的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="23e69-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="23e69-106">使用的變數來參考的物件會比重複地透過必要的方法或屬性存取物件本身更有效率。</span><span class="sxs-lookup"><span data-stu-id="23e69-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="23e69-107">您可以變更變數，以執行您的程式碼時，對其他物件參考。</span><span class="sxs-lookup"><span data-stu-id="23e69-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="23e69-108">縮短程式碼</span><span class="sxs-lookup"><span data-stu-id="23e69-108">Making Code Shorter</span></span>  
 <span data-ttu-id="23e69-109">您可以使用物件變數來縮短必須輸入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23e69-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="23e69-110">下列範例會使用的方法和屬性的完整路徑來存取<xref:System.Windows.Forms.Control>物件。</span><span class="sxs-lookup"><span data-stu-id="23e69-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="23e69-111">您可以縮短這段程式碼，並加速執行，如果您使用控制項的物件變數。</span><span class="sxs-lookup"><span data-stu-id="23e69-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="23e69-112">您應該宣告物件變數，您想要為其指派的特定類別 (`Control`在此情況下)。</span><span class="sxs-lookup"><span data-stu-id="23e69-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="23e69-113">一旦您將物件指派給變數時，您可以將它完全相同，您將它所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="23e69-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="23e69-114">您可以設定或擷取物件的屬性，或使用它的任何方法。</span><span class="sxs-lookup"><span data-stu-id="23e69-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="23e69-115">下列範例會使用物件變數，以簡化在上述範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23e69-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="23e69-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23e69-116">See also</span></span>
- [<span data-ttu-id="23e69-117">變數宣告</span><span class="sxs-lookup"><span data-stu-id="23e69-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="23e69-118">如何：加快存取具有限定性條件長路徑的物件</span><span class="sxs-lookup"><span data-stu-id="23e69-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="23e69-119">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="23e69-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="23e69-120">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="23e69-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="23e69-121">物件變數值</span><span class="sxs-lookup"><span data-stu-id="23e69-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
