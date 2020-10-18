---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 5eff7622ce2a35cf2846c5141cede98ea033d708
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159881"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="24bbb-102">未設定物件變數或 With 區塊變數</span><span class="sxs-lookup"><span data-stu-id="24bbb-102">Object variable or With block variable not set</span></span>

<span data-ttu-id="24bbb-103">參考了不正確物件變數。</span><span class="sxs-lookup"><span data-stu-id="24bbb-103">An invalid object variable is being referenced.</span></span> <span data-ttu-id="24bbb-104">發生這個錯誤的原因有下列幾種︰</span><span class="sxs-lookup"><span data-stu-id="24bbb-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="24bbb-105">宣告的變數未指定類型。</span><span class="sxs-lookup"><span data-stu-id="24bbb-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="24bbb-106">如果宣告的變數未指定類型，則會預設為類型 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="24bbb-107">例如，使用宣告的變數 `Dim x` 的類型會是類型 `Object;` `Dim x As String` `String` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="24bbb-108">`Option Strict`語句不允許隱含型別產生型別 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="24bbb-109">如果您省略型別，就會發生編譯階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="24bbb-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="24bbb-110">請參閱 [Option Strict 語句](../statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="24bbb-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="24bbb-111">您正在嘗試參考已設定為的物件 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="24bbb-112">您嘗試存取的陣列變數元素未正確宣告。</span><span class="sxs-lookup"><span data-stu-id="24bbb-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="24bbb-113">例如，如果您嘗試參考陣列的元素，則宣告為的陣列 `products() As String` 將會觸發錯誤 `products(3) = "Widget"` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="24bbb-114">陣列沒有元素，並被視為物件。</span><span class="sxs-lookup"><span data-stu-id="24bbb-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="24bbb-115">您正在嘗試先存取區塊內的程式碼 `With...End With` ，再初始化區塊。</span><span class="sxs-lookup"><span data-stu-id="24bbb-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="24bbb-116">`With...End With`區塊必須藉由執行 `With` 語句進入點來初始化。</span><span class="sxs-lookup"><span data-stu-id="24bbb-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="24bbb-117">在舊版的 Visual Basic 或 VBA 中，此錯誤也會藉由指派值給變數來觸發，而不使用 `Set` 關鍵字 (， `x = "name"` 而不是 `Set x = "name"`) 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-117">In earlier versions of Visual Basic or VBA, this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="24bbb-118">`Set`Visual Basic .net 中的關鍵字已不再有效。</span><span class="sxs-lookup"><span data-stu-id="24bbb-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="24bbb-119">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="24bbb-119">To correct this error</span></span>

1. <span data-ttu-id="24bbb-120">將 `Option Strict` `On` 下列程式碼新增至檔案的開頭，以將設定為：</span><span class="sxs-lookup"><span data-stu-id="24bbb-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="24bbb-121">當您執行專案時，如果未指定類型，則會在 **錯誤清單** 中顯示編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="24bbb-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="24bbb-122">如果您不想要啟用 `Option Strict` ，請在您的程式碼中搜尋未指定類型的任何變數 (`Dim x` 而不是 `Dim x As String`) ，然後將所需的類型加入至宣告。</span><span class="sxs-lookup"><span data-stu-id="24bbb-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="24bbb-123">請確定您未參考已設定為的物件變數 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="24bbb-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="24bbb-124">搜尋您的程式碼中的關鍵字 `Nothing` ，並修改您的程式碼，使物件在 `Nothing` 您參考它之前都不會設定為。</span><span class="sxs-lookup"><span data-stu-id="24bbb-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="24bbb-125">在您存取陣列變數之前，請先確定其已建立維度。</span><span class="sxs-lookup"><span data-stu-id="24bbb-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="24bbb-126">當您第一次建立陣列 (`Dim x(5) As String` 而不是) 時，您可以指派維度 `Dim x() As String` ，或在 `ReDim` 第一次存取陣列之前使用關鍵字來設定陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="24bbb-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="24bbb-127">請確定您的 `With` 區塊是藉由執行 `With` 語句進入點來初始化。</span><span class="sxs-lookup"><span data-stu-id="24bbb-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="24bbb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24bbb-128">See also</span></span>

- [<span data-ttu-id="24bbb-129">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="24bbb-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="24bbb-130">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="24bbb-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="24bbb-131">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="24bbb-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
