---
title: using 陳述式 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: ec4849dda0f28ad1f0e0ebb2c493a33005107db4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480703"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="9df51-102">using 陳述式 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9df51-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="9df51-103">提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。</span><span class="sxs-lookup"><span data-stu-id="9df51-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df51-104">範例</span><span class="sxs-lookup"><span data-stu-id="9df51-104">Example</span></span>  
 <span data-ttu-id="9df51-105">下列範例顯示如何使用 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9df51-105">The following example shows how to use the `using` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="9df51-106">備註</span><span class="sxs-lookup"><span data-stu-id="9df51-106">Remarks</span></span>  
 <span data-ttu-id="9df51-107"><xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。</span><span class="sxs-lookup"><span data-stu-id="9df51-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="9df51-108">還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。</span><span class="sxs-lookup"><span data-stu-id="9df51-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="9df51-109">所有這些類型都會實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="9df51-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="9df51-110">當 `IDisposable` 物件的存留期限制為單一方法時，您應該在 `using` 陳述式中宣告它並加以具現化。</span><span class="sxs-lookup"><span data-stu-id="9df51-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="9df51-111">`using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。</span><span class="sxs-lookup"><span data-stu-id="9df51-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="9df51-112">在 `using` 區塊內，物件是唯讀的，而且無法加以修改或重新指派。</span><span class="sxs-lookup"><span data-stu-id="9df51-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="9df51-113">`using` 陳述式可確保會呼叫 <xref:System.IDisposable.Dispose%2A>，即使在 `using` 區塊內發生例外狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="9df51-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="9df51-114">您可以將物件放在 `try` 區塊內，然後在 `finally` 區塊中呼叫 <xref:System.IDisposable.Dispose%2A>，來達到相同的結果；事實上，這就是編譯器轉譯 `using` 陳述式的方式。</span><span class="sxs-lookup"><span data-stu-id="9df51-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="9df51-115">稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：</span><span class="sxs-lookup"><span data-stu-id="9df51-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 <span data-ttu-id="9df51-116">如需 `try`-`finally` 陳述式的詳細資訊，請參閱 [try-finally](try-finally.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9df51-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>
  
 <span data-ttu-id="9df51-117">您可以在 `using` 陳述式中宣告一種類型的多個執行個體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9df51-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="9df51-118">您可以具現化資源物件，然後將變數傳遞至 `using` 陳述式，但這不是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="9df51-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="9df51-119">在此情況下，控制權離開 `using` 區塊之後，物件仍會留在範圍內，不過它可能無法再存取其非受控資源。</span><span class="sxs-lookup"><span data-stu-id="9df51-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="9df51-120">換句話說，它不再是完全初始化。</span><span class="sxs-lookup"><span data-stu-id="9df51-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="9df51-121">如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。</span><span class="sxs-lookup"><span data-stu-id="9df51-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="9df51-122">因此，通常最好在 `using` 陳述式中具現化物件，並將其範圍限制為 `using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9df51-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="9df51-123">如需處置 `IDisposable` 物件的詳細資訊，請參閱[使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="9df51-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9df51-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9df51-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9df51-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="9df51-125">See Also</span></span>

- [<span data-ttu-id="9df51-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9df51-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9df51-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9df51-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9df51-128">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9df51-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9df51-129">using 指示詞</span><span class="sxs-lookup"><span data-stu-id="9df51-129">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="9df51-130">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="9df51-130">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
- [<span data-ttu-id="9df51-131">使用實作 IDisposable 的物件</span><span class="sxs-lookup"><span data-stu-id="9df51-131">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
- [<span data-ttu-id="9df51-132">IDisposable 介面</span><span class="sxs-lookup"><span data-stu-id="9df51-132">IDisposable interface</span></span>](xref:System.IDisposable)
