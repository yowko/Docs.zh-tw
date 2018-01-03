---
title: "處理和擲回例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 82e314dacc9fb2657a3a7088a928b59d00282a5d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="7ef01-102">在 .NET 中處理和擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="7ef01-103">應用程式必須能以一致的方式處理執行期間發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ef01-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="7ef01-104">.NET 提供模型，可以統一的方式通知應用程式的錯誤：.NET 作業會藉由擲回例外狀況指出失敗。</span><span class="sxs-lookup"><span data-stu-id="7ef01-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="7ef01-105">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-105">Exceptions</span></span>

<span data-ttu-id="7ef01-106">例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="7ef01-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="7ef01-107">若是程式碼或您呼叫的程式碼 (例如共用程式庫) 中有錯誤、無法使用作業系統資源、執行階段遇到非預期的狀況 (例如無法驗證的程式碼) 等等，就可能擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ef01-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that cannot be verified), and so on.</span></span> <span data-ttu-id="7ef01-108">您的應用程式可從一些狀況中復原，但有些狀況就無法復原。</span><span class="sxs-lookup"><span data-stu-id="7ef01-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="7ef01-109">雖然您可以從應用程式的大部分例外狀況中復原，但卻無法從執行階段的大部分例外狀況中復原。</span><span class="sxs-lookup"><span data-stu-id="7ef01-109">Although you can recover from most application exceptions, you cannot recover from most runtime exceptions.</span></span>

<span data-ttu-id="7ef01-110">在 .NET 中，例外狀況是繼承自 <xref:System.Exception?displayProperty=nameWithType> 類別的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef01-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7ef01-111">從發生問題的程式碼區域擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ef01-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="7ef01-112">例外狀況會向上傳遞堆疊，直到應用程式處理或程式終止它。</span><span class="sxs-lookup"><span data-stu-id="7ef01-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="7ef01-113">例外狀況與傳統錯誤處理方法的比較</span><span class="sxs-lookup"><span data-stu-id="7ef01-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="7ef01-114">傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。</span><span class="sxs-lookup"><span data-stu-id="7ef01-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="7ef01-115">.NET 實作例外狀況處理的方式具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="7ef01-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="7ef01-116">.NET 程式語言擲回和處理例外狀況的方式都相同。</span><span class="sxs-lookup"><span data-stu-id="7ef01-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="7ef01-117">要處理例外狀況不需要任何特定語言的語法，但可讓每一種語言定義自己的語法。</span><span class="sxs-lookup"><span data-stu-id="7ef01-117">Does not require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="7ef01-118">例外狀況可跨處理序，甚至是跨電腦界限擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="7ef01-119">可將例外狀況處理程式碼加入應用程式，以增加程式可靠性。</span><span class="sxs-lookup"><span data-stu-id="7ef01-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="7ef01-120">例外狀況優於其他錯誤通知方法，例如傳回碼。</span><span class="sxs-lookup"><span data-stu-id="7ef01-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="7ef01-121">不會發生未通知失敗的情況，因為如果擲回例外狀況而您未加以處理，執行階段就會終止您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ef01-121">Failures do not go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="7ef01-122">也不會因為程式碼無法檢查失敗傳回碼，就繼續在整個系統散佈無效的值。</span><span class="sxs-lookup"><span data-stu-id="7ef01-122">Invalid values do not continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span> 

## <a name="common-exceptions"></a><span data-ttu-id="7ef01-123">常見的例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-123">Common Exceptions</span></span>

<span data-ttu-id="7ef01-124">下表列出一些常見的例外狀況，並提供可能造成這些例外狀況的原因範例。</span><span class="sxs-lookup"><span data-stu-id="7ef01-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="7ef01-125">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="7ef01-125">Exception type</span></span> | <span data-ttu-id="7ef01-126">基底類型</span><span class="sxs-lookup"><span data-stu-id="7ef01-126">Base type</span></span> | <span data-ttu-id="7ef01-127">描述</span><span class="sxs-lookup"><span data-stu-id="7ef01-127">Description</span></span> | <span data-ttu-id="7ef01-128">範例</span><span class="sxs-lookup"><span data-stu-id="7ef01-128">Example</span></span> |
| -------------- | --------- | ----------- | ------- |
| <xref:System.Exception> | <xref:System.Object> | <span data-ttu-id="7ef01-129">適用於所有例外狀況的基底類別。</span><span class="sxs-lookup"><span data-stu-id="7ef01-129">Base class for all exceptions.</span></span> | <span data-ttu-id="7ef01-130">無 (使用這個例外狀況的衍生類別)。</span><span class="sxs-lookup"><span data-stu-id="7ef01-130">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="7ef01-131">只有當陣列索引不正確時，才由執行階段擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-131">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="7ef01-132">在有效的陣列範圍之外編製陣列索引：`arr[arr.Length+1]`</span><span class="sxs-lookup"><span data-stu-id="7ef01-132">Indexing an array outside its valid range: `arr[arr.Length+1]`</span></span> |
| <xref:System.NullReferenceException> | <xref:System.Exception> | <span data-ttu-id="7ef01-133">只有當參考 Null 物件時，才由執行階段擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-133">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null; o.ToString();` |
| <xref:System.InvalidOperationException> | <xref:System.Exception> | <span data-ttu-id="7ef01-134">當處於無效狀態時，由方法擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-134">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="7ef01-135">在從基礎集合將 Item 移除之後，呼叫 `Enumerator.GetNext()`。</span><span class="sxs-lookup"><span data-stu-id="7ef01-135">Calling `Enumerator.GetNext()` after removing an Item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <xref:System.Exception> | <span data-ttu-id="7ef01-136">適用於所有引數例外狀況的基底類別。</span><span class="sxs-lookup"><span data-stu-id="7ef01-136">Base class for all argument exceptions.</span></span> | <span data-ttu-id="7ef01-137">無 (使用這個例外狀況的衍生類別)。</span><span class="sxs-lookup"><span data-stu-id="7ef01-137">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <xref:System.Exception> | <span data-ttu-id="7ef01-138">由不允許引數為 Null 的方法擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-138">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null; "Calculate".IndexOf (s);` |
| <xref:System.ArgumentOutOfRangeException> | <xref:System.Exception> | <span data-ttu-id="7ef01-139">由驗證引數是在指定範圍內的方法擲回。</span><span class="sxs-lookup"><span data-stu-id="7ef01-139">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="7ef01-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef01-140">See Also</span></span>

* [<span data-ttu-id="7ef01-141">例外狀況類別和屬性</span><span class="sxs-lookup"><span data-stu-id="7ef01-141">Exception Class and Properties</span></span>](exception-class-and-properties.md)
* [<span data-ttu-id="7ef01-142">操作說明：使用 Try/Catch 區塊攔截例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-142">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [<span data-ttu-id="7ef01-143">操作說明：使用 Catch 區塊中的特定例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-143">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
* [<span data-ttu-id="7ef01-144">操作說明：明確擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-144">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
* [<span data-ttu-id="7ef01-145">操作說明：建立使用者定義的例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-145">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
* [<span data-ttu-id="7ef01-146">使用使用者篩選的例外狀況處理常式</span><span class="sxs-lookup"><span data-stu-id="7ef01-146">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
* [<span data-ttu-id="7ef01-147">操作說明：使用 Finally 區塊</span><span class="sxs-lookup"><span data-stu-id="7ef01-147">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
* [<span data-ttu-id="7ef01-148">處理 COM Interop 例外狀況</span><span class="sxs-lookup"><span data-stu-id="7ef01-148">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
* [<span data-ttu-id="7ef01-149">例外狀況的最佳做法</span><span class="sxs-lookup"><span data-stu-id="7ef01-149">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)

<span data-ttu-id="7ef01-150">若要深入了解 .NET 中例外狀況的運作方式，請參閱 [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef01-150">To learn more about how exceptions work in .NET, see [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
