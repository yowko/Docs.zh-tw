---
title: "fixed 陳述式 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords: fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="e5288-102">fixed 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e5288-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="e5288-103">`fixed` 陳述式可防止記憶體回收行程重新配置可移動的變數。</span><span class="sxs-lookup"><span data-stu-id="e5288-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="e5288-104">`fixed` 陳述式只能用於[不安全](../../../csharp/language-reference/keywords/unsafe.md)的內容中。</span><span class="sxs-lookup"><span data-stu-id="e5288-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="e5288-105">`Fixed` 也可用來建立[固定大小緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。</span><span class="sxs-lookup"><span data-stu-id="e5288-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="e5288-106">`fixed` 陳述式會將指標設定為 Managed 變數，並在陳述式執行期間「固定」該變數。</span><span class="sxs-lookup"><span data-stu-id="e5288-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="e5288-107">如果未使用 `fixed`，由於記憶體回收可能會意外重新配置變數，因此指向可移動的 Managed 變數沒什麼用處。</span><span class="sxs-lookup"><span data-stu-id="e5288-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="e5288-108">C# 編譯器只能讓您將指標指派給 `fixed` 陳述式中的 Managed 變數。</span><span class="sxs-lookup"><span data-stu-id="e5288-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="e5288-109">您可以使用陣列、字串、固定大小緩衝區或變數位址，來初始化指標。</span><span class="sxs-lookup"><span data-stu-id="e5288-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="e5288-110">下列範例說明如何使用變數位址、陣列和字串。</span><span class="sxs-lookup"><span data-stu-id="e5288-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="e5288-111">如需固定大小緩衝區的詳細資訊，請參閱[固定大小緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。</span><span class="sxs-lookup"><span data-stu-id="e5288-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="e5288-112">您可以初始化多個指標，但這些指標必須屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="e5288-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="e5288-113">若要初始化不同類型的指標，只要巢狀 `fixed` 陳述式即可，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e5288-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="e5288-114">執行陳述式中的程式碼之後，任何固定的變數都會取消固定並受限於記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e5288-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="e5288-115">因此，請不要指向 `fixed` 陳述式之外的變數。</span><span class="sxs-lookup"><span data-stu-id="e5288-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5288-116">您無法修改在 fixed 陳述式中初始化的指標。</span><span class="sxs-lookup"><span data-stu-id="e5288-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="e5288-117">在不安全模式中，您可以配置堆疊上的記憶體，這不受限於記憶體回收，因此不需要固定。</span><span class="sxs-lookup"><span data-stu-id="e5288-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="e5288-118">如需詳細資訊，請參閱 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)。</span><span class="sxs-lookup"><span data-stu-id="e5288-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5288-119">範例</span><span class="sxs-lookup"><span data-stu-id="e5288-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e5288-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e5288-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5288-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5288-121">See Also</span></span>  
 [<span data-ttu-id="e5288-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e5288-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e5288-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e5288-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e5288-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5288-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e5288-125">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="e5288-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="e5288-126">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="e5288-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
