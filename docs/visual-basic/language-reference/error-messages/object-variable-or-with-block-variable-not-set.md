---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: bde0150e1e20fb96d079e21b593f1ac6e27e6af7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611367"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="5be16-102">未設定物件變數或 With 區塊變數</span><span class="sxs-lookup"><span data-stu-id="5be16-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="5be16-103">正在參考無效的物件變數。</span><span class="sxs-lookup"><span data-stu-id="5be16-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="5be16-104">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="5be16-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="5be16-105">未指定類型所宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="5be16-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="5be16-106">如果未指定的型別宣告變數，則預設為輸入`Object`。</span><span class="sxs-lookup"><span data-stu-id="5be16-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="5be16-107">例如，以宣告的變數`Dim x`的型別`Object;`以宣告的變數`Dim x As String`的型別`String`。</span><span class="sxs-lookup"><span data-stu-id="5be16-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="5be16-108">`Option Strict`陳述式不允許隱含型別，會導致`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="5be16-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="5be16-109">如果您省略類型時，會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5be16-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="5be16-110">請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5be16-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="5be16-111">您嘗試參考已設定為物件 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="5be16-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="5be16-112">。</span><span class="sxs-lookup"><span data-stu-id="5be16-112">.</span></span>  
  
-   <span data-ttu-id="5be16-113">您嘗試存取未正確地宣告陣列變數的項目。</span><span class="sxs-lookup"><span data-stu-id="5be16-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="5be16-114">例如，陣列宣告為`products() As String`如果您嘗試參考陣列項目，將會觸發錯誤`products(3) = "Widget"`。</span><span class="sxs-lookup"><span data-stu-id="5be16-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="5be16-115">陣列沒有任何項目，並會被視為物件。</span><span class="sxs-lookup"><span data-stu-id="5be16-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="5be16-116">您嘗試存取程式碼內`With...End With`區塊之前尚未初始化的區塊。</span><span class="sxs-lookup"><span data-stu-id="5be16-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="5be16-117">A`With...End With`區塊必須初始化執行`With`陳述式的進入點。</span><span class="sxs-lookup"><span data-stu-id="5be16-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5be16-118">在舊版的 Visual Basic 或 VBA 這項錯誤也觸發指派給變數的值，而不使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`)。</span><span class="sxs-lookup"><span data-stu-id="5be16-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="5be16-119">`Set`關鍵字已不再有效 Visual Basic.Net 中。</span><span class="sxs-lookup"><span data-stu-id="5be16-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5be16-120">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5be16-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="5be16-121">設定`Option Strict`至`On`藉由將下列程式碼新增至檔案的開頭：</span><span class="sxs-lookup"><span data-stu-id="5be16-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="5be16-122">如果您不想要啟用`Option Strict`，搜尋您的程式碼所指定型別沒有任何變數 (`Dim x`而不是`Dim x As String`) 並將預定的型別新增至宣告。</span><span class="sxs-lookup"><span data-stu-id="5be16-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="5be16-123">請確定您已設定為物件變數不參考`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="5be16-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="5be16-124">搜尋您的程式碼，關鍵字`Nothing`，和修訂您的程式碼，讓物件未設定為`Nothing`直到之後，您已參考它。</span><span class="sxs-lookup"><span data-stu-id="5be16-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="5be16-125">請確定陣列的任何變數建立維度，才能存取它們。</span><span class="sxs-lookup"><span data-stu-id="5be16-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="5be16-126">當您第一次建立陣列時，您可以是指派維度 (`Dim x(5) As String`而非`Dim x() As String`)，或使用`ReDim`設定陣列的維度，然後第一次存取關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5be16-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="5be16-127">請確定您`With`區塊會藉由執行初始化`With`陳述式的進入點。</span><span class="sxs-lookup"><span data-stu-id="5be16-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be16-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5be16-128">See also</span></span>
- [<span data-ttu-id="5be16-129">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="5be16-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="5be16-130">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5be16-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="5be16-131">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="5be16-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
