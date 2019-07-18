---
title: 清除 Unmanaged 資源
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6be45a3d03d8cff580653260081a20d518448237
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662737"
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="9e2dc-102">清除 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="9e2dc-102">Cleaning Up Unmanaged Resources</span></span>

<span data-ttu-id="9e2dc-103">對於應用程式所建立的大部分物件而言，您都可以依賴 .NET 記憶體回收行程處理記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-103">For the majority of the objects that your app creates, you can rely on .NET's garbage collector to handle memory management.</span></span> <span data-ttu-id="9e2dc-104">但是，當您建立包含 Unmanaged 資源的物件時，必須在應用程式使用完這些資源後明確地釋放它們。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-104">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them in your app.</span></span> <span data-ttu-id="9e2dc-105">最常見的 Unmanaged 資源類型就是包裝作業系統資源的物件，例如檔案、視窗、網路連接或資料庫連接都屬於這類資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-105">The most common types of unmanaged resource are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="9e2dc-106">雖然記憶體回收行程能夠追蹤封裝 Unmanaged 資源的物件存留期，但是它並不知道如何釋放和清除 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-106">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>

<span data-ttu-id="9e2dc-107">如果您的類型使用 Unmanaged 資源，則應該執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9e2dc-107">If your types use unmanaged resources, you should do the following:</span></span>

- <span data-ttu-id="9e2dc-108">實作[處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-108">Implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md).</span></span> <span data-ttu-id="9e2dc-109">這樣會要求您提供 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作以便將 Unmanaged 資源進行決定性的釋放。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-109">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of  unmanaged resources.</span></span> <span data-ttu-id="9e2dc-110">類型的消費者會在不再需要物件與其使用的資源時呼叫 <xref:System.IDisposable.Dispose%2A>。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-110">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) is no longer needed.</span></span> <span data-ttu-id="9e2dc-111"><xref:System.IDisposable.Dispose%2A> 方法會立即釋放 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-111">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>

- <span data-ttu-id="9e2dc-112">提供的用途是在您的類型消費者忘記呼叫 <xref:System.IDisposable.Dispose%2A> 時釋放 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-112">Provide for your unmanaged resources to be released in the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>.</span></span> <span data-ttu-id="9e2dc-113">執行此作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="9e2dc-113">There are two ways to do this:</span></span>

  - <span data-ttu-id="9e2dc-114">使用安全控制代碼包裝您的 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-114">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="9e2dc-115">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-115">This is the recommended technique.</span></span> <span data-ttu-id="9e2dc-116">安全控制代碼衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 類別，並且包括穩固的 <xref:System.Object.Finalize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-116">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="9e2dc-117">當您使用安全控制代碼時，只要實作 <xref:System.IDisposable> 介面並且在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 實作中呼叫安全控制代碼的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法即可。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-117">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="9e2dc-118">如果未呼叫 <xref:System.IDisposable.Dispose%2A> 方法，記憶體回收行程會自動呼叫安全控制代碼的完成項。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-118">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

    <span data-ttu-id="9e2dc-119">-或-</span><span class="sxs-lookup"><span data-stu-id="9e2dc-119">—or—</span></span>

  - <span data-ttu-id="9e2dc-120">覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-120">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9e2dc-121">最終處理可在類型消費者未呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以決定性的方式處理 Unmanaged 資源時，進行非決定性的 Unmanaged 資源釋放。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-121">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="9e2dc-122">不過，由於物件最終處理可能是複雜且容易發生錯誤的作業，因此建議您使用安全控制代碼，而不要提供您自己的完成項。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-122">However, because object finalization can be a complex and error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>

<span data-ttu-id="9e2dc-123">這樣類型的消費者就可以直接呼叫您的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作來釋放 Unmanaged 資源所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-123">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="9e2dc-124">當您正確實作 <xref:System.IDisposable.Dispose%2A> 方法時，安全控制代碼的 <xref:System.Object.Finalize%2A> 方法或是自有的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法覆寫便會成為一種防護措施，可在未呼叫 <xref:System.IDisposable.Dispose%2A> 方法時清除資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-124">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9e2dc-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="9e2dc-125">In This Section</span></span>

<span data-ttu-id="9e2dc-126">[實作 Dispose 方法](../../../docs/standard/garbage-collection/implementing-dispose.md) - 描述如何實作[處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md)以便釋放非受控資源。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-126">[Implementing a Dispose Method](../../../docs/standard/garbage-collection/implementing-dispose.md) Describes how to implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) for releasing unmanaged resources.</span></span>

<span data-ttu-id="9e2dc-127">[使用實作 IDisposable 的物件](../../../docs/standard/garbage-collection/using-objects.md) - 描述型別取用者如何確保呼叫其 <xref:System.IDisposable.Dispose%2A> 實作。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-127">[Using Objects That Implement IDisposable](../../../docs/standard/garbage-collection/using-objects.md) Describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="9e2dc-128">建議您使用 C# `using` 陳述式或 Visual Basic `Using` 陳述式執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-128">We recommend using the C# `using` statement or the Visual Basic `Using` statement to do this.</span></span>

## <a name="reference"></a><span data-ttu-id="9e2dc-129">參考資料</span><span class="sxs-lookup"><span data-stu-id="9e2dc-129">Reference</span></span>

<xref:System.IDisposable?displayProperty=nameWithType>\
<span data-ttu-id="9e2dc-130">定義用於釋放 Unmanaged 資源的 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-130">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span>

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
<span data-ttu-id="9e2dc-131">提供的用途是在 <xref:System.IDisposable.Dispose%2A> 方法未釋放 Unmanaged 資源時，進行物件最終處理。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-131">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span>

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
<span data-ttu-id="9e2dc-132">隱藏最終處理。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-132">Suppresses finalization.</span></span> <span data-ttu-id="9e2dc-133">這個方法通常會從 `Dispose` 方法呼叫，以便防止執行完成項。</span><span class="sxs-lookup"><span data-stu-id="9e2dc-133">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span>
