---
title: 清除 Unmanaged 資源
description: 請參閱如何清除不是由 .NET 垃圾收集行程處理的非受控資源，例如檔案、windows、& 網路或資料庫連接。
ms.date: 05/13/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: 07a8d754f1fc2612ae53407fa1b12a1eab7e38f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599825"
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="7830e-103">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="7830e-103">Cleaning up unmanaged resources</span></span>

<span data-ttu-id="7830e-104">針對您的應用程式所建立的大部分物件，您可以依賴[.net 垃圾收集](index.md)行程來處理記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="7830e-104">For the majority of the objects that your app creates, you can rely on the [.NET garbage collector](index.md) to handle memory management.</span></span> <span data-ttu-id="7830e-105">不過，當您建立包含非受控資源的物件時，您必須在完成使用這些資源時明確地釋放它們。</span><span class="sxs-lookup"><span data-stu-id="7830e-105">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them.</span></span> <span data-ttu-id="7830e-106">最常見的非受控資源類型是包裝作業系統資源的物件，例如檔案、windows、網路連接或資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="7830e-106">The most common types of unmanaged resources are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="7830e-107">雖然記憶體回收行程能夠追蹤封裝 Unmanaged 資源的物件存留期，但是它並不知道如何釋放和清除 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-107">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>

<span data-ttu-id="7830e-108">如果您的類型使用 Unmanaged 資源，則應該執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7830e-108">If your types use unmanaged resources, you should do the following:</span></span>

- <span data-ttu-id="7830e-109">實作[處置模式](implementing-dispose.md)。</span><span class="sxs-lookup"><span data-stu-id="7830e-109">Implement the [dispose pattern](implementing-dispose.md).</span></span> <span data-ttu-id="7830e-110">這會要求您提供 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 可啟用具決定性版本之非受控資源的執行方式。</span><span class="sxs-lookup"><span data-stu-id="7830e-110">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of unmanaged resources.</span></span> <span data-ttu-id="7830e-111">當您不再 <xref:System.IDisposable.Dispose%2A> 需要物件（及其使用的資源）時，您的型別取用者會呼叫。</span><span class="sxs-lookup"><span data-stu-id="7830e-111">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) are no longer needed.</span></span> <span data-ttu-id="7830e-112"><xref:System.IDisposable.Dispose%2A> 方法會立即釋放 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-112">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>

- <span data-ttu-id="7830e-113">如果您的型別取用者忘記呼叫 <xref:System.IDisposable.Dispose%2A> ，請提供一種方式來釋放非受控資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-113">In the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>, provide a way for your unmanaged resources to be released.</span></span> <span data-ttu-id="7830e-114">作法有二：</span><span class="sxs-lookup"><span data-stu-id="7830e-114">There are two ways to do this:</span></span>

  - <span data-ttu-id="7830e-115">使用安全控制代碼包裝您的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-115">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="7830e-116">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="7830e-116">This is the recommended technique.</span></span> <span data-ttu-id="7830e-117">安全控制碼衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 抽象類別，並包含健全的 <xref:System.Object.Finalize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7830e-117">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> abstract class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="7830e-118">當您使用安全控制代碼時，只要實作 <xref:System.IDisposable> 介面並且在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 實作中呼叫安全控制代碼的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法即可。</span><span class="sxs-lookup"><span data-stu-id="7830e-118">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="7830e-119">如果未呼叫 <xref:System.IDisposable.Dispose%2A> 方法，記憶體回收行程會自動呼叫安全控制代碼的完成項。</span><span class="sxs-lookup"><span data-stu-id="7830e-119">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

    <span data-ttu-id="7830e-120">-**或**-</span><span class="sxs-lookup"><span data-stu-id="7830e-120">—**or**—</span></span>

  - <span data-ttu-id="7830e-121">覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7830e-121">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7830e-122">最終處理可在類型消費者未呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以決定性的方式處理 Unmanaged 資源時，進行非決定性的 Unmanaged 資源釋放。</span><span class="sxs-lookup"><span data-stu-id="7830e-122">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="7830e-123">藉由[覆](../../csharp/programming-guide/classes-and-structs/destructors.md)寫方法來定義完成項 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7830e-123">Define a [finalizer](../../csharp/programming-guide/classes-and-structs/destructors.md) by overriding the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span>

  > [!WARNING]
  > <span data-ttu-id="7830e-124">不過，因為物件結束可能是複雜且容易出錯的作業，所以建議您使用安全控制碼，而不要提供自己的完成項。</span><span class="sxs-lookup"><span data-stu-id="7830e-124">However, because object finalization can be a complex and an error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>

<span data-ttu-id="7830e-125">這樣類型的消費者就可以直接呼叫您的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作來釋放 Unmanaged 資源所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="7830e-125">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="7830e-126">當您正確實作 <xref:System.IDisposable.Dispose%2A> 方法時，安全控制代碼的 <xref:System.Object.Finalize%2A> 方法或是自有的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法覆寫便會成為一種防護措施，可在未呼叫 <xref:System.IDisposable.Dispose%2A> 方法時清除資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-126">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7830e-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="7830e-127">In this section</span></span>

<span data-ttu-id="7830e-128">[執行 dispose 方法](implementing-dispose.md)說明如何執行處置模式以釋放非受控資源。</span><span class="sxs-lookup"><span data-stu-id="7830e-128">[Implementing a Dispose method](implementing-dispose.md) describes how to implement the dispose pattern for releasing unmanaged resources.</span></span>

<span data-ttu-id="7830e-129">[使用執行 `IDisposable` 的物件](using-objects.md)描述類型的取用者如何確保其 <xref:System.IDisposable.Dispose%2A> 實作為呼叫。</span><span class="sxs-lookup"><span data-stu-id="7830e-129">[Using objects that implement `IDisposable`](using-objects.md) describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="7830e-130">我們建議使用 c # `using` （或 Visual Basic `Using` ）語句來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="7830e-130">We recommend using the C# `using` (or the Visual Basic `Using`) statement to do this.</span></span>

## <a name="reference"></a><span data-ttu-id="7830e-131">參考</span><span class="sxs-lookup"><span data-stu-id="7830e-131">Reference</span></span>

| <span data-ttu-id="7830e-132">類型/成員</span><span class="sxs-lookup"><span data-stu-id="7830e-132">Type / Member</span></span> | <span data-ttu-id="7830e-133">描述</span><span class="sxs-lookup"><span data-stu-id="7830e-133">Description</span></span> |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | <span data-ttu-id="7830e-134">定義用於釋放 Unmanaged 資源的 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7830e-134">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span> |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | <span data-ttu-id="7830e-135">提供的用途是在 <xref:System.IDisposable.Dispose%2A> 方法未釋放 Unmanaged 資源時，進行物件最終處理。</span><span class="sxs-lookup"><span data-stu-id="7830e-135">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span> |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | <span data-ttu-id="7830e-136">隱藏最終處理。</span><span class="sxs-lookup"><span data-stu-id="7830e-136">Suppresses finalization.</span></span> <span data-ttu-id="7830e-137">這個方法通常會從 `Dispose` 方法呼叫，以便防止執行完成項。</span><span class="sxs-lookup"><span data-stu-id="7830e-137">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span> |
