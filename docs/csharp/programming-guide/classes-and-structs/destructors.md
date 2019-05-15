---
title: 完成項 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 87755eadeaebb72c5a8ce147ba2e6faf109e6c12
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584378"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="72101-102">完成項 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="72101-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="72101-103">完成項 (也稱為**解構函式**) 可在記憶體回收行程收集類別執行個體時，用來執行任何必要的最後清除。</span><span class="sxs-lookup"><span data-stu-id="72101-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72101-104">備註</span><span class="sxs-lookup"><span data-stu-id="72101-104">Remarks</span></span>  
  
- <span data-ttu-id="72101-105">無法在結構中定義完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="72101-106">它們只能與類別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="72101-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="72101-107">一個類別只能有一個完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="72101-108">無法繼承或多載完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="72101-109">無法呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-109">Finalizers cannot be called.</span></span> <span data-ttu-id="72101-110">會自動呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="72101-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="72101-111">完成項不會接受修飾詞，也不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="72101-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="72101-112">例如，下列是 `Car` 類別的完成項宣告。</span><span class="sxs-lookup"><span data-stu-id="72101-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="72101-113">完成項也可以實作為運算式主體定義，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="72101-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="72101-114">完成項會在物件的基底類別上隱含地呼叫 <xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="72101-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="72101-115">因此，會將完成項呼叫隱含地轉譯為下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="72101-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="72101-116">這表示，會依最高衍生性到最低衍生性的順序，對繼承鏈結中的所有執行個體遞迴呼叫 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="72101-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72101-117">不應該使用空的完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="72101-118">類別包含完成項時，會在 `Finalize` 佇列中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="72101-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="72101-119">呼叫完成項時，會叫用記憶體回收行程來處理佇列。</span><span class="sxs-lookup"><span data-stu-id="72101-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="72101-120">空的完成項只會導致不必要的效能損失。</span><span class="sxs-lookup"><span data-stu-id="72101-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="72101-121">因為這是由記憶體回收行程所決定，所以程式設計人員無法控制完成項的呼叫時機。</span><span class="sxs-lookup"><span data-stu-id="72101-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="72101-122">記憶體回收行程會檢查應用程式不再使用的物件。</span><span class="sxs-lookup"><span data-stu-id="72101-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="72101-123">如果它認為物件適合進行完成，則會呼叫完成項 (如果有的話)，並回收用來儲存物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="72101-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="72101-124">在 .NET Framework 應用程式 (而非 .NET Core 應用程式) 中，程式結束時也會呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="72101-125">呼叫 <xref:System.GC.Collect%2A> 可能會強制執行記憶體回收，但在大部分的情況下，這種情況可能會造成效能問題，因此應該予以避免。</span><span class="sxs-lookup"><span data-stu-id="72101-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="72101-126">使用完成項來釋放資源</span><span class="sxs-lookup"><span data-stu-id="72101-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="72101-127">一般而言，C# 所需要的記憶體管理，會少於使用不以具有記憶體回收的執行階段為目標之語言進行開發所需的記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="72101-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="72101-128">這是因為 .NET Framework 記憶體回收行程會隱含地管理您物件的記憶體配置和釋放。</span><span class="sxs-lookup"><span data-stu-id="72101-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="72101-129">不過，您的應用程式封裝視窗、檔案和網路連線這類未受管理資源時，應該使用完成項來釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="72101-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="72101-130">適合完成物件時，記憶體回收行程會執行物件的 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="72101-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="72101-131">明確釋放資源</span><span class="sxs-lookup"><span data-stu-id="72101-131">Explicit release of resources</span></span>  
 <span data-ttu-id="72101-132">如果您的應用程式使用過多的外部資源，則也建議您提供一種方式，以在記憶體回收行程釋放物件之前明確釋放資源。</span><span class="sxs-lookup"><span data-stu-id="72101-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="72101-133">做法是從對物件執行必要清除的 <xref:System.IDisposable> 介面實作 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="72101-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="72101-134">這可以大幅改善應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="72101-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="72101-135">即使對資源使用這個明確控制，如果 `Dispose` 方法呼叫失敗，完成項還是會成為清除資源的保護措施。</span><span class="sxs-lookup"><span data-stu-id="72101-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="72101-136">如需清除資源的詳細資訊，請參閱下列主題︰</span><span class="sxs-lookup"><span data-stu-id="72101-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="72101-137">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="72101-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="72101-138">實作 Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="72101-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="72101-139">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="72101-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="72101-140">範例</span><span class="sxs-lookup"><span data-stu-id="72101-140">Example</span></span>  
 <span data-ttu-id="72101-141">下列範例會建立三個產生繼承鏈結的類別。</span><span class="sxs-lookup"><span data-stu-id="72101-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="72101-142">`First` 類別是基底類別、`Second` 衍生自 `First`，而 `Third` 衍生自 `Second`。</span><span class="sxs-lookup"><span data-stu-id="72101-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="72101-143">所有這三個都有完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-143">All three have finalizers.</span></span> <span data-ttu-id="72101-144">在 `Main` 中，會建立最高衍生性類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72101-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="72101-145">程式執行時，請注意，會依最高衍生性到最低衍生性的順序，自動呼叫這三個類別的完成項。</span><span class="sxs-lookup"><span data-stu-id="72101-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="72101-146">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="72101-146">C# language specification</span></span>  

<span data-ttu-id="72101-147">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[解構函式](~/_csharplang/spec/classes.md#destructors)一節。</span><span class="sxs-lookup"><span data-stu-id="72101-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="72101-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72101-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="72101-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="72101-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="72101-150">建構函式</span><span class="sxs-lookup"><span data-stu-id="72101-150">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="72101-151">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="72101-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
