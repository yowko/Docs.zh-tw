---
title: "實作 Dispose 方法"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5a304c48a953b172cbcc3aa1c717a660298d36a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-dispose-method"></a><span data-ttu-id="4ea38-102">實作 Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="4ea38-102">Implementing a Dispose method</span></span>

<span data-ttu-id="4ea38-103">您實作<xref:System.IDisposable.Dispose%2A>方法，以釋放您的應用程式所使用的 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="4ea38-103">You implement a <xref:System.IDisposable.Dispose%2A> method to release unmanaged resources used by your application.</span></span> <span data-ttu-id="4ea38-104">.NET 記憶體回收行程不會配置或釋放 Unmanaged 記憶體。</span><span class="sxs-lookup"><span data-stu-id="4ea38-104">The .NET garbage collector does not allocate or release unmanaged memory.</span></span>  
  
<span data-ttu-id="4ea38-105">處置物件的模式稱為[處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md)，會在物件存留期上安排順序。</span><span class="sxs-lookup"><span data-stu-id="4ea38-105">The pattern for disposing an object, referred to as a [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md), imposes order on the lifetime of an object.</span></span> <span data-ttu-id="4ea38-106">處置模式僅適用於存取 Unmanaged 資源的物件，例如檔案和管道控制碼、註冊控制代碼、等候控制代碼，或是 Unmanaged 記憶體區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="4ea38-106">The dispose pattern is used only for objects that access unmanaged resources, such as file and pipe handles, registry handles, wait handles, or pointers to blocks of unmanaged memory.</span></span> <span data-ttu-id="4ea38-107">這是因為記憶體回收行程在回收未使用的 Managed 物件方面相當有效率，但是它無法回收 Unmanaged 物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-107">This is because the garbage collector is very efficient at reclaiming unused managed objects, but it is unable to reclaim unmanaged objects.</span></span>  
  
<span data-ttu-id="4ea38-108">處置模式有兩種：</span><span class="sxs-lookup"><span data-stu-id="4ea38-108">The dispose pattern has two variations:</span></span>  
  
* <span data-ttu-id="4ea38-109">將類型使用的每一種 Unmanaged 資源包裝在安全控制代碼中 (也就是在衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 的類別中)。</span><span class="sxs-lookup"><span data-stu-id="4ea38-109">You wrap each unmanaged resource that a type uses in a safe handle (that is, in a class derived from <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>).</span></span> <span data-ttu-id="4ea38-110">在這種情況下，請實作 <xref:System.IDisposable> 介面和額外的 `Dispose(Boolean)` 方法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-110">In this case, you implement the <xref:System.IDisposable> interface and an additional `Dispose(Boolean)` method.</span></span> <span data-ttu-id="4ea38-111">這是建議的做法，這種做法不需要覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-111">This is the recommended variation and doesn't require overriding the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span>  
  
  > [!NOTE]
  > <span data-ttu-id="4ea38-112"><xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType>命名空間提供一組類別衍生自<xref:System.Runtime.InteropServices.SafeHandle>，列出這些[使用安全控制代碼](#SafeHandles)> 一節。</span><span class="sxs-lookup"><span data-stu-id="4ea38-112">The <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> namespace provides a set of classes derived from <xref:System.Runtime.InteropServices.SafeHandle>, which are listed in the [Using safe handles](#SafeHandles) section.</span></span> <span data-ttu-id="4ea38-113">如果您找不到適合釋放 Unmanaged 資源的類別，可以實作自有的 <xref:System.Runtime.InteropServices.SafeHandle> 子類別。</span><span class="sxs-lookup"><span data-stu-id="4ea38-113">If you can't find a class that is suitable for releasing your unmanaged resource, you can implement your own subclass of <xref:System.Runtime.InteropServices.SafeHandle>.</span></span>  
  
* <span data-ttu-id="4ea38-114">除了實作 <xref:System.IDisposable> 介面和額外的 `Dispose(Boolean)` 方法之外，還要覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-114">You implement the <xref:System.IDisposable> interface and an additional `Dispose(Boolean)` method, and you also override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ea38-115">您必須覆寫 <xref:System.Object.Finalize%2A>，才能確保類型消費者未呼叫您的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作時，Unmanaged 資源仍會獲得處置。</span><span class="sxs-lookup"><span data-stu-id="4ea38-115">You must override <xref:System.Object.Finalize%2A> to ensure that unmanaged resources are disposed of if your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation is not called by a consumer of your type.</span></span> <span data-ttu-id="4ea38-116">如果您採用前一項所討論的建議技術，<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 類別會自動為您完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="4ea38-116">If you use the recommended technique discussed in the previous bullet, the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class does this on your behalf.</span></span>  
  
<span data-ttu-id="4ea38-117">若要確保資源永遠都能適當清除，<xref:System.IDisposable.Dispose%2A> 方法應該能夠被呼叫多次而不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4ea38-117">To help ensure that resources are always cleaned up appropriately, a <xref:System.IDisposable.Dispose%2A> method should be callable multiple times without throwing an exception.</span></span>  
  
<span data-ttu-id="4ea38-118">此處所提供的 <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> 方法程式碼範例，顯示積極記憶體回收如何在被回收的物件仍在執行時，即讓完成項開始執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-118">The code example provided for the <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> method shows how aggressive garbage collection can cause a finalizer to run while a member of the reclaimed object is still executing.</span></span> <span data-ttu-id="4ea38-119">在冗長的 <xref:System.GC.KeepAlive%2A> 方法結尾處呼叫 <xref:System.IDisposable.Dispose%2A> 方法，這是個不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-119">It is a good idea to call the <xref:System.GC.KeepAlive%2A> method at the end of a lengthy <xref:System.IDisposable.Dispose%2A> method.</span></span>  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a><span data-ttu-id="4ea38-120">Dispose() 和 Dispose(Boolean)</span><span class="sxs-lookup"><span data-stu-id="4ea38-120">Dispose() and Dispose(Boolean)</span></span>  

<span data-ttu-id="4ea38-121"><xref:System.IDisposable> 介面要求實作單一無參數方法 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="4ea38-121">The <xref:System.IDisposable> interface requires the implementation of a single parameterless method, <xref:System.IDisposable.Dispose%2A>.</span></span> <span data-ttu-id="4ea38-122">不過，處置模式要求實作兩種 `Dispose` 方法：</span><span class="sxs-lookup"><span data-stu-id="4ea38-122">However, the dispose pattern requires two `Dispose` methods to be implemented:</span></span>  
  
* <span data-ttu-id="4ea38-123">公用非虛擬 (在 Visual Basic 中為 `NonInheritable`) 的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作，而且沒有任何參數。</span><span class="sxs-lookup"><span data-stu-id="4ea38-123">A public non-virtual (`NonInheritable` in Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation that has no parameters.</span></span>  
  
* <span data-ttu-id="4ea38-124">受保護的虛擬 (Visual Basic 中為 `Overridable`) `Dispose` 方法，其簽章為：</span><span class="sxs-lookup"><span data-stu-id="4ea38-124">A protected virtual (`Overridable` in Visual Basic) `Dispose` method whose signature is:</span></span>  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a><span data-ttu-id="4ea38-125">Dispose() 多載</span><span class="sxs-lookup"><span data-stu-id="4ea38-125">The Dispose() overload</span></span>

<span data-ttu-id="4ea38-126">由於這個公用、非虛擬 (在 Visual Basic 中為 `NonInheritable`)、無參數的 `Dispose` 方法是由類型消費者所呼叫，其用途是釋放 Unmanaged 資源並指出完成項 (如果有的話) 不需要執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-126">Because the public, non-virtual (`NonInheritable` in Visual Basic), parameterless `Dispose` method is called by a consumer of the type, its purpose is to free unmanaged resources and to indicate that the finalizer, if one is present, doesn't have to run.</span></span> <span data-ttu-id="4ea38-127">因此，它擁有標準實作：</span><span class="sxs-lookup"><span data-stu-id="4ea38-127">Because of this, it has a standard implementation:</span></span>  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
<span data-ttu-id="4ea38-128">`Dispose` 方法會執行所有物件清除，所以記憶體回收行程不需要再呼叫物件的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 覆寫。</span><span class="sxs-lookup"><span data-stu-id="4ea38-128">The `Dispose` method performs all object cleanup, so the garbage collector no longer needs to call the objects' <xref:System.Object.Finalize%2A?displayProperty=nameWithType> override.</span></span> <span data-ttu-id="4ea38-129">因此，呼叫 <xref:System.GC.SuppressFinalize%2A> 方法會防止記憶體回收行程執行完成項。</span><span class="sxs-lookup"><span data-stu-id="4ea38-129">Therefore, the call to the <xref:System.GC.SuppressFinalize%2A> method prevents the garbage collector from running the finalizer.</span></span> <span data-ttu-id="4ea38-130">如果類型沒有完成項，則呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 沒有作用。</span><span class="sxs-lookup"><span data-stu-id="4ea38-130">If the type has no finalizer, the call to <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> has no effect.</span></span> <span data-ttu-id="4ea38-131">請注意，實際釋放 Unmanaged 資源的工作是由 `Dispose` 方法的第二個多載執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-131">Note that the actual work of releasing unmanaged resources is performed by the second overload of the `Dispose` method.</span></span>  
  
### <a name="the-disposeboolean-overload"></a><span data-ttu-id="4ea38-132">Dispose(Boolean) 多載</span><span class="sxs-lookup"><span data-stu-id="4ea38-132">The Dispose(Boolean) overload</span></span>

<span data-ttu-id="4ea38-133">在第二個多載，*處置*參數是<xref:System.Boolean>，指出方法呼叫來自<xref:System.IDisposable.Dispose%2A>方法 (其值是`true`) 或是來自完成項 (其值是`false`)。</span><span class="sxs-lookup"><span data-stu-id="4ea38-133">In the second overload, the *disposing* parameter is a <xref:System.Boolean> that indicates whether the method call comes from a <xref:System.IDisposable.Dispose%2A> method (its value is `true`) or from a finalizer (its value is `false`).</span></span>  
  
<span data-ttu-id="4ea38-134">方法的主體是由兩個程式碼區塊所構成：</span><span class="sxs-lookup"><span data-stu-id="4ea38-134">The body of the method consists of two blocks of code:</span></span>  
  
* <span data-ttu-id="4ea38-135">釋放 Unmanaged 資源的區塊。</span><span class="sxs-lookup"><span data-stu-id="4ea38-135">A block that frees unmanaged resources.</span></span> <span data-ttu-id="4ea38-136">不論 `disposing` 參數的值為何，這個區塊都會執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-136">This block executes regardless of the value of the `disposing` parameter.</span></span>  
  
* <span data-ttu-id="4ea38-137">釋放 Managed 資源的條件性區塊。</span><span class="sxs-lookup"><span data-stu-id="4ea38-137">A conditional block that frees managed resources.</span></span> <span data-ttu-id="4ea38-138">如果 `disposing` 的值為 `true`，這個區塊就會執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-138">This block executes if the value of `disposing` is `true`.</span></span> <span data-ttu-id="4ea38-139">它所釋放的 Managed 資源可能包括：</span><span class="sxs-lookup"><span data-stu-id="4ea38-139">The managed resources that it frees can include:</span></span>  
  
  <span data-ttu-id="4ea38-140">**受管理物件，可實作<xref:System.IDisposable>。**</span><span class="sxs-lookup"><span data-stu-id="4ea38-140">**Managed objects that implement <xref:System.IDisposable>.**</span></span> <span data-ttu-id="4ea38-141">條件式區塊可以用來呼叫其 <xref:System.IDisposable.Dispose%2A> 實作。</span><span class="sxs-lookup"><span data-stu-id="4ea38-141">The conditional block can be used to call their <xref:System.IDisposable.Dispose%2A> implementation.</span></span> <span data-ttu-id="4ea38-142">如果您已使用安全控制代碼包裝 Unmanaged 資源，則應該在這裡呼叫 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="4ea38-142">If you have used a safe handle to wrap your unmanaged resource, you should call the <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementation here.</span></span>  
  
  <span data-ttu-id="4ea38-143">**耗用大量記憶體或耗用少量資源的 Managed 物件。**</span><span class="sxs-lookup"><span data-stu-id="4ea38-143">**Managed objects that consume large amounts of memory or consume scarce resources.**</span></span> <span data-ttu-id="4ea38-144">如果它們是之非由記憶體回收行程，在 `Dispose` 方法中明確釋放這些物件的速度，會比由記憶體回收行程以非決定性的方式回收來得快。</span><span class="sxs-lookup"><span data-stu-id="4ea38-144">Freeing these objects explicitly in the `Dispose` method releases them faster than if they were reclaimed non-deterministically by the garbage collector.</span></span>  
  
<span data-ttu-id="4ea38-145">如果方法呼叫來自完成項 (也就是如果 *disposing* 為 `false`)，則只會執行釋放 Unmanaged 資源的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-145">If the method call comes from a finalizer (that is, if *disposing* is `false`), only the code that frees unmanaged resources executes.</span></span> <span data-ttu-id="4ea38-146">由於記憶體回收行程在最終處理期間終結 Managed 物件的順序並未定義，使用 `Dispose` 值呼叫此 `false` 多載可防止完成項嘗試釋放可能已經回收的 Managed 資源。</span><span class="sxs-lookup"><span data-stu-id="4ea38-146">Because the order in which the garbage collector destroys managed objects during finalization is not defined, calling this `Dispose` overload with a value of `false` prevents the finalizer from trying to release managed resources that may have already been reclaimed.</span></span>  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a><span data-ttu-id="4ea38-147">實作基底類別的處置模式</span><span class="sxs-lookup"><span data-stu-id="4ea38-147">Implementing the dispose pattern for a base class</span></span>

<span data-ttu-id="4ea38-148">如果您實作基底類別的處置模式，則必須提供下列項目：</span><span class="sxs-lookup"><span data-stu-id="4ea38-148">If you implement the dispose pattern for a base class, you must provide the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4ea38-149">您應該針對實作 <xref:System.IDisposable.Dispose> 並且不是 `sealed` (在 Visual Basic 中為 `NotInheritable`) 的所有基底類別實作此模式。</span><span class="sxs-lookup"><span data-stu-id="4ea38-149">You should implement this pattern for all base classes that implement <xref:System.IDisposable.Dispose> and are not `sealed` (`NotInheritable` in Visual Basic).</span></span>  
  
* <span data-ttu-id="4ea38-150">呼叫 <xref:System.IDisposable.Dispose%2A> 方法的 `Dispose(Boolean)` 實作。</span><span class="sxs-lookup"><span data-stu-id="4ea38-150">A <xref:System.IDisposable.Dispose%2A> implementation that calls the `Dispose(Boolean)` method.</span></span>  
  
* <span data-ttu-id="4ea38-151">實際釋放資源的 `Dispose(Boolean)` 方法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-151">A `Dispose(Boolean)` method that performs the actual work of releasing resources.</span></span>  
  
* <span data-ttu-id="4ea38-152">衍生自包裝您的 Unmanaged 資源之 <xref:System.Runtime.InteropServices.SafeHandle> 的類別 (建議使用)，或式 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="4ea38-152">Either a class derived from <xref:System.Runtime.InteropServices.SafeHandle> that wraps your unmanaged resource (recommended), or an override to the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ea38-153"><xref:System.Runtime.InteropServices.SafeHandle> 類別會提供完成項，讓您不必自行撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-153">The <xref:System.Runtime.InteropServices.SafeHandle> class provides a finalizer that frees you from having to code one.</span></span>  
  
<span data-ttu-id="4ea38-154">以下一般模式將會實作使用安全控制代碼之基底類別的處置模式。</span><span class="sxs-lookup"><span data-stu-id="4ea38-154">Here's the general pattern for implementing the dispose pattern for a base class that uses a safe handle.</span></span>  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="4ea38-155">上一個範例使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件來說明模式；可改用任何衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-155">The previous example uses a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> object to illustrate the pattern; any object derived from <xref:System.Runtime.InteropServices.SafeHandle> could be used instead.</span></span> <span data-ttu-id="4ea38-156">請注意，該範例未正確地執行個體化其 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-156">Note that the example does not properly instantiate its <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> object.</span></span>  
  
<span data-ttu-id="4ea38-157">以下一般模式將會實作覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 之基底類別的處置模式。</span><span class="sxs-lookup"><span data-stu-id="4ea38-157">Here's the general pattern for implementing the dispose pattern for a base class that overrides <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.</span></span>  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> <span data-ttu-id="4ea38-158">在 C# 中，您會覆寫<xref:System.Object.Finalize%2A?displayProperty=nameWithType>藉由定義[解構函式](~/docs/csharp/programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="4ea38-158">In C#, you override <xref:System.Object.Finalize%2A?displayProperty=nameWithType> by defining a [destructor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a><span data-ttu-id="4ea38-159">實作衍生類別的處置模式</span><span class="sxs-lookup"><span data-stu-id="4ea38-159">Implementing the dispose pattern for a derived class</span></span>

<span data-ttu-id="4ea38-160">從實作 <xref:System.IDisposable> 介面的類別衍生的類別不應該實作 <xref:System.IDisposable>，因為 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 的基底類別實作會由其衍生類別繼承。</span><span class="sxs-lookup"><span data-stu-id="4ea38-160">A class derived from a class that implements the <xref:System.IDisposable> interface shouldn't implement <xref:System.IDisposable>, because the base class implementation of <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> is inherited by its derived classes.</span></span> <span data-ttu-id="4ea38-161">因此，若要實作衍生類別的處置模式，請改為提供下列項目：</span><span class="sxs-lookup"><span data-stu-id="4ea38-161">Instead, to implement the dispose pattern for a derived class, you provide the following:</span></span>  
  
* <span data-ttu-id="4ea38-162">覆寫基底類別方法及實際釋放衍生類別之資源的 `protected``Dispose(Boolean)` 方法。</span><span class="sxs-lookup"><span data-stu-id="4ea38-162">A `protected``Dispose(Boolean)` method that overrides the base class method and performs the actual work of releasing the resources of the derived class.</span></span> <span data-ttu-id="4ea38-163">這個方法也應該呼叫基底類別的 `Dispose(Boolean)` 方法，並且將 *disposing* 引數的 `true` 值傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="4ea38-163">This method should also call the `Dispose(Boolean)` method of the base class and pass it a value of `true` for the *disposing* argument.</span></span>  
  
* <span data-ttu-id="4ea38-164">衍生自包裝您的 Unmanaged 資源之 <xref:System.Runtime.InteropServices.SafeHandle> 的類別 (建議使用)，或式 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="4ea38-164">Either a class derived from <xref:System.Runtime.InteropServices.SafeHandle> that wraps your unmanaged resource (recommended), or an override to the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ea38-165"><xref:System.Runtime.InteropServices.SafeHandle> 類別會提供完成項，讓您不必自行撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-165">The <xref:System.Runtime.InteropServices.SafeHandle> class provides a finalizer that frees you from having to code one.</span></span> <span data-ttu-id="4ea38-166">如果您提供完成項，則它應該呼叫 `Dispose(Boolean)` 多載且 *disposing* 引數為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4ea38-166">If you do provide a finalizer, it should call the `Dispose(Boolean)` overload with a *disposing* argument of `false`.</span></span>  
  
<span data-ttu-id="4ea38-167">以下一般模式將會實作使用安全控制代碼之衍生類別的處置模式：</span><span class="sxs-lookup"><span data-stu-id="4ea38-167">Here's the general pattern for implementing the dispose pattern for a derived class that uses a safe handle:</span></span>  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="4ea38-168">上一個範例使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件來說明模式；可改用任何衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-168">The previous example uses a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> object to illustrate the pattern; any object derived from <xref:System.Runtime.InteropServices.SafeHandle> could be used instead.</span></span> <span data-ttu-id="4ea38-169">請注意，該範例未正確地執行個體化其 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-169">Note that the example does not properly instantiate its <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> object.</span></span>  
  
<span data-ttu-id="4ea38-170">以下一般模式將會實作覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 之衍生類別的處置模式：</span><span class="sxs-lookup"><span data-stu-id="4ea38-170">Here's the general pattern for implementing the dispose pattern for a derived class that overrides <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:</span></span>  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> <span data-ttu-id="4ea38-171">在 C# 中，您會覆寫<xref:System.Object.Finalize%2A?displayProperty=nameWithType>藉由定義[解構函式](~/docs/csharp/programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="4ea38-171">In C#, you override <xref:System.Object.Finalize%2A?displayProperty=nameWithType> by defining a [destructor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a><span data-ttu-id="4ea38-172">使用安全控制代碼</span><span class="sxs-lookup"><span data-stu-id="4ea38-172">Using safe handles</span></span>

<span data-ttu-id="4ea38-173">撰寫物件完成項的程式碼是一項複雜的工作，若未正確撰寫，可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="4ea38-173">Writing code for an object's finalizer is a complex task that can cause problems if not done correctly.</span></span> <span data-ttu-id="4ea38-174">因此，建議您建構 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 物件，而不要實作完成項。</span><span class="sxs-lookup"><span data-stu-id="4ea38-174">Therefore, we recommend that you construct <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> objects instead of implementing a finalizer.</span></span>  
  
<span data-ttu-id="4ea38-175">衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 類別的類別會在不受干擾的情況下，藉由指派和釋放控制代碼的方式簡化物件存留期的問題。</span><span class="sxs-lookup"><span data-stu-id="4ea38-175">Classes derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class simplify object lifetime issues by assigning and releasing handles without interruption.</span></span> <span data-ttu-id="4ea38-176">這些類別包含重要的完成項，該完成項保證會在應用程式定義域卸載時執行。</span><span class="sxs-lookup"><span data-stu-id="4ea38-176">They contain a critical finalizer that is guaranteed to run while an application domain is unloading.</span></span> <span data-ttu-id="4ea38-177">如需使用安全控制代碼之優點的詳細資訊，請參閱<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4ea38-177">For more information about the advantages of using a safe handle, see <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ea38-178"><xref:Microsoft.Win32.SafeHandles> 命名空間中的下列衍生類別會提供安全控制代碼：</span><span class="sxs-lookup"><span data-stu-id="4ea38-178">The following derived classes in the <xref:Microsoft.Win32.SafeHandles> namespace provide safe handles:</span></span>  
  
* <span data-ttu-id="4ea38-179"><xref:Microsoft.Win32.SafeHandles.SafeFileHandle>、<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> 和 <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> 類別，適用於檔案、記憶體對應檔案和管道。</span><span class="sxs-lookup"><span data-stu-id="4ea38-179">The <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, and <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> class, for files, memory mapped files, and pipes.</span></span>  
  
* <span data-ttu-id="4ea38-180"><xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 類別，適用於記憶體檢視。</span><span class="sxs-lookup"><span data-stu-id="4ea38-180">The <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> class, for memory views.</span></span>  
  
* <span data-ttu-id="4ea38-181"><xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>、<xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> 和 <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> 類別，適用於加密建構。</span><span class="sxs-lookup"><span data-stu-id="4ea38-181">The <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, and <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> classes, for cryptography constructs.</span></span>  
  
* <span data-ttu-id="4ea38-182"><xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> 類別，適用於登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-182">The <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> class, for registry keys.</span></span>  
  
* <span data-ttu-id="4ea38-183"><xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> 類別，適用於等候控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-183">The <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> class, for wait handles.</span></span>  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a><span data-ttu-id="4ea38-184">使用安全控制代碼實作基底類別的處置模式</span><span class="sxs-lookup"><span data-stu-id="4ea38-184">Using a safe handle to implement the dispose pattern for a base class</span></span>

<span data-ttu-id="4ea38-185">下列範例將說明使用安全控制代碼封裝 Unmanaged 資源之基底類別 `DisposableStreamResource` 的處置模式。</span><span class="sxs-lookup"><span data-stu-id="4ea38-185">The following example illustrates the dispose pattern for a base class, `DisposableStreamResource`, that uses a safe handle to encapsulate unmanaged resources.</span></span> <span data-ttu-id="4ea38-186">它會定義 `DisposableResource` 類別，該類別使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 包裝代表開啟檔案的 <xref:System.IO.Stream> 物件。</span><span class="sxs-lookup"><span data-stu-id="4ea38-186">It defines a `DisposableResource` class that uses a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> to wrap a <xref:System.IO.Stream> object that represents an open file.</span></span> <span data-ttu-id="4ea38-187">`DisposableResource` 方法還包含單一屬性 `Size`，該屬性會傳回檔案資料流中的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="4ea38-187">The `DisposableResource` method also includes a single property, `Size`, that returns the total number of bytes in the file stream.</span></span>  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a><span data-ttu-id="4ea38-188">使用安全控制代碼實作衍生類別的處置模式</span><span class="sxs-lookup"><span data-stu-id="4ea38-188">Using a safe handle to implement the dispose pattern for a derived class</span></span>

<span data-ttu-id="4ea38-189">下列範例將說明衍生類別 `DisposableStreamResource2` 的處置模式，該類別繼承自上述範例中顯示的 `DisposableStreamResource` 類別。</span><span class="sxs-lookup"><span data-stu-id="4ea38-189">The following example illustrates the dispose pattern for a derived class, `DisposableStreamResource2`, that inherits from the `DisposableStreamResource` class presented in the previous example.</span></span> <span data-ttu-id="4ea38-190">這個類別會加入額外的方法 `WriteFileInfo`，並使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件包裝可寫入檔案的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4ea38-190">The class adds an additional method, `WriteFileInfo`, and uses a <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> object to wrap the handle of the writable file.</span></span>  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="4ea38-191">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea38-191">See also</span></span>

<span data-ttu-id="4ea38-192"><xref:System.GC.SuppressFinalize%2A></span><span class="sxs-lookup"><span data-stu-id="4ea38-192"><xref:System.GC.SuppressFinalize%2A></span></span>   
<span data-ttu-id="4ea38-193"><xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="4ea38-193"><xref:System.IDisposable></span></span>   
<span data-ttu-id="4ea38-194"><xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4ea38-194"><xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType></span></span>   
<span data-ttu-id="4ea38-195"><xref:Microsoft.Win32.SafeHandles></span><span class="sxs-lookup"><span data-stu-id="4ea38-195"><xref:Microsoft.Win32.SafeHandles></span></span>   
<span data-ttu-id="4ea38-196"><xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4ea38-196"><xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType></span></span>   
<span data-ttu-id="4ea38-197"><xref:System.Object.Finalize%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4ea38-197"><xref:System.Object.Finalize%2A?displayProperty=nameWithType></span></span>   
<span data-ttu-id="4ea38-198">[如何： 定義和使用類別和結構 (C + + /CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli) </span><span class="sxs-lookup"><span data-stu-id="4ea38-198">[How to: Define and Consume Classes and Structs (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli) </span></span>  
[<span data-ttu-id="4ea38-199">處置模式</span><span class="sxs-lookup"><span data-stu-id="4ea38-199">Dispose Pattern</span></span>](../../../docs/standard/design-guidelines/dispose-pattern.md)
