---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040549"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="a9b39-102">未設定物件變數或 With 區塊變數</span><span class="sxs-lookup"><span data-stu-id="a9b39-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="a9b39-103">參考的物件變數無效。</span><span class="sxs-lookup"><span data-stu-id="a9b39-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="a9b39-104">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="a9b39-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="a9b39-105">已宣告變數, 但未指定類型。</span><span class="sxs-lookup"><span data-stu-id="a9b39-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="a9b39-106">如果在未指定類型的情況下宣告變數, 則會預設`Object`為類型。</span><span class="sxs-lookup"><span data-stu-id="a9b39-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="a9b39-107">例如, 以`Dim x`宣告`Object;`的變數會是類型, 以宣告的變數`Dim x As String`會是類型`String`。</span><span class="sxs-lookup"><span data-stu-id="a9b39-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="a9b39-108">語句不允許產生`Object`類型的隱含類型。 `Option Strict`</span><span class="sxs-lookup"><span data-stu-id="a9b39-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="a9b39-109">如果您省略型別, 就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9b39-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="a9b39-110">請參閱[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b39-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="a9b39-111">您嘗試參考已設定為`Nothing`的物件。</span><span class="sxs-lookup"><span data-stu-id="a9b39-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="a9b39-112">您嘗試存取未正確宣告之陣列變數的元素。</span><span class="sxs-lookup"><span data-stu-id="a9b39-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="a9b39-113">例如, 如果您嘗試參考陣列`products() As String` `products(3) = "Widget"`的元素, 則宣告為的陣列將會觸發錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9b39-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="a9b39-114">陣列沒有任何元素, 而且會被視為物件。</span><span class="sxs-lookup"><span data-stu-id="a9b39-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="a9b39-115">您正嘗試在區塊初始化之前, `With...End With`先存取區塊內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9b39-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="a9b39-116">區塊必須藉由`With`執行語句進入點來初始化。 `With...End With`</span><span class="sxs-lookup"><span data-stu-id="a9b39-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="a9b39-117">在舊版的 Visual Basic 或 VBA 中, 也會藉由指派值給變數而不使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`) 來觸發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9b39-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="a9b39-118">`Set`關鍵字在 Visual Basic .net 中已不再有效。</span><span class="sxs-lookup"><span data-stu-id="a9b39-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a9b39-119">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a9b39-119">To correct this error</span></span>

1. <span data-ttu-id="a9b39-120">將`Option Strict`下列`On`程式碼新增至檔案的開頭, 將設為:</span><span class="sxs-lookup"><span data-stu-id="a9b39-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="a9b39-121">當您執行專案時, 如果未指定任何類型的變數, 則會在**錯誤清單**中顯示編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9b39-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="a9b39-122">如果您不想要啟用`Option Strict`, 請在您的程式碼中搜尋未使用類型 (`Dim x`而非`Dim x As String`) 指定的任何變數, 並將所需的類型加入至宣告。</span><span class="sxs-lookup"><span data-stu-id="a9b39-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="a9b39-123">請確定您未參考已設定為`Nothing`的物件變數。</span><span class="sxs-lookup"><span data-stu-id="a9b39-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="a9b39-124">在您的程式碼中`Nothing`搜尋關鍵字, 然後修改您的程式碼, 讓物件`Nothing`不會設定為, 直到您參考它為止。</span><span class="sxs-lookup"><span data-stu-id="a9b39-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="a9b39-125">在存取之前, 請確定所有陣列變數都已建立維度。</span><span class="sxs-lookup"><span data-stu-id="a9b39-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="a9b39-126">您可以在第一次建立陣列時指派維度 (`Dim x(5) As String` `Dim x() As String`而不是`ReDim` ), 或使用關鍵字來設定陣列的維度, 然後再進行第一次存取。</span><span class="sxs-lookup"><span data-stu-id="a9b39-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="a9b39-127">請確定您`With`的區塊是藉由`With`執行語句進入點來初始化。</span><span class="sxs-lookup"><span data-stu-id="a9b39-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9b39-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b39-128">See also</span></span>

- [<span data-ttu-id="a9b39-129">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="a9b39-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="a9b39-130">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="a9b39-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="a9b39-131">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="a9b39-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
