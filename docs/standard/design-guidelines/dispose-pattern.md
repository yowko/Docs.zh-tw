---
title: "Dispose 模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 86fef5b18ac2c1c1b1dfee385b726484191fe714
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="dispose-pattern"></a><span data-ttu-id="2b067-102">Dispose 模式</span><span class="sxs-lookup"><span data-stu-id="2b067-102">Dispose Pattern</span></span>
<span data-ttu-id="2b067-103">所有程式執行期間都取得一或多個系統資源，例如記憶體、 系統處理或資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="2b067-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="2b067-104">開發人員需要時請小心使用這類的系統資源，因為它們已取得並使用之後必須釋放它們。</span><span class="sxs-lookup"><span data-stu-id="2b067-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="2b067-105">CLR 會提供自動記憶體管理的支援。</span><span class="sxs-lookup"><span data-stu-id="2b067-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="2b067-106">Managed 記憶體 (使用 C# 運算子配置的記憶體`new`) 不需要明確釋放。</span><span class="sxs-lookup"><span data-stu-id="2b067-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="2b067-107">它會自動釋放記憶體回收行程 (GC)。</span><span class="sxs-lookup"><span data-stu-id="2b067-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="2b067-108">這可以讓開發人員從繁瑣且困難的工作，釋出記憶體，且已前所未有的產能，.NET Framework 所提供的主要原因之一。</span><span class="sxs-lookup"><span data-stu-id="2b067-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="2b067-109">不幸的是，受管理的記憶體只是許多類型的系統資源。</span><span class="sxs-lookup"><span data-stu-id="2b067-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="2b067-110">除了受管理的記憶體之外的資源仍必須明確釋放且稱為 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="2b067-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="2b067-111">GC 特別設計無法管理這類 unmanaged 的資源，這表示管理 unmanaged 的資源的責任在於開發人員提供的指針。</span><span class="sxs-lookup"><span data-stu-id="2b067-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="2b067-112">CLR 會提供一些幫助釋放 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="2b067-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="2b067-113"><xref:System.Object?displayProperty=nameWithType>宣告虛擬方法<xref:System.Object.Finalize%2A>（也稱為完成項） 的 gc 之前呼叫物件的記憶體回收 gc 並會覆寫來釋放 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="2b067-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="2b067-114">覆寫完成項的類型被指可最終處理的類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="2b067-115">雖然在某些案例中清除有效完成項，但它們是使用兩個很大的缺點：</span><span class="sxs-lookup"><span data-stu-id="2b067-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="2b067-116">GC 偵測到的物件可供回收時，會呼叫完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="2b067-117">這會發生在特定一段時間之後再也不需要有資源。</span><span class="sxs-lookup"><span data-stu-id="2b067-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="2b067-118">當開發人員無法或想要發行的資源和資源所完成項當發行的時間之間的延遲可能會在取得許多很少的資源 （可能會輕易地耗盡資源） 的程式或在無法接受資源有成本保持在使用 （例如大量 unmanaged 的記憶體緩衝區） 的情況。</span><span class="sxs-lookup"><span data-stu-id="2b067-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="2b067-119">當 CLR 需要呼叫完成項時，它必須延後的記憶體物件的集合 （集合之間執行完成項） 記憶體回收的捨入的下一步。</span><span class="sxs-lookup"><span data-stu-id="2b067-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="2b067-120">這表示的時間更長的時間將會釋放物件的記憶體 （和其參考的所有物件）。</span><span class="sxs-lookup"><span data-stu-id="2b067-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="2b067-121">因此，完成項上獨佔式信賴憑證者可能不適合在許多情況下，務必盡，回收 unmanaged 的資源，很少資源，在處理時或在高高效能的案例中加入的 GC 額外負荷最終處理的是無法接受。</span><span class="sxs-lookup"><span data-stu-id="2b067-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="2b067-122">架構提供<xref:System.IDisposable?displayProperty=nameWithType>應該要提供開發人員手動的方式來釋放 unmanaged 的資源，因為它們不需要實作的介面。</span><span class="sxs-lookup"><span data-stu-id="2b067-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="2b067-123">它也提供<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>可以得知在 GC 的方法物件已手動處置，因此不需要最終處理而失效，在此情況下之前回收物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2b067-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="2b067-124">型別都會實作`IDisposable`介面指可處置的類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="2b067-125">處置的模式是標準化的使用方式和實作完成項和`IDisposable`介面。</span><span class="sxs-lookup"><span data-stu-id="2b067-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="2b067-126">模式的主要動機是減少實作的複雜性<xref:System.Object.Finalize%2A>和<xref:System.IDisposable.Dispose%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="2b067-127">複雜度源自的方法有部份但並非所有的程式碼路徑 （在本章稍後描述其差異） 的事實。</span><span class="sxs-lookup"><span data-stu-id="2b067-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="2b067-128">此外，還有歷史原因相關的具決定性的資源管理語言支援的進化模式的某些項目。</span><span class="sxs-lookup"><span data-stu-id="2b067-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="2b067-129">**✓ 不要**包含的可處置的類型執行個體的型別上實作基本的處置模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="2b067-130">請參閱[基本的處置模式](#basic_pattern)如需詳細資訊，在基本模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="2b067-131">如果類型是負責其他可處置的物件的存留期，開發人員需要能夠太處置它們。</span><span class="sxs-lookup"><span data-stu-id="2b067-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="2b067-132">使用容器的`Dispose`方法是方便進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="2b067-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="2b067-133">**✓ 不要**實作基本的處置模式，並提供完成項型別上保留的資源需要明確地釋放沒有完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="2b067-134">例如，應該在儲存未受管理的記憶體緩衝區的型別上實作這個模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="2b067-135">[變成可最終處理的型別](#finalizable_types)章節討論與實作完成項相關的指導方針。</span><span class="sxs-lookup"><span data-stu-id="2b067-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="2b067-136">**✓ 考慮**實作基本的處置模式類別本身不保存 unmanaged 資源，或是可處置的物件但可能會有執行的子類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="2b067-137">是一個絕佳範例<xref:System.IO.Stream?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="2b067-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2b067-138">雖然它是不保留任何資源的抽象基底類別，它的子類別的大部分作業，並因此，它會實作此模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="2b067-139">基本的處置模式</span><span class="sxs-lookup"><span data-stu-id="2b067-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="2b067-140">實作模式的基本實作牽涉到`System.IDisposable`介面，以及將宣告`Dispose(bool)`方法，可實作之間共用的所有資源清除邏輯`Dispose`方法，並選擇性的完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="2b067-141">下列範例示範基本模式的簡單實作：</span><span class="sxs-lookup"><span data-stu-id="2b067-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2b067-142">布林值參數`disposing`指出方法已從叫用`IDisposable.Dispose`實作或完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="2b067-143">`Dispose(bool)`實作應檢查參數，才能存取其他參考的物件 （例如，在上述範例中的資源欄位）。</span><span class="sxs-lookup"><span data-stu-id="2b067-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="2b067-144">呼叫此方法時，應該只能存取這類物件`IDisposable.Dispose`實作 (當`disposing`參數等於 true)。</span><span class="sxs-lookup"><span data-stu-id="2b067-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="2b067-145">如果方法叫用完成項 (`disposing`為 false)，不應該存取其他物件。</span><span class="sxs-lookup"><span data-stu-id="2b067-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="2b067-146">原因是物件的無法預期的順序完成，因此它們，或其任何相依性，可能會有已完成。</span><span class="sxs-lookup"><span data-stu-id="2b067-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="2b067-147">此外，本章節適用於具有未實作 Dispose 模式的基底類別。</span><span class="sxs-lookup"><span data-stu-id="2b067-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="2b067-148">如果您繼承自的類別已實作的模式，只是覆寫`Dispose(bool)`方法以提供額外的資源將清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="2b067-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="2b067-149">**✓ 不要**宣告受保護的虛擬 void`Dispose(bool disposing)`來釋放 unmanaged 的資源相關的方法來集中管理所有邏輯。</span><span class="sxs-lookup"><span data-stu-id="2b067-149">**✓ DO** declare a protected virtual void `Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="2b067-150">所有資源清除應都發生在這個方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="2b067-151">方法呼叫來自完成項和`IDisposable.Dispose`方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="2b067-152">參數會是如果正在從叫用完成項內則為 false。</span><span class="sxs-lookup"><span data-stu-id="2b067-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="2b067-153">它應該用於確保在最終處理期間執行的任何程式碼不會存取其他最終處理物件。</span><span class="sxs-lookup"><span data-stu-id="2b067-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="2b067-154">下一節會說明實作完成項的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2b067-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="2b067-155">**✓ 不要**實作`IDisposable`介面只呼叫`Dispose(true)`後面`GC.SuppressFinalize(this)`。</span><span class="sxs-lookup"><span data-stu-id="2b067-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="2b067-156">若要呼叫`SuppressFinalize`才應該發生`Dispose(true)`順利執行。</span><span class="sxs-lookup"><span data-stu-id="2b067-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="2b067-157">**X 不**進行無參數`Dispose`虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="2b067-158">`Dispose(bool)`方法是由子類別應該覆寫。</span><span class="sxs-lookup"><span data-stu-id="2b067-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 <span data-ttu-id="2b067-159">**X 不**宣告的任何多載`Dispose`方法以外`Dispose()`和`Dispose(bool)`。</span><span class="sxs-lookup"><span data-stu-id="2b067-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="2b067-160">`Dispose`應視為協助編訂此模式並防止混淆實作者、 使用者和編譯器之間的保留的字。</span><span class="sxs-lookup"><span data-stu-id="2b067-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="2b067-161">某些語言可能會選擇自動在特定類型上實作此模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="2b067-162">**✓ 不要**允許`Dispose(bool)`方法來呼叫一次以上。</span><span class="sxs-lookup"><span data-stu-id="2b067-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="2b067-163">此方法可能會選擇不執行任何動作後第一次呼叫。</span><span class="sxs-lookup"><span data-stu-id="2b067-163">The method might choose to do nothing after the first call.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="2b067-164">**避免 x**擲回例外狀況從`Dispose(bool)`重大其中包含處理序已損毀的情況下除外 （流失，不一致的共用的狀態等。）。</span><span class="sxs-lookup"><span data-stu-id="2b067-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="2b067-165">使用者可預期的呼叫`Dispose`將不會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b067-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="2b067-166">如果`Dispose`可能會引發例外狀況，將不會執行進一步的 finally 區塊清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="2b067-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="2b067-167">若要解決這個問題，使用者必須換行的每個呼叫`Dispose`(內 finally 區塊 ！) 在 try 區塊中，這會導致非常複雜的清除的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2b067-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="2b067-168">如果執行`Dispose(bool disposing)`方法時，永遠不會擲回的例外狀況，如果正在處置為 false。</span><span class="sxs-lookup"><span data-stu-id="2b067-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="2b067-169">若一個完成項內容中執行，如此一來會終止處理程序。</span><span class="sxs-lookup"><span data-stu-id="2b067-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="2b067-170">**✓ 不要**擲回<xref:System.ObjectDisposedException>從已經過處置物件後，無法使用的任何成員。</span><span class="sxs-lookup"><span data-stu-id="2b067-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="2b067-171">**✓ 考慮**提供方法`Close()`，除了`Dispose()`，如果關閉是標準區域中的術語。</span><span class="sxs-lookup"><span data-stu-id="2b067-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="2b067-172">這樣做，它時，請務必`Close`實作相同`Dispose`並考慮實作`IDisposable.Dispose`方法明確。</span><span class="sxs-lookup"><span data-stu-id="2b067-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="2b067-173">可進行最終處理的類型</span><span class="sxs-lookup"><span data-stu-id="2b067-173">Finalizable Types</span></span>  
 <span data-ttu-id="2b067-174">可進行最終處理的類型都是擴充基本的處置模式，藉由覆寫完成項，並提供結束程式碼路徑中的類型`Dispose(bool)`方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="2b067-175">完成項是簡單難以正確地實作，主要是因為您無法在執行期間進行系統的狀態 （通常是有效的） 假設。</span><span class="sxs-lookup"><span data-stu-id="2b067-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="2b067-176">下列指導方針應該應該謹慎考量。</span><span class="sxs-lookup"><span data-stu-id="2b067-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="2b067-177">請注意，有些指導方針套用無法只供`Finalize`方法，但任何程式碼呼叫來自完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="2b067-178">如果基本處置先前所定義的模式，這一點表示內部執行的邏輯`Dispose(bool disposing)`時`disposing`參數為 false。</span><span class="sxs-lookup"><span data-stu-id="2b067-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="2b067-179">如果基底類別已是可進行最終處理，並實作基本的處置模式，您不應覆寫`Finalize`一次。</span><span class="sxs-lookup"><span data-stu-id="2b067-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="2b067-180">您應該改為只覆寫`Dispose(bool)`方法以提供額外的資源將清除邏輯。</span><span class="sxs-lookup"><span data-stu-id="2b067-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="2b067-181">下列程式碼會顯示可完成類型的範例：</span><span class="sxs-lookup"><span data-stu-id="2b067-181">The following code shows an example of a finalizable type:</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="2b067-182">**請避免 x**進行最終處理的類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="2b067-183">請仔細考慮任何案例中您將需要完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="2b067-184">沒有實際具有完成項，從效能和程式碼複雜度觀點來看的執行個體相關聯的成本。</span><span class="sxs-lookup"><span data-stu-id="2b067-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="2b067-185">偏好使用資源的包裝函式，例如<xref:System.Runtime.InteropServices.SafeHandle>封裝 unmanaged 的資源，可能的話，在此情況下完成項會變成不需要因為包裝函式是負責其自己的資源清除。</span><span class="sxs-lookup"><span data-stu-id="2b067-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="2b067-186">**X 不**進行最終處理實值類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="2b067-187">實際上只是參考型別取得完成 clr，並因此將略過任何嘗試完成項置於實值類型。</span><span class="sxs-lookup"><span data-stu-id="2b067-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="2b067-188">C# 和 c + + 編譯器強制執行此規則。</span><span class="sxs-lookup"><span data-stu-id="2b067-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="2b067-189">**✓ 不要**讓類型變成可最終處理，如果類型是負責釋放 unmanaged 的資源，但是沒有自己的完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="2b067-190">當實作完成項時，只需呼叫`Dispose(false)`，並將內的所有資源清除邏輯`Dispose(bool disposing)`方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="2b067-191">**✓ 不要**每個可進行最終處理的類型上實作基本的處置模式。</span><span class="sxs-lookup"><span data-stu-id="2b067-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="2b067-192">這可讓使用者類型的方法來明確地執行完成項是負責這些相同資源的具決定性的清除。</span><span class="sxs-lookup"><span data-stu-id="2b067-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="2b067-193">**X 不**存取在完成項程式碼路徑中，任何最終處理物件，因為有極大的風險，它們將已完成。</span><span class="sxs-lookup"><span data-stu-id="2b067-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="2b067-194">例如，參考到另一個可進行最終處理物件 B 變成可最終處理物件 A 無法可靠地使用 B 中 A 的完成項，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="2b067-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="2b067-195">完成項 （不重要的最終處理的弱式排序保證） 以隨機順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="2b067-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="2b067-196">此外，請注意，以靜態變數儲存的物件會取得收集特定時間點期間的應用程式定義域卸載或結束程序。</span><span class="sxs-lookup"><span data-stu-id="2b067-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="2b067-197">存取是指可最終處理物件 （或呼叫靜態方法，可能會使用靜態變數中儲存的值） 的靜態變數可能不安全的如果<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>傳回 true。</span><span class="sxs-lookup"><span data-stu-id="2b067-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="2b067-198">**✓ 不要**請您`Finalize`受保護的方法。</span><span class="sxs-lookup"><span data-stu-id="2b067-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="2b067-199">C#、 c + + 和 VB.NET 開發人員不需要擔心，因為編譯器有助於強制執行這項指導方針。</span><span class="sxs-lookup"><span data-stu-id="2b067-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="2b067-200">**X 不**讓例外狀況逸出與完成項邏輯，除了嚴重系統失敗。</span><span class="sxs-lookup"><span data-stu-id="2b067-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="2b067-201">如果來自完成項擲回例外狀況，CLR 會關閉 (as of.NET Framework 2.0 版)，整個程序防止執行並以節制的方式將被釋放資源的其他完成項。</span><span class="sxs-lookup"><span data-stu-id="2b067-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="2b067-202">**✓ 考慮**建立和使用的重要變成可最終處理物件 (具有型別階層架構，其中包含的型別<xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) 的情況下，在其中完成項絕對必須執行而且即使發生強制應用程式定義域卸載和執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="2b067-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="2b067-203">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="2b067-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2b067-204">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="2b067-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b067-205">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b067-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2b067-206">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="2b067-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="2b067-207">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="2b067-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="2b067-208">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="2b067-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
