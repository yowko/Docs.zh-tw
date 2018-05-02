---
title: fixed 陳述式 (C# 參考)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="1a383-102">fixed 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a383-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="1a383-103">`fixed` 陳述式可防止記憶體回收行程重新配置可移動的變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="1a383-104">`fixed` 陳述式只能用於[不安全](unsafe.md)的內容中。</span><span class="sxs-lookup"><span data-stu-id="1a383-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="1a383-105">`Fixed` 也可用來建立[固定大小緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。</span><span class="sxs-lookup"><span data-stu-id="1a383-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="1a383-106">`fixed` 陳述式會將指標設定為 Managed 變數，並在陳述式執行期間「固定」該變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="1a383-107">可移動之受控變數的指標只適用於 `fixed` 內容。</span><span class="sxs-lookup"><span data-stu-id="1a383-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="1a383-108">如果未使用 `fixed` 內容，記憶體回收可能會意外地重新配置變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="1a383-109">C# 編譯器只能讓您將指標指派給 `fixed` 陳述式中的 Managed 變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="1a383-110">您可以使用陣列、字串、固定大小緩衝區或變數位址，來初始化指標。</span><span class="sxs-lookup"><span data-stu-id="1a383-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="1a383-111">下列範例說明如何使用變數位址、陣列和字串。</span><span class="sxs-lookup"><span data-stu-id="1a383-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="1a383-112">如需固定大小緩衝區的詳細資訊，請參閱[固定大小緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。</span><span class="sxs-lookup"><span data-stu-id="1a383-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="1a383-113">如果指標的型別全都相同，則可以在一個陳述式中初始化多個指標：</span><span class="sxs-lookup"><span data-stu-id="1a383-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="1a383-114">若要初始化不同類型的指標，只要巢狀 `fixed` 陳述式即可，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1a383-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="1a383-115">執行陳述式中的程式碼之後，任何固定的變數都會取消固定並受限於記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1a383-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="1a383-116">因此，請不要指向 `fixed` 陳述式之外的變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="1a383-117">`fixed` 陳述式中所宣告變數的範圍會設為該陳述式，使其更加簡單：</span><span class="sxs-lookup"><span data-stu-id="1a383-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="1a383-118">在 `fixed` 陳述式中初始化的指標是唯讀變數。</span><span class="sxs-lookup"><span data-stu-id="1a383-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="1a383-119">如果您要修改指標值，則必須宣告第二個指標變數並予以修改。</span><span class="sxs-lookup"><span data-stu-id="1a383-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="1a383-120">在 `fixed` 陳述式中宣告的變數無法修改：</span><span class="sxs-lookup"><span data-stu-id="1a383-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="1a383-121">在不安全模式中，您可以配置堆疊上的記憶體，這不受限於記憶體回收，因此不需要固定。</span><span class="sxs-lookup"><span data-stu-id="1a383-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="1a383-122">如需詳細資訊，請參閱 [stackalloc](stackalloc.md)。</span><span class="sxs-lookup"><span data-stu-id="1a383-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="1a383-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1a383-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1a383-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a383-124">See Also</span></span>

 [<span data-ttu-id="1a383-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1a383-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="1a383-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a383-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="1a383-127">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a383-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="1a383-128">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="1a383-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="1a383-129">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="1a383-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
