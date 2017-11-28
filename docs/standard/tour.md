---
title: ".NET 教學課程"
description: ".NET 某些重要功能的逐步導覽。"
keywords: ".NET, .NET Core, 教學課程, 程式設計語言, 不安全, 記憶體管理, 型別安全, 非同步處理"
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 809f0eaddf298b0d6a57e217c2bcf5450675c3e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="tour-of-net"></a><span data-ttu-id="9aa0c-104">.NET 教學課程</span><span class="sxs-lookup"><span data-stu-id="9aa0c-104">Tour of .NET</span></span>

<span data-ttu-id="9aa0c-105">.NET 是一般用途開發平台。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-105">.NET is a general purpose development platform.</span></span> <span data-ttu-id="9aa0c-106">它有數種重要功能，例如支援多種程式設計語言、非同步和並行程式設計模型，以及原生互通性，可支援跨多重平台的眾多案例。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-106">It has several key features, such as support for multiple programming languages, asynchronous and concurrent programming models, and native interoperability, which enable a wide range of scenarios across multiple platforms.</span></span>

<span data-ttu-id="9aa0c-107">本文提供 .NET 某些重要功能的逐步導覽。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-107">This article offers a guided tour through some of the key features of the .NET.</span></span> <span data-ttu-id="9aa0c-108">請參閱 [.NET 架構元件](components.md)主題以了解 .NET 的架構片段，以及其用途。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-108">See the [.NET Architectural Components](components.md) topic to learn about the architectural pieces of .NET and what they're used for.</span></span>

## <a name="how-to-run-the-code-samples"></a><span data-ttu-id="9aa0c-109">如何執行程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9aa0c-109">How to run the code samples</span></span>

<span data-ttu-id="9aa0c-110">若要了解如何設定開發環境以執行程式碼範例，請參閱[入門](get-started.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-110">To learn how to set up a development environment to run the code samples, see the [Getting Started](get-started.md) topic.</span></span> <span data-ttu-id="9aa0c-111">請從此頁面將程式碼複製並貼入您的環境中來執行它們。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-111">Copy and paste code samples from this page into your environment to execute them.</span></span> 

## <a name="programming-languages"></a><span data-ttu-id="9aa0c-112">程式語言</span><span class="sxs-lookup"><span data-stu-id="9aa0c-112">Programming languages</span></span>

<span data-ttu-id="9aa0c-113">.NET 支援多種程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-113">.NET supports multiple programming languages.</span></span> <span data-ttu-id="9aa0c-114">.NET 實作會實作[通用語言基礎結構 (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/)，它的其中一個功能是指定與語言無關的執行階段和語言互通性。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-114">The .NET implementations implement the [Common Language Infrastructure (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/), which among other things specifies a language-independent runtime and language interoperability.</span></span> <span data-ttu-id="9aa0c-115">這表示您可以選擇任何 .NET 語言，在 .NET 上建置應用程式與服務。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-115">This means that you choose any .NET language to build apps and services on .NET.</span></span>

<span data-ttu-id="9aa0c-116">Microsoft 積極地開發並支援三種 .NET 語言：C#、F# 與 Visual Basic (VB)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-116">Microsoft actively develops and supports three .NET languages: C#, F#, and Visual Basic (VB).</span></span> 

* <span data-ttu-id="9aa0c-117">C# 既簡單、強大、型別安全且為物件導向，同時保留 C 樣式語言的易讀性與簡潔性。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-117">C# is simple, powerful, type-safe, and object-oriented, while retaining the expressiveness and elegance of C-style languages.</span></span> <span data-ttu-id="9aa0c-118">熟悉 C 和類似語言的任何人在適應 C# 方面很少有問題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-118">Anyone familiar with C and similar languages finds few problems in adapting to C#.</span></span> <span data-ttu-id="9aa0c-119">若要深入了解 C#，請參閱 [C# 指南](../csharp/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-119">Check out the [C# Guide](../csharp/index.md) to learn more about C#.</span></span>

* <span data-ttu-id="9aa0c-120">F# 是跨平台、功能優先的程式語言，也支援傳統物件導向和命令式程式設計。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-120">F# is a cross-platform, functional-first programming language that also supports traditional object-oriented and imperative programming.</span></span> <span data-ttu-id="9aa0c-121">若要深入了解 F#，請參閱 [F# 指南](../fsharp/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-121">Check out the [F# Guide](../fsharp/index.md) to learn more about F#.</span></span>

* <span data-ttu-id="9aa0c-122">Visual Basic 是容易學習的語言，您可以使用該語言建置 .NET 上所執行的各種應用程式。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-122">Visual Basic is an easy language to learn that you use to build a variety of apps that run on .NET.</span></span> <span data-ttu-id="9aa0c-123">在所有的 .NET 語言中，VB 的語法最接近一般人類語言，因此通常可讓新手更輕鬆地開發軟體。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-123">Among the .NET languages, the syntax of VB is the closest to ordinary human language, often making it easier for people new to software development.</span></span>

## <a name="automatic-memory-management"></a><span data-ttu-id="9aa0c-124">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="9aa0c-124">Automatic memory management</span></span>

<span data-ttu-id="9aa0c-125">.NET 使用[記憶體回收 (GC)](garbagecollection/index.md) 為程式提供自動記憶體管理。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-125">.NET uses [garbage collection (GC)](garbagecollection/index.md) to provide automatic memory management for programs.</span></span> <span data-ttu-id="9aa0c-126">GC 採用延遲方法來管理記憶體，優先考慮應用程式輸送量，而不是立即收集記憶體。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-126">The GC operates on a lazy approach to memory management, preferring app throughput to the immediate collection of memory.</span></span> <span data-ttu-id="9aa0c-127">若要深入了解 .NET GC，請參閱[記憶體回收 (GC) 的基本概念](garbagecollection/fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-127">To learn more about the .NET GC, check out [Fundamentals of garbage collection (GC)](garbagecollection/fundamentals.md).</span></span>

<span data-ttu-id="9aa0c-128">下列兩行會配置記憶體：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-128">The following two lines both allocate memory:</span></span>

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

<span data-ttu-id="9aa0c-129">沒有類似的關鍵字可取消配置記憶體，因為當記憶體回收行程透過其排程執行回收記憶體時，就會自動取消配置。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-129">There's no analogous keyword to de-allocate memory, as de-allocation happens automatically when the garbage collector reclaims the memory through its scheduled run.</span></span>

<span data-ttu-id="9aa0c-130">記憶體回收行程是服務之一，可確保*記憶體安全*。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-130">The garbage collector is one of the services that help ensure *memory safety*.</span></span> <span data-ttu-id="9aa0c-131">如果程式只存取已配置的記憶體，就是記憶體安全。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-131">A program is memory safe if it accesses only allocated memory.</span></span> <span data-ttu-id="9aa0c-132">例如，執行階段可確保應用程式不會存取陣列界限外已取消配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-132">For instance, the runtime ensures that an app doesn't access unallocated memory beyond the bounds of an array.</span></span>

<span data-ttu-id="9aa0c-133">在下列範例中，執行階段會擲回 `InvalidIndexException` 例外狀況來確保記憶體安全：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-133">In the following example, the runtime throws an `InvalidIndexException` exception to enforce memory safety:</span></span>

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a><span data-ttu-id="9aa0c-134">使用 Unmanaged 資源</span><span class="sxs-lookup"><span data-stu-id="9aa0c-134">Working with unmanaged resources</span></span>

<span data-ttu-id="9aa0c-135">有一些物件會參考 *Unmanaged 資源*。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-135">Some objects reference *unmanaged resources*.</span></span> <span data-ttu-id="9aa0c-136">Unmanaged 資源是指 .NET 執行階段不會自動維護的資源。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-136">Unmanaged resources are resources that aren't automatically maintained by the .NET runtime.</span></span> <span data-ttu-id="9aa0c-137">例如檔案控制程式碼就是 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-137">For example, a file handle is an unmanaged resource.</span></span> <span data-ttu-id="9aa0c-138"><xref:System.IO.FileStream> 物件是Managed 物件，但會 Unmanaged 檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-138">A <xref:System.IO.FileStream> object is a managed object, but it references a file handle, which is unmanaged.</span></span> <span data-ttu-id="9aa0c-139">當您完成使用 <xref:System.IO.FileStream> 時，您必須釋放檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-139">When you're done using the <xref:System.IO.FileStream>, you need to release the file handle.</span></span>

<span data-ttu-id="9aa0c-140">在.NET 中，參考 Unmanaged 資源的物件會實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-140">In .NET, objects that reference unmanaged resources implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9aa0c-141">當您完成使用此物件時，您可以呼叫物件的 <xref:System.IDisposable.Dispose> 方法來釋放任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-141">When you're done using the object, you call the object's <xref:System.IDisposable.Dispose> method, which is responsible for releasing any unmanaged resources.</span></span> <span data-ttu-id="9aa0c-142">.NET 語言為這類物件提供了 `using` 語法，此語法十分方便，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-142">.NET languages provide a convenient `using` syntax for such objects, as shown in the following example:</span></span>

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

<span data-ttu-id="9aa0c-143">當 `using` 區塊完成後，.NET 執行階段會自動呼叫 `stream` 物件的 <xref:System.IDisposable.Dispose> 方法來釋放檔案控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-143">Once the `using` block completes, the .NET runtime automatically calls the `stream` object's <xref:System.IDisposable.Dispose> method, which releases the file handle.</span></span> <span data-ttu-id="9aa0c-144">如果例外狀況造成控制項離開區塊，執行階段也會執行此作業。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-144">The runtime also does this if an exception causes control to leave the block.</span></span>

<span data-ttu-id="9aa0c-145">如需詳細資料，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-145">For more details, see the following topics:</span></span>

* <span data-ttu-id="9aa0c-146">若是 C#，請參閱 [using 陳述式 (C# 參考)](../csharp/language-reference/keywords/using-statement.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-146">For C#, see the [using Statement (C# Reference)](../csharp/language-reference/keywords/using-statement.md) topic.</span></span>
* <span data-ttu-id="9aa0c-147">若是 F#，請參閱[資源管理：use 關鍵字](../fsharp/language-reference/resource-management-the-use-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-147">For F#, see [Resource Management: The use Keyword](../fsharp/language-reference/resource-management-the-use-keyword.md).</span></span>
* <span data-ttu-id="9aa0c-148">若是 VB，請參閱 [Using 陳述式 (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-148">For VB, see the [Using Statement (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) topic.</span></span>

## <a name="type-safety"></a><span data-ttu-id="9aa0c-149">型別安全</span><span class="sxs-lookup"><span data-stu-id="9aa0c-149">Type safety</span></span>

<span data-ttu-id="9aa0c-150">物件是特定類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-150">An object is an instance of a specific type.</span></span> <span data-ttu-id="9aa0c-151">指定物件所允許的唯一作業會是其類型所允許的作業。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-151">The only operations allowed for a given object are those of its type.</span></span> <span data-ttu-id="9aa0c-152">`Dog` 類型可能會有 `Jump` 和 `WagTail` 方法，但沒有 `SumTotal` 方法。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-152">A `Dog` type may have `Jump` and `WagTail` methods but not a `SumTotal` method.</span></span> <span data-ttu-id="9aa0c-153">程式只能呼叫屬於指定類型的方法。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-153">A program only calls the methods belonging to a given type.</span></span> <span data-ttu-id="9aa0c-154">所有其他呼叫會導致編譯時期錯誤，或執行階段例外狀況 (如果使用動態功能或 `object`)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-154">All other calls result in either a compile-time error or a run-time exception (in case of using dynamic features or `object`).</span></span>

<span data-ttu-id="9aa0c-155">.NET 語言是物件導向，具有基底和衍生類別的階層架構。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-155">.NET languages are object-oriented with hierarchies of base and derived classes.</span></span> <span data-ttu-id="9aa0c-156">.NET 執行階段只允許符合物件階層架構的的物件轉換和呼叫。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-156">The .NET runtime only allows object casts and calls that align with the object hierarchy.</span></span> <span data-ttu-id="9aa0c-157">請記住，以任何 .NET 語言所定義的每種類型都是衍生自基底 <xref:System.Object> 型別。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-157">Remember that every type defined in any .NET language derives from the base <xref:System.Object> type.</span></span>

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

<span data-ttu-id="9aa0c-158">此外也會使用型別安全，藉由確保存取子關鍵字的精確度，來協助強制執行封裝。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-158">Type safety is also used to help enforce encapsulation by guaranteeing the fidelity of the accessor keywords.</span></span> <span data-ttu-id="9aa0c-159">存取子關鍵字是控制其他程式碼存取指定型別成員的成品。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-159">Accessor keywords are artifacts which control access to members of a given type by other code.</span></span> <span data-ttu-id="9aa0c-160">這些關鍵字通常會用於某種類型中用來管理其行為的各種資料。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-160">These are usually used for various kinds of data within a type that are used to manage its behavior.</span></span>

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

<span data-ttu-id="9aa0c-161">C#、VB 與 F# 支援本機「型別推斷」。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-161">C#, VB, and F# support local *type inference*.</span></span> <span data-ttu-id="9aa0c-162">型別推斷表示編譯器會從右邊的運算式推算左邊的運算式類型。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-162">Type inference means that the compiler deduces the type of the expression on the left-hand side from the expression on the right-hand side.</span></span> <span data-ttu-id="9aa0c-163">這並不會破壞或規避型別安全。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-163">This doesn't mean that the type safety is broken or avoided.</span></span> <span data-ttu-id="9aa0c-164">產生的類型確實具有強型別，其中包含其所指的所有項目。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-164">The resulting type does have a strong type with everything that implies.</span></span> <span data-ttu-id="9aa0c-165">上述範例中的 `dog` 和 `cat` 已重寫並引入型別推斷，範例的其餘部分則保持不變：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-165">From the previous example, `dog` and `cat` are rewritten to introduce type inference, and the remainder of the example is unchanged:</span></span>

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

<span data-ttu-id="9aa0c-166">F# 提供比 C# 和 VB 中的方法區域型別推斷更進步的型別推斷功能。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-166">F# has even further type inference capabilities than the method-local type inference found in C# and VB.</span></span> <span data-ttu-id="9aa0c-167">如需詳細資訊，請參閱[型別推斷](../fsharp/language-reference/type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-167">To learn more, see [Type Inference](../fsharp/language-reference/type-inference.md).</span></span>

## <a name="delegates-and-lambdas"></a><span data-ttu-id="9aa0c-168">委派和 Lambda</span><span class="sxs-lookup"><span data-stu-id="9aa0c-168">Delegates and lambdas</span></span>

<span data-ttu-id="9aa0c-169">委派是以方法簽章表示。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-169">A delegate is represented by a method signature.</span></span> <span data-ttu-id="9aa0c-170">任何具有該簽章的方法都可以指派給委派，並在叫用委派時執行。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-170">Any method with that signature can be assigned to the delegate and is executed when the delegate is invoked.</span></span>

<span data-ttu-id="9aa0c-171">委派與 C++ 函式指標類似，不同之處在於委派是型別安全。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-171">Delegates are like C++ function pointers except that they're type safe.</span></span> <span data-ttu-id="9aa0c-172">委派是 CLR 型別系統中一種已中斷連線的方法。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-172">They're a kind of disconnected method within the CLR type system.</span></span> <span data-ttu-id="9aa0c-173">一般方法是附加到類別，並且只能透過靜態或執行個體呼叫慣例來直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-173">Regular methods are attached to a class and are only directly callable through static or instance calling conventions.</span></span>

<span data-ttu-id="9aa0c-174">在 .NET 中，委派常用於事件處理常式以定義非同步作業，並可用於 Lambda 運算式，這是 LINQ 的基石。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-174">In .NET, delegates are commonly used in event handlers, in defining asynchronous operations, and in lambda expressions, which are a cornerstone of LINQ.</span></span> <span data-ttu-id="9aa0c-175">深入了解[委派和 Lambda](delegates-lambdas.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-175">Learn more in the [Delegates and lambdas](delegates-lambdas.md) topic.</span></span>

## <a name="generics"></a><span data-ttu-id="9aa0c-176">泛型</span><span class="sxs-lookup"><span data-stu-id="9aa0c-176">Generics</span></span>

<span data-ttu-id="9aa0c-177">泛型可讓程式設計師在設計其類別時引入「型別參數」，如此即可讓用戶端程式碼 (類型的使用者) 指定正確類型來取代型別參數。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-177">Generics allow the programmer to introduce a *type parameter* when designing their classes that allows the client code (the users of the type) to specify the exact type to use in place of the type parameter.</span></span>

<span data-ttu-id="9aa0c-178">新增泛型功能是為了協助程式設計師實作泛型資料結構。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-178">Generics were added to help programmers implement generic data structures.</span></span> <span data-ttu-id="9aa0c-179">在此功能之前，若要讓 `List` 等類型成為泛型，您必須使用 `object` 類型的項目。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-179">Before their arrival in order for a type such as the `List` type to be generic, it would have to work with elements that were of type `object`.</span></span> <span data-ttu-id="9aa0c-180">這樣做會有各種效能及語意問題，更別提可能會有難以解決的執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-180">This had various performance and semantic problems, along with possible subtle runtime errors.</span></span> <span data-ttu-id="9aa0c-181">後者最糟的情況是當資料結構同時包含整數與字串時，而且會在使用清單的成員時擲回 `InvalidCastException`。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-181">The most notorious of the latter is when a data structure contains, for instance, both integers and strings, and an `InvalidCastException` is thrown on working with the list's members.</span></span>

<span data-ttu-id="9aa0c-182">下列範例顯示使用 <xref:System.Collections.Generic.List%601> 類型執行個體的基本程式正在執行：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-182">The following sample shows a basic program running using an instance of <xref:System.Collections.Generic.List%601> types:</span></span>

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

<span data-ttu-id="9aa0c-183">如需詳細資訊，請參閱[泛型型別 (泛型) 概觀](generics.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-183">For more information, see the [Generic types (Generics) overview](generics.md) topic.</span></span>

## <a name="async-programming"></a><span data-ttu-id="9aa0c-184">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="9aa0c-184">Async programming</span></span>

<span data-ttu-id="9aa0c-185">非同步程式設計是 .NET 中的最高階概念，包括執行階段、架構程式庫和 .NET 語言建構的非同步支援。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-185">Async programming is a first-class concept within .NET with async support in the runtime, framework libraries, and .NET language constructs.</span></span> <span data-ttu-id="9aa0c-186">就內部而言，它們是以物件 (例如 `Task`) 為基礎，可利用作業系統盡可能有效率地執行 I/O 繫結工作。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-186">Internally, they're based on objects (such as `Task`), which take advantage of the operating system to perform I/O-bound jobs as efficiently as possible.</span></span>

<span data-ttu-id="9aa0c-187">若要深入了解 .NET 非同步程式設計，請從[非同步概觀](async.md)主題開始。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-187">To learn more about async programming in .NET, start with the [Async overview](async.md) topic.</span></span>

## <a name="language-integrated-query-linq"></a><span data-ttu-id="9aa0c-188">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9aa0c-188">Language Integrated Query (LINQ)</span></span>

<span data-ttu-id="9aa0c-189">LINQ 是一組強大的 C# 和 VB 功能，可讓您撰寫簡單的宣告式程式碼來操作資料。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-189">LINQ is a powerful set of features for C# and VB that allow you to write simple, declarative code for operating on data.</span></span> <span data-ttu-id="9aa0c-190">資料可以是許多形式 (例如記憶體內部物件、SQL 資料庫或 XML 文件)，但您撰寫的 LINQ 程式碼在資料來源方面通常大同小異。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-190">The data can be in many forms (such as in-memory objects, a SQL database, or an XML document), but the LINQ code you write typically doesn't differ by data source.</span></span>

<span data-ttu-id="9aa0c-191">若要深入了解及查看一些範例，請參閱 [LINQ (Language Integrated Query)](using-linq.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-191">To learn more and see some samples, see the [LINQ (Language Integrated Query)](using-linq.md) topic.</span></span>

## <a name="native-interoperability"></a><span data-ttu-id="9aa0c-192">原生互通性</span><span class="sxs-lookup"><span data-stu-id="9aa0c-192">Native interoperability</span></span>

<span data-ttu-id="9aa0c-193">每個作業系統都包含提供系統服務的應用程式開發介面 (API)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-193">Every operating system includes an application programming interface (API) that provides system services.</span></span> <span data-ttu-id="9aa0c-194">.NET 提供幾種方式來呼叫這些 API。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-194">.NET provides several ways to call those APIs.</span></span>

<span data-ttu-id="9aa0c-195">執行原生互通性的主要方式是透過「平台叫用」(簡稱 P/Invoke)，這在 Linux 和 Windows 平台之間都受到支援。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-195">The main way to do native interoperability is via "platform invoke" or P/Invoke for short, which is supported across Linux and Windows platforms.</span></span> <span data-ttu-id="9aa0c-196">另一項僅適用於 Windows 的原生互通性做法稱為 "COM Interop"，可用來處理 Managed 程式碼中的 [COM 元件](https://msdn.microsoft.com/library/bwa2bx93.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-196">A Windows-only way of doing native interoperability is known as "COM interop," which is used to work with [COM components](https://msdn.microsoft.com/library/bwa2bx93.aspx) in managed code.</span></span> <span data-ttu-id="9aa0c-197">它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-197">It's built on top of the P/Invoke infrastructure, but it works in subtly different ways.</span></span>

<span data-ttu-id="9aa0c-198">Mono (以及 Xamarin) 對 Java 和 Objective-C 的互通性支援大致上很類似；也就是說，它們使用相同的原則。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-198">Most of Mono's (and thus Xamarin's) interoperability support for Java and Objective-C are built similarly, that is, they use the same principles.</span></span>

<span data-ttu-id="9aa0c-199">若要深入了解原生互通性，請參閱[原生互通性](native-interop.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-199">Read more about it native interoperability in the [Native interoperability](native-interop.md) topic.</span></span>

## <a name="unsafe-code"></a><span data-ttu-id="9aa0c-200">Unsafe 程式碼</span><span class="sxs-lookup"><span data-stu-id="9aa0c-200">Unsafe code</span></span>

<span data-ttu-id="9aa0c-201">CLR 可讓您根據語言支援透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-201">Depending on language support, the CLR lets you access native memory and do pointer arithmetic via `unsafe` code.</span></span> <span data-ttu-id="9aa0c-202">特定演算法和系統互通性需要這些作業。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-202">These operations are needed for certain algorithms and system interoperability.</span></span> <span data-ttu-id="9aa0c-203">Unsafe 程式碼雖然功能強大，但除非是必須與系統 API 互通，或必須實作最有效率的演算法，否則不建議使用。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-203">Although powerful, use of unsafe code is discouraged unless it's necessary to interop with system APIs or implement the most efficient algorithm.</span></span> <span data-ttu-id="9aa0c-204">Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-204">Unsafe code may not execute the same way in different environments and also loses the benefits of a garbage collector and type safety.</span></span> <span data-ttu-id="9aa0c-205">建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-205">It's recommended to confine and centralize unsafe code as much as possible and test that code thoroughly.</span></span>

<span data-ttu-id="9aa0c-206">下列範例是 `StringBuilder` 類別的 `ToString()` 方法修改後的版本。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-206">The following example is a modified version of the `ToString()` method from the `StringBuilder` class.</span></span> <span data-ttu-id="9aa0c-207">它說明如何使用 `unsafe` 程式碼直接四處移動記憶體區塊，以有效率地實作演算法：</span><span class="sxs-lookup"><span data-stu-id="9aa0c-207">It illustrates how using `unsafe` code can efficiently implement an algorithm by moving around chunks of memory directly:</span></span>

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a><span data-ttu-id="9aa0c-208">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9aa0c-208">Next steps</span></span>

<span data-ttu-id="9aa0c-209">若您對 C# 功能的教學課程感興趣，請參閱 [C# 教學課程](../csharp/tour-of-csharp/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-209">If you're interested in a tour of C# features, check out [Tour of C#](../csharp/tour-of-csharp/index.md).</span></span>

<span data-ttu-id="9aa0c-210">若您對 F# 功能的教學課程感興趣，請參閱 [F# 教學課程](../fsharp/tour.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-210">If you're interested in a tour of F# features, see [Tour of F#](../fsharp/tour.md).</span></span>

<span data-ttu-id="9aa0c-211">若要開始撰寫自己的程式碼，請瀏覽[使用者入門](get-started.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-211">If you want to get started with writing code of your own, visit [Getting Started](get-started.md).</span></span>

<span data-ttu-id="9aa0c-212">若要了解重要的 .NET 元件，請參閱 [.NET 架構元件](components.md)。</span><span class="sxs-lookup"><span data-stu-id="9aa0c-212">To learn about important components of .NET, check out [.NET Architectural Components](components.md).</span></span>
