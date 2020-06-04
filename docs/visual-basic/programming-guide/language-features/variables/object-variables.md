---
title: 物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410331"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="d4ecd-102">Visual Basic 中的物件變數</span><span class="sxs-lookup"><span data-stu-id="d4ecd-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="d4ecd-103">除了直接儲存值之外，變數也可以參考物件。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="d4ecd-104">將物件指派給變數的原因，是因為您將任何值指派給變數：</span><span class="sxs-lookup"><span data-stu-id="d4ecd-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="d4ecd-105">變數名稱通常比存取物件本身所需之方法和屬性的完整路徑更短且更容易記憶。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="d4ecd-106">使用參考物件的變數會比透過必要的方法或屬性重複存取物件本身更有效率。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="d4ecd-107">當您的程式碼正在執行時，您可以變更變數來參考其他物件。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="d4ecd-108">使程式碼更短</span><span class="sxs-lookup"><span data-stu-id="d4ecd-108">Making Code Shorter</span></span>

<span data-ttu-id="d4ecd-109">您可以使用物件變數來縮短您必須輸入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="d4ecd-110">下列範例會使用方法和屬性的完整路徑來存取 <xref:System.Windows.Forms.Control> 物件。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="d4ecd-111">如果您使用控制項的物件變數，可以縮短此程式碼並加快執行速度。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="d4ecd-112">您應該使用您想要指派給它的特定類別（ `Control` 在此案例中為）來宣告物件變數。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="d4ecd-113">將物件指派給變數之後，您就可以將它視為您處理它所參考的物件完全相同。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="d4ecd-114">您可以設定或取出物件的屬性，或使用其任何方法。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="d4ecd-115">下列範例會使用物件變數來簡化上述範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4ecd-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="d4ecd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ecd-116">See also</span></span>

- [<span data-ttu-id="d4ecd-117">變數宣告</span><span class="sxs-lookup"><span data-stu-id="d4ecd-117">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="d4ecd-118">如何：加快存取具有限定性條件長路徑的物件</span><span class="sxs-lookup"><span data-stu-id="d4ecd-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="d4ecd-119">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="d4ecd-119">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="d4ecd-120">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="d4ecd-120">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="d4ecd-121">物件變數值</span><span class="sxs-lookup"><span data-stu-id="d4ecd-121">Object Variable Values</span></span>](object-variable-values.md)
