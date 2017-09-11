---
title: "物件變數或 With 區塊變數未設定 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4db2c827c3e77cfa6cc51132f0d647a58c93c769
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="b6d2c-102">未設定物件變數或 With 區塊變數</span><span class="sxs-lookup"><span data-stu-id="b6d2c-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="b6d2c-103">正在參考無效的物件變數。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="b6d2c-104">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="b6d2c-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="b6d2c-105">變數已宣告但未指定的型別。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="b6d2c-106">如果沒有指定型別宣告變數，則預設為輸入`Object`。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="b6d2c-107">宣告的變數，例如`Dim x`屬於型別`Object;`所宣告的變數`Dim x As String`的型別會是`String`。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b6d2c-108">`Option Strict`陳述式不允許隱含型別，而產生的`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="b6d2c-109">如果您省略類型，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="b6d2c-110">請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="b6d2c-111">您嘗試參考已設定為物件`Nothing`</span><span class="sxs-lookup"><span data-stu-id="b6d2c-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="b6d2c-112">。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-112">.</span></span>  
  
-   <span data-ttu-id="b6d2c-113">您嘗試存取的項目未正確宣告陣列變數。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="b6d2c-114">例如，陣列宣告為`products() As String`如果您嘗試將參考陣列的項目將會觸發錯誤`products(3) = "Widget"`。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="b6d2c-115">陣列沒有項目，因此會被視為物件。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="b6d2c-116">您嘗試存取程式碼內`With...End With`封鎖之前已初始化的區塊。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="b6d2c-117">A`With...End With`區塊必須初始化執行`With`陳述式的進入點。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6d2c-118">在舊版的 Visual Basic 或 VBA 此錯誤也已觸發的值指派給變數，而不需使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`)。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="b6d2c-119">`Set`關鍵字已不再有效，在 Visual Basic.Net。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6d2c-120">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b6d2c-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="b6d2c-121">設定`Option Strict`至`On`檔案的開頭加入下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="b6d2c-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="b6d2c-122">如果您不想要啟用`Option Strict`，搜尋您指定了不具型別的任何變數的程式碼 (`Dim x`而不是`Dim x As String`)，並新增至宣告預期的類型。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="b6d2c-123">請確定已設定為物件變數，您不參考`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="b6d2c-124">搜尋關鍵字的程式碼`Nothing`，並修改您的程式碼，讓物件未設定為 `Nothing`直到您之後參考它。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="b6d2c-125">請確定陣列的任何變數建立維度，才能存取它們。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="b6d2c-126">您可以指派維度當您首次建立陣列 (`Dim x(5) As String`而不是`Dim x() As String`)，或使用`ReDim`關鍵字來設定陣列的維度，第一次存取之前。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="b6d2c-127">請確定您`With`區塊會藉由執行初始化`With`陳述式的進入點。</span><span class="sxs-lookup"><span data-stu-id="b6d2c-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d2c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d2c-128">See Also</span></span>  
 <span data-ttu-id="b6d2c-129">[物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="b6d2c-129">[Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="b6d2c-130"> [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b6d2c-130"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="b6d2c-131"> [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b6d2c-131"> [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
