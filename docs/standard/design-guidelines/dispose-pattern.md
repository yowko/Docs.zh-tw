---
title: Dispose 模式
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: KrzysztofCwalina
ms.openlocfilehash: ee6e9898ae93e2e6628eadec150a3c9c05f5d9c5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147707"
---
# <a name="dispose-pattern"></a><span data-ttu-id="840a8-102">Dispose 模式</span><span class="sxs-lookup"><span data-stu-id="840a8-102">Dispose Pattern</span></span>
<span data-ttu-id="840a8-103">所有程式執行期間都取得一或多個系統資源，例如記憶體、 系統的控制代碼或資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="840a8-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="840a8-104">開發人員需要時務必謹慎使用這類系統的資源，因為它們必須在取得並使用後釋放。</span><span class="sxs-lookup"><span data-stu-id="840a8-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="840a8-105">CLR 會提供自動記憶體管理的支援。</span><span class="sxs-lookup"><span data-stu-id="840a8-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="840a8-106">受控記憶體 (使用 C# 運算子配置的記憶體`new`) 不需要明確釋放。</span><span class="sxs-lookup"><span data-stu-id="840a8-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="840a8-107">它會自動釋放記憶體回收行程 (GC)。</span><span class="sxs-lookup"><span data-stu-id="840a8-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="840a8-108">這可讓開發人員從繁瑣且更釋出記憶體的工作，並已針對.NET Framework 所提供前所未有的產能的主要原因之一。</span><span class="sxs-lookup"><span data-stu-id="840a8-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="840a8-109">不幸的是，受管理的記憶體只是許多類型的系統資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="840a8-110">除了受管理的記憶體資源仍然必須明確地釋放，並稱為 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="840a8-111">GC 已沒有特別設計來管理這類未受管理的資源，這表示負責管理 unmanaged 的資源存在於開發人員手。</span><span class="sxs-lookup"><span data-stu-id="840a8-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="840a8-112">CLR 提供一些協助中釋放 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="840a8-113"><xref:System.Object?displayProperty=nameWithType> 宣告虛擬方法<xref:System.Object.Finalize%2A>（也稱為 「 完成項 」） 的 gc 之前呼叫物件的記憶體由 GC 回收，且可以釋放 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="840a8-114">覆寫完成項的類型被指可完成的類型。</span><span class="sxs-lookup"><span data-stu-id="840a8-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="840a8-115">雖然在某些案例中清除作業有效完成項，它們會有兩個很大的缺點：</span><span class="sxs-lookup"><span data-stu-id="840a8-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="840a8-116">GC 會偵測到的物件可供回收時，會呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="840a8-117">這會發生於未定一段時間後不再需要資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="840a8-118">當開發人員無法，或想要釋放的資源和資源的完成項當發行的時間之間的延遲可能會在取得許多很少資源 （可以輕鬆地耗盡的資源） 的程式，或在無法接受資源可使用 （例如，大型的 unmanaged 的記憶體緩衝區） 中，將高成本的情況。</span><span class="sxs-lookup"><span data-stu-id="840a8-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="840a8-119">在 CLR 需要呼叫完成項，它必須延後收集物件的記憶體回收 （集合之間執行的完成項） 的捨入的下一步。</span><span class="sxs-lookup"><span data-stu-id="840a8-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="840a8-120">這表示，在物件的記憶體 （和所有物件，它是指） 將不會釋放段較長的時間。</span><span class="sxs-lookup"><span data-stu-id="840a8-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="840a8-121">因此，在完成項信賴憑證者可能不適合在許多情況下，當務必盡可能的情況下，快速回收 unmanaged 的資源，很少資源，在處理時，或在高度高效能在其中的案例中新增的 GC 額外負荷最終處理的是無法接受。</span><span class="sxs-lookup"><span data-stu-id="840a8-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="840a8-122">「 架構 」 提供<xref:System.IDisposable?displayProperty=nameWithType>應該為開發人員提供手動的方式來釋放 unmanaged 的資源，因為它們不需要實作的介面。</span><span class="sxs-lookup"><span data-stu-id="840a8-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="840a8-123">它也提供<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>方法，可以告訴 GC，物件已手動處置的不需要完成，在此情況下之前回收物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="840a8-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="840a8-124">型別都會實作`IDisposable`介面就是可處置的類型。</span><span class="sxs-lookup"><span data-stu-id="840a8-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="840a8-125">Dispose 模式要標準化的使用方式與實作完成項和`IDisposable`介面。</span><span class="sxs-lookup"><span data-stu-id="840a8-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="840a8-126">模式的主要動機是要減少的實作的複雜性<xref:System.Object.Finalize%2A>而<xref:System.IDisposable.Dispose%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="840a8-127">複雜度是源自方法共用 （差異會在本章稍後所述） 的部分而非全部的程式碼路徑的事實。</span><span class="sxs-lookup"><span data-stu-id="840a8-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="840a8-128">此外，有的發展的語言支援具決定性的資源管理相關的模式的一些項目歷程記錄的原因。</span><span class="sxs-lookup"><span data-stu-id="840a8-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="840a8-129">**✓ DO** 包含的可處置的類型執行個體的型別上實作基本的處置模式。</span><span class="sxs-lookup"><span data-stu-id="840a8-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="840a8-130">請參閱[基本的處置模式](#basic_pattern)區段，如需有關基本模式。</span><span class="sxs-lookup"><span data-stu-id="840a8-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="840a8-131">如果類型是負責其他可處置物件的存留期，開發人員需要想辦法太處置它們。</span><span class="sxs-lookup"><span data-stu-id="840a8-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="840a8-132">使用容器的`Dispose`方法是便利的方式，才能達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="840a8-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="840a8-133">**✓ DO** 實作基本的處置模式，並提供完成項型別上保留的資源需要明確地釋放沒有完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="840a8-134">比方說，您應該實作模式儲存未受管理的記憶體緩衝區的型別上。</span><span class="sxs-lookup"><span data-stu-id="840a8-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="840a8-135">[最終處理的型別](#finalizable_types)章節討論與實作完成項相關的指導方針。</span><span class="sxs-lookup"><span data-stu-id="840a8-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="840a8-136">**✓ CONSIDER** 實作基本的處置模式類別本身不保存 unmanaged 資源，或是可處置的物件但可能會有執行的子類型。</span><span class="sxs-lookup"><span data-stu-id="840a8-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="840a8-137">最佳的範例是<xref:System.IO.Stream?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="840a8-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="840a8-138">雖然很不保留任何資源的抽象基底類別，但大部分其子類別的執行，因為這個緣故，它會實作此模式。</span><span class="sxs-lookup"><span data-stu-id="840a8-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="840a8-139">基本的處置模式</span><span class="sxs-lookup"><span data-stu-id="840a8-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="840a8-140">模式的基本實作，包括實作`System.IDisposable`介面和宣告`Dispose(bool)`方法，會實作所有的資源清除邏輯，以在之間共用`Dispose`方法，並選擇性完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="840a8-141">下列範例示範基本模式的簡單實作：</span><span class="sxs-lookup"><span data-stu-id="840a8-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="840a8-142">布林值參數`disposing`表示方法從叫用`IDisposable.Dispose`實作或完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="840a8-143">`Dispose(bool)`實作應檢查參數，然後再存取其他參考物件 （例如，在上述範例中的資源欄位）。</span><span class="sxs-lookup"><span data-stu-id="840a8-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="840a8-144">從呼叫方法時，應該只能存取這類物件`IDisposable.Dispose`實作 (當`disposing`參數等於 true)。</span><span class="sxs-lookup"><span data-stu-id="840a8-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="840a8-145">如果方法會叫用完成項完成 (`disposing`為 false)，不應該存取其他物件。</span><span class="sxs-lookup"><span data-stu-id="840a8-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="840a8-146">原因是物件的完成，無法預期的順序，因此它們，或任何其相依性，可能會有已經結束。</span><span class="sxs-lookup"><span data-stu-id="840a8-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="840a8-147">此外，這一節適用於具有未實作 Dispose 模式的基底類別。</span><span class="sxs-lookup"><span data-stu-id="840a8-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="840a8-148">如果您繼承自的類別已實作的模式，只是覆寫`Dispose(bool)`方法，以提供其他資源的清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="840a8-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="840a8-149">**✓ DO** 宣告 `protected virtual void Dispose(bool disposing)` 來釋放 unmanaged 的資源相關的方法來集中管理所有邏輯。</span><span class="sxs-lookup"><span data-stu-id="840a8-149">**✓ DO** declare a `protected virtual void Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="840a8-150">在此方法中，應該進行所有的資源清除。</span><span class="sxs-lookup"><span data-stu-id="840a8-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="840a8-151">這兩個完成項呼叫的方法和`IDisposable.Dispose`方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="840a8-152">參數會是如果正在叫用完成項內，則為 false。</span><span class="sxs-lookup"><span data-stu-id="840a8-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="840a8-153">它應該用來確保任何最終處理期間執行的程式碼不會存取其他可完成的物件。</span><span class="sxs-lookup"><span data-stu-id="840a8-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="840a8-154">在下一節中詳述實作完成項的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="840a8-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="840a8-155">**✓ DO** 實作 `IDisposable` 介面只呼叫 `Dispose(true)` 後面 `GC.SuppressFinalize(this)`。</span><span class="sxs-lookup"><span data-stu-id="840a8-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="840a8-156">若要在呼叫`SuppressFinalize`才應該發生`Dispose(true)`順利執行。</span><span class="sxs-lookup"><span data-stu-id="840a8-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="840a8-157">**X DO NOT** 進行無參數 `Dispose` 虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="840a8-158">`Dispose(bool)`方法就是應該加以覆寫子類別。</span><span class="sxs-lookup"><span data-stu-id="840a8-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 <span data-ttu-id="840a8-159">**X DO NOT** 宣告的任何多載 `Dispose` 方法以外 `Dispose()` 和 `Dispose(bool)`。</span><span class="sxs-lookup"><span data-stu-id="840a8-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="840a8-160">`Dispose` 應視為協助編寫此模式，並防止困惑實作者、 使用者和編譯器的保留的字。</span><span class="sxs-lookup"><span data-stu-id="840a8-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="840a8-161">有些語言可能會選擇會自動在特定類型上實作此模式。</span><span class="sxs-lookup"><span data-stu-id="840a8-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="840a8-162">**✓ DO** 允許 `Dispose(bool)` 方法來呼叫一次以上。</span><span class="sxs-lookup"><span data-stu-id="840a8-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="840a8-163">方法可能會選擇第一個呼叫之後會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="840a8-163">The method might choose to do nothing after the first call.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="840a8-164">**X AVOID** 擲回例外狀況從 `Dispose(bool)` 重大其中包含處理序已損毀的情況下除外 （流失，不一致的共用的狀態等。）。</span><span class="sxs-lookup"><span data-stu-id="840a8-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="840a8-165">使用者會預期呼叫`Dispose`將不會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="840a8-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="840a8-166">如果`Dispose`可能會引發例外狀況，將不會執行進一步的 finally 區塊清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="840a8-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="840a8-167">若要解決這個問題，使用者必須將每次呼叫`Dispose`(在 finally 區塊 ！) 在 try 區塊中，這會導致非常複雜的清除作業處理常式。</span><span class="sxs-lookup"><span data-stu-id="840a8-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="840a8-168">如果執行`Dispose(bool disposing)`方法中，永遠不會擲回的例外狀況，如果處置為 false。</span><span class="sxs-lookup"><span data-stu-id="840a8-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="840a8-169">如果完成項內容中執行，如此一來會終止處理序。</span><span class="sxs-lookup"><span data-stu-id="840a8-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="840a8-170">**✓ DO** 擲回 <xref:System.ObjectDisposedException> 從已經過處置物件後，無法使用的任何成員。</span><span class="sxs-lookup"><span data-stu-id="840a8-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="840a8-171">**✓ CONSIDER** 提供方法 `Close()`，除了 `Dispose()`，如果關閉是標準區域中的術語。</span><span class="sxs-lookup"><span data-stu-id="840a8-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="840a8-172">這樣一來，時，請務必`Close`實作相同`Dispose`，並考慮實作`IDisposable.Dispose`方法明確。</span><span class="sxs-lookup"><span data-stu-id="840a8-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="840a8-173">最終處理的類型</span><span class="sxs-lookup"><span data-stu-id="840a8-173">Finalizable Types</span></span>  
 <span data-ttu-id="840a8-174">最終處理的型別會擴充基本的處置模式，藉由覆寫完成項，並提供最終處理程式碼路徑中的型別`Dispose(bool)`方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="840a8-175">主要是因為您不能假設系統的狀態 （通常是有效的） 在執行期間，很難正確地實作完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="840a8-176">下列指導方針應該列入仔細考量。</span><span class="sxs-lookup"><span data-stu-id="840a8-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="840a8-177">請注意，有些指導方針套用不只是為`Finalize`方法，但任何程式碼呼叫來自完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="840a8-178">在其基本 Dispose 模式預先定義的情況下，這表示內部執行的邏輯`Dispose(bool disposing)`當`disposing`參數為 false。</span><span class="sxs-lookup"><span data-stu-id="840a8-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="840a8-179">如果基底類別已經是最終處理，而且會實作基本的處置模式，您不應該覆寫`Finalize`一次。</span><span class="sxs-lookup"><span data-stu-id="840a8-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="840a8-180">您應該改為只覆寫`Dispose(bool)`方法，以提供其他資源的清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="840a8-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="840a8-181">下列程式碼會顯示可完成類型的範例：</span><span class="sxs-lookup"><span data-stu-id="840a8-181">The following code shows an example of a finalizable type:</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="840a8-182">**X AVOID** 進行最終處理的類型。</span><span class="sxs-lookup"><span data-stu-id="840a8-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="840a8-183">請仔細考慮的只要在其中您認為需要完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="840a8-184">沒有即時完成項，從效能和程式碼複雜度觀點來看的執行個體相關聯的成本。</span><span class="sxs-lookup"><span data-stu-id="840a8-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="840a8-185">偏好使用資源的包裝函式，例如<xref:System.Runtime.InteropServices.SafeHandle>封裝 unmanaged 的資源，可能的話，在此情況下完成項將不再需要因為包裝函式是負責它自己的資源清除。</span><span class="sxs-lookup"><span data-stu-id="840a8-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="840a8-186">**X DO NOT** 進行最終處理實值類型。</span><span class="sxs-lookup"><span data-stu-id="840a8-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="840a8-187">實際上只是參考型別取得完成由 CLR，因此任何嘗試對實值型別中的完成項將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="840a8-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="840a8-188">C# 和 c + + 編譯器強制執行此規則。</span><span class="sxs-lookup"><span data-stu-id="840a8-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="840a8-189">**✓ DO** 讓類型變成可最終處理，如果類型是負責釋放 unmanaged 的資源，但是沒有自己的完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="840a8-190">當實作完成項，只要呼叫`Dispose(false)`內的所有資源清除邏輯隨時隨地`Dispose(bool disposing)`方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 <span data-ttu-id="840a8-191">**✓ DO** 每個可進行最終處理的類型上實作基本的處置模式。</span><span class="sxs-lookup"><span data-stu-id="840a8-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="840a8-192">這可讓使用者類型的方法來明確地執行具決定性的清除作業的完成項是負責那些相同的資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="840a8-193">**X DO NOT** 存取在完成項程式碼路徑中，任何最終處理物件，因為有極大的風險，它們將已完成。</span><span class="sxs-lookup"><span data-stu-id="840a8-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="840a8-194">比方說，最終處理物件的另一個可完成物件 B 參考無法可靠地使用 B 中 A 的完成項，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="840a8-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="840a8-195">以隨機順序 （除了關鍵結束的弱式排序保證），會呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="840a8-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="840a8-196">此外，請注意，靜態變數中儲存的物件將會收集在特定時間點期間的應用程式定義域卸載或結束處理程序。</span><span class="sxs-lookup"><span data-stu-id="840a8-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="840a8-197">存取最終處理物件 （或呼叫靜態方法，可能會使用儲存在靜態變數的值） 是指靜態變數可能不安全的如果<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="840a8-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="840a8-198">**✓ DO** 請您 `Finalize` 受保護的方法。</span><span class="sxs-lookup"><span data-stu-id="840a8-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="840a8-199">C#、 c + + 和 VB.NET 開發人員不需要擔心這個問題，因為編譯器可以協助強制執行這項指導方針。</span><span class="sxs-lookup"><span data-stu-id="840a8-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="840a8-200">**X DO NOT** 讓例外狀況逸出與完成項邏輯，除了嚴重系統失敗。</span><span class="sxs-lookup"><span data-stu-id="840a8-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="840a8-201">如果來自完成項擲回例外狀況，CLR 就會關閉整個程序 （從.NET Framework 2.0 版)，防止其他完成項執行並以節制的方式將被釋放的資源。</span><span class="sxs-lookup"><span data-stu-id="840a8-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="840a8-202">**✓ CONSIDER** 建立和使用的重要變成可最終處理物件 (具有型別階層架構，其中包含的型別 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) 的情況下，在其中完成項絕對必須執行而且即使發生強制應用程式定義域卸載和執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="840a8-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="840a8-203">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="840a8-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="840a8-204">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="840a8-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840a8-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="840a8-205">See also</span></span>

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="840a8-206">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="840a8-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="840a8-207">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="840a8-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [<span data-ttu-id="840a8-208">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="840a8-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
