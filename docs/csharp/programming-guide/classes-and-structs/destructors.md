---
title: 完成項 - C# 程式設計手冊
description: 'C # 中的完成項（也稱為「析構函數」）會在垃圾收集行程收集類別實例時，執行任何必要的最後清除。'
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 61a00e766b0f975691b9f2a7c7561bb4f1d33c02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174299"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="e54f5-103">完成項 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e54f5-103">Finalizers (C# Programming Guide)</span></span>

<span data-ttu-id="e54f5-104">完成項 (也稱為**解構函式**) 可在記憶體回收行程收集類別執行個體時，用來執行任何必要的最後清除。</span><span class="sxs-lookup"><span data-stu-id="e54f5-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e54f5-105">備註</span><span class="sxs-lookup"><span data-stu-id="e54f5-105">Remarks</span></span>  
  
- <span data-ttu-id="e54f5-106">無法在結構中定義完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="e54f5-107">它們只能與類別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e54f5-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="e54f5-108">一個類別只能有一個完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="e54f5-109">無法繼承或多載完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="e54f5-110">無法呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-110">Finalizers cannot be called.</span></span> <span data-ttu-id="e54f5-111">會自動呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="e54f5-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="e54f5-112">完成項不會接受修飾詞，也不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="e54f5-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="e54f5-113">例如，下列是 `Car` 類別的完成項宣告。</span><span class="sxs-lookup"><span data-stu-id="e54f5-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="e54f5-114">完成項也可以實作為運算式主體定義，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e54f5-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="e54f5-115">完成項會在物件的基底類別上隱含地呼叫 <xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="e54f5-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="e54f5-116">因此，會將完成項呼叫隱含地轉譯為下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="e54f5-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="e54f5-117">此設計表示 `Finalize` 會針對繼承鏈中的所有實例，以遞迴方式呼叫方法，從最高衍生到最低衍生。</span><span class="sxs-lookup"><span data-stu-id="e54f5-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e54f5-118">不應該使用空的完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="e54f5-119">類別包含完成項時，會在 `Finalize` 佇列中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="e54f5-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="e54f5-120">呼叫完成項時，會叫用記憶體回收行程來處理佇列。</span><span class="sxs-lookup"><span data-stu-id="e54f5-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="e54f5-121">空的完成項只會導致不必要的效能損失。</span><span class="sxs-lookup"><span data-stu-id="e54f5-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="e54f5-122">程式設計師無法控制呼叫完成項的時間;垃圾收集行程會決定呼叫它的時機。</span><span class="sxs-lookup"><span data-stu-id="e54f5-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="e54f5-123">記憶體回收行程會檢查應用程式不再使用的物件。</span><span class="sxs-lookup"><span data-stu-id="e54f5-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="e54f5-124">如果它認為物件適合進行完成，則會呼叫完成項 (如果有的話)，並回收用來儲存物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e54f5-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="e54f5-125">在 .NET Framework 應用程式 (而非 .NET Core 應用程式) 中，程式結束時也會呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="e54f5-126">您可以藉由呼叫來強制進行垃圾收集 <xref:System.GC.Collect%2A> ，但在大部分的情況下，應該避免此呼叫，因為它可能會造成效能問題。</span><span class="sxs-lookup"><span data-stu-id="e54f5-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="e54f5-127">使用完成項來釋放資源</span><span class="sxs-lookup"><span data-stu-id="e54f5-127">Using finalizers to release resources</span></span>  

 <span data-ttu-id="e54f5-128">一般情況下，c # 不需要開發人員的記憶體管理，因為不是以垃圾收集的執行時間為目標的語言。</span><span class="sxs-lookup"><span data-stu-id="e54f5-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="e54f5-129">這是因為 .NET 垃圾收集行程會隱含地管理物件的記憶體配置和釋放。</span><span class="sxs-lookup"><span data-stu-id="e54f5-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="e54f5-130">不過，當您的應用程式封裝非受控資源（例如 windows、檔案和網路連接）時，您應該使用完成項來釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="e54f5-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="e54f5-131">適合完成物件時，記憶體回收行程會執行物件的 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="e54f5-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="e54f5-132">明確釋放資源</span><span class="sxs-lookup"><span data-stu-id="e54f5-132">Explicit release of resources</span></span>  

 <span data-ttu-id="e54f5-133">如果您的應用程式使用過多的外部資源，則也建議您提供一種方式，以在記憶體回收行程釋放物件之前明確釋放資源。</span><span class="sxs-lookup"><span data-stu-id="e54f5-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="e54f5-134">若要釋放資源，請 `Dispose` 從介面執行方法，以 <xref:System.IDisposable> 針對物件執行必要的清除。</span><span class="sxs-lookup"><span data-stu-id="e54f5-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="e54f5-135">這可以大幅改善應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="e54f5-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="e54f5-136">即使對資源使用這個明確的控制，如果呼叫方法失敗，完成項也會成為清除資源的保護措施 `Dispose` 。</span><span class="sxs-lookup"><span data-stu-id="e54f5-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="e54f5-137">如需有關清除資源的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="e54f5-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="e54f5-138">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="e54f5-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="e54f5-139">執行 Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="e54f5-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="e54f5-140">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="e54f5-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="e54f5-141">範例</span><span class="sxs-lookup"><span data-stu-id="e54f5-141">Example</span></span>  

 <span data-ttu-id="e54f5-142">下列範例會建立三個產生繼承鏈結的類別。</span><span class="sxs-lookup"><span data-stu-id="e54f5-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="e54f5-143">`First` 類別是基底類別、`Second` 衍生自 `First`，而 `Third` 衍生自 `Second`。</span><span class="sxs-lookup"><span data-stu-id="e54f5-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="e54f5-144">所有這三個都有完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-144">All three have finalizers.</span></span> <span data-ttu-id="e54f5-145">在 `Main` 中，會建立最高衍生性類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e54f5-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="e54f5-146">程式執行時，請注意，會依最高衍生性到最低衍生性的順序，自動呼叫這三個類別的完成項。</span><span class="sxs-lookup"><span data-stu-id="e54f5-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e54f5-147">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e54f5-147">C# language specification</span></span>  

<span data-ttu-id="e54f5-148">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[解構函式](~/_csharplang/spec/classes.md#destructors)一節。</span><span class="sxs-lookup"><span data-stu-id="e54f5-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e54f5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e54f5-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="e54f5-150">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e54f5-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e54f5-151">建構函式</span><span class="sxs-lookup"><span data-stu-id="e54f5-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e54f5-152">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="e54f5-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
