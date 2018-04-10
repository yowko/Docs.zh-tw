---
title: C# 的教學課程 - C# 指南
description: 第一次接觸 C#？ 了解該語言的基本概念。
keywords: .NET, .NET Core, C#, C# Primer, C# Guide
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ebc727cd-8112-42e7-b59c-3c2873ad661c
ms.openlocfilehash: 0fa7f9f906ba72b114fc59c8026b4b6c79586dd2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="a-tour-of-the-c-language"></a><span data-ttu-id="34326-105">C# 語言教學課程</span><span class="sxs-lookup"><span data-stu-id="34326-105">A Tour of the C# Language</span></span>  

<span data-ttu-id="34326-106">C# (發音為 "See Sharp") 是簡單、物件導向、型別安全的現代化程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="34326-106">C# (pronounced "See Sharp") is a simple, modern, object-oriented, and type-safe programming language.</span></span> <span data-ttu-id="34326-107">C# 源自於是 C 系列語言，使用 C、C++、Java 和 JavaScript 的程式設計人員會立即感到熟悉。</span><span class="sxs-lookup"><span data-stu-id="34326-107">C# has its roots in the C family of languages and will be immediately familiar to C, C++, Java, and JavaScript programmers.</span></span>

<span data-ttu-id="34326-108">C# 是物件導向的語言，但 C# 更進一步支援「元件導向」程式設計。</span><span class="sxs-lookup"><span data-stu-id="34326-108">C# is an object-oriented language, but C# further includes support for ***component-oriented*** programming.</span></span> <span data-ttu-id="34326-109">現代軟體設計逐漸依賴功能性上獨立與屬於自我描述套件的軟體元件。</span><span class="sxs-lookup"><span data-stu-id="34326-109">Contemporary software design increasingly relies on software components in the form of self-contained and self-describing packages of functionality.</span></span> <span data-ttu-id="34326-110">這類元件的關鍵在於它們呈現含有屬性、方法和事件的程式設計模型；它們提供元件相關宣告資訊的屬性，且併入自己的文件。</span><span class="sxs-lookup"><span data-stu-id="34326-110">Key to such components is that they present a programming model with properties, methods, and events; they have attributes that provide declarative information about the component; and they incorporate their own documentation.</span></span> <span data-ttu-id="34326-111">C# 提供語言建構來直接支援這些概念，使 C# 成為對建立及使用軟體元件都非常自然的語言。</span><span class="sxs-lookup"><span data-stu-id="34326-111">C# provides language constructs to support directly these concepts, making C# a very natural language in which to create and use software components.</span></span>

<span data-ttu-id="34326-112">以下幾個 C# 功能有助於建構健全且持久的應用程式：「記憶體回收」自動取回不可能執行到且未使用的物件所佔用的記憶體；「例外狀況處理」針對錯誤偵測及復原提供結構化且可延伸的方法；該語言「型別安全」的設計使讀取未初始化的變數、索引超出陣列的範圍，或執行未檢查的型別轉換變得不可能。</span><span class="sxs-lookup"><span data-stu-id="34326-112">Several C# features aid in the construction of robust and durable applications: ***Garbage collection*** automatically reclaims memory occupied by unreachable unused objects; ***exception handling*** provides a structured and extensible approach to error detection and recovery; and the ***type-safe*** design of the language makes it impossible to read from uninitialized variables, to index arrays beyond their bounds, or to perform unchecked type casts.</span></span>

<span data-ttu-id="34326-113">C# 有***統一的型別系統***。</span><span class="sxs-lookup"><span data-stu-id="34326-113">C# has a ***unified type system***.</span></span> <span data-ttu-id="34326-114">所有的 C# 型別 (包括 `int` 和 `double` 等基本型別) 都繼承自單一的 `object` 根型別。</span><span class="sxs-lookup"><span data-stu-id="34326-114">All C# types, including primitive types such as `int` and `double`, inherit from a single root `object` type.</span></span> <span data-ttu-id="34326-115">因此，所有型別都擁有相同的一組常見作業，且任何型別的值都能以相同方式儲存、傳送及操作。</span><span class="sxs-lookup"><span data-stu-id="34326-115">Thus, all types share a set of common operations, and values of any type can be stored, transported, and operated upon in a consistent manner.</span></span> <span data-ttu-id="34326-116">此外，C# 支援使用者定義的參考型別和數值型別，因此能動態配置物件，以及內嵌儲存輕量結構。</span><span class="sxs-lookup"><span data-stu-id="34326-116">Furthermore, C# supports both user-defined reference types and value types, allowing dynamic allocation of objects as well as in-line storage of lightweight structures.</span></span>

<span data-ttu-id="34326-117">為了確保 C# 程式和程式庫能以相容的方式隨時間演進，C# 的設計中特別強調「版本控制」。</span><span class="sxs-lookup"><span data-stu-id="34326-117">To ensure that C# programs and libraries can evolve over time in a compatible manner, much emphasis has been placed on ***versioning*** in C#’s design.</span></span> <span data-ttu-id="34326-118">許多程式設計語言並不注重此問題，因此當推出新版的相依程式庫時，以那些語言撰寫的程式需要進行較多修改才能繼續運作。</span><span class="sxs-lookup"><span data-stu-id="34326-118">Many programming languages pay little attention to this issue, and, as a result, programs written in those languages break more often than necessary when newer versions of dependent libraries are introduced.</span></span> <span data-ttu-id="34326-119">直接受版本控制考量影響的 C# 設計層面包括個別的 `virtual` 與 `override` 修飾詞、方法多載解析的規則，以及對明確介面成員宣告的支援。</span><span class="sxs-lookup"><span data-stu-id="34326-119">Aspects of C#’s design that were directly influenced by versioning considerations include the separate `virtual` and `override` modifiers, the rules for method overload resolution, and support for explicit interface member declarations.</span></span>

## <a name="hello-world"></a><span data-ttu-id="34326-120">Hello World</span><span class="sxs-lookup"><span data-stu-id="34326-120">Hello world</span></span>

<span data-ttu-id="34326-121">“Hello, World” 程式通常用來介紹程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="34326-121">The "Hello, World" program is traditionally used to introduce a programming language.</span></span> <span data-ttu-id="34326-122">以下是以 C# 撰寫的：</span><span class="sxs-lookup"><span data-stu-id="34326-122">Here it is in C#:</span></span>

[!code-csharp[Hello World](../../../samples/snippets/csharp/tour/hello/Program.cs#L1-L8)]

<span data-ttu-id="34326-123">C# 原始程式檔的副檔名通常是 `.cs`。</span><span class="sxs-lookup"><span data-stu-id="34326-123">C# source files typically have the file extension `.cs`.</span></span> <span data-ttu-id="34326-124">假設 “Hello, World” 程式儲存在檔案 `hello.cs` 之中，該程式可以使用下列命令列編譯：</span><span class="sxs-lookup"><span data-stu-id="34326-124">Assuming that the "Hello, World" program is stored in the file `hello.cs`, the program might be compiled using the command line:</span></span>

```console
csc hello.cs
```

<span data-ttu-id="34326-125">這樣會建立名稱為 hello.exe 的可執行組件。</span><span class="sxs-lookup"><span data-stu-id="34326-125">which produces an executable assembly named hello.exe.</span></span> <span data-ttu-id="34326-126">當此應用程式執行時，它產生的輸出為：</span><span class="sxs-lookup"><span data-stu-id="34326-126">The output produced by this application when it is run is:</span></span>

```console
Hello, World
```

> [!IMPORTANT]
> <span data-ttu-id="34326-127">`csc` 命令會針對完整架構進行編譯，而且可能不是在所有平台上都能取得。</span><span class="sxs-lookup"><span data-stu-id="34326-127">The `csc` command compiles for the full framework, and may not be available on all platforms.</span></span>


<span data-ttu-id="34326-128">“Hello, World” 程式的開頭為 `using` 指示詞，會參考 `System` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="34326-128">The "Hello, World" program starts with a `using` directive that references the `System` namespace.</span></span> <span data-ttu-id="34326-129">命名空間提供組織 C# 程式和程式庫的階層式方法。</span><span class="sxs-lookup"><span data-stu-id="34326-129">Namespaces provide a hierarchical means of organizing C# programs and libraries.</span></span> <span data-ttu-id="34326-130">命名空間包含型別和其他命名空間，例如 `System` 命名空間包含數個型別 (如程式中參考的 `Console` 類別)，和數個其他命名空間 (如 `IO` 和 `Collections`)。</span><span class="sxs-lookup"><span data-stu-id="34326-130">Namespaces contain types and other namespaces—for example, the `System` namespace contains a number of types, such as the `Console` class referenced in the program, and a number of other namespaces, such as `IO` and `Collections`.</span></span> <span data-ttu-id="34326-131">使用 `using` 指示詞參考指定的命名空間，就能以非限定的方式使用屬於該命名空間成員的型別。</span><span class="sxs-lookup"><span data-stu-id="34326-131">A `using` directive that references a given namespace enables unqualified use of the types that are members of that namespace.</span></span> <span data-ttu-id="34326-132">因為 `using` 指示詞的緣故，該程式可以使用 `Console.WriteLine` 當作 `System.Console.WriteLine` 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="34326-132">Because of the `using` directive, the program can use `Console.WriteLine` as shorthand for `System.Console.WriteLine`.</span></span>

<span data-ttu-id="34326-133">“Hello, World” 程式宣告的 `Hello` 類別包含單一成員，即名為 `Main` 的方法。</span><span class="sxs-lookup"><span data-stu-id="34326-133">The `Hello` class declared by the "Hello, World" program has a single member, the method named `Main`.</span></span> <span data-ttu-id="34326-134">`Main` 方法是使用 static 修飾詞來宣告。</span><span class="sxs-lookup"><span data-stu-id="34326-134">The `Main` method is declared with the static modifier.</span></span> <span data-ttu-id="34326-135">執行個體方法可以使用關鍵字 `this` 參考特定的封入物件執行個體，但靜態方法卻不需要參考特定物件即可運作。</span><span class="sxs-lookup"><span data-stu-id="34326-135">While instance methods can reference a particular enclosing object instance using the keyword `this`, static methods operate without reference to a particular object.</span></span> <span data-ttu-id="34326-136">依照慣例，會使用名為 `Main` 的靜態方法做為程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="34326-136">By convention, a static method named `Main` serves as the entry point of a program.</span></span>

<span data-ttu-id="34326-137">程式的輸出是由 `System` 命名空間中 `Console` 類別的 `WriteLine` 方法產生。</span><span class="sxs-lookup"><span data-stu-id="34326-137">The output of the program is produced by the `WriteLine` method of the `Console` class in the `System` namespace.</span></span> <span data-ttu-id="34326-138">此類別是由標準類別程式庫提供，根據預設，編譯器會自動參考此程式庫。</span><span class="sxs-lookup"><span data-stu-id="34326-138">This class is provided by the standard class libraries, which, by default, are automatically referenced by the compiler.</span></span>

<span data-ttu-id="34326-139">C# 還有更多可探討的主題。</span><span class="sxs-lookup"><span data-stu-id="34326-139">There's a lot more to learn about C#.</span></span>  <span data-ttu-id="34326-140">下列主題提供 C# 語言元素的概觀。</span><span class="sxs-lookup"><span data-stu-id="34326-140">The following topics provide an overview of the elements of the C# language.</span></span> <span data-ttu-id="34326-141">這些概觀提供此語言所有元素的基本資訊，並且提供您深入了解 C# 語言元素的必要資訊：</span><span class="sxs-lookup"><span data-stu-id="34326-141">These overviews will provide basic information about all elements of the language and give you the information necessary to dive deeper into elements of the C# language:</span></span>

* [<span data-ttu-id="34326-142">程式結構</span><span class="sxs-lookup"><span data-stu-id="34326-142">Program Structure</span></span>](program-structure.md)
    - <span data-ttu-id="34326-143">了解 C# 語言的重要組織概念：***程式***、***命名空間***、***型別***、***成員***和***組件***。</span><span class="sxs-lookup"><span data-stu-id="34326-143">Learn the key organizational concepts in the C# language: ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span>
* [<span data-ttu-id="34326-144">類型與變數</span><span class="sxs-lookup"><span data-stu-id="34326-144">Types and Variables</span></span>](types-and-variables.md)
    - <span data-ttu-id="34326-145">了解 C# 語言中的***實值型別***、***參考型別***和***變數***。</span><span class="sxs-lookup"><span data-stu-id="34326-145">Learn about ***value types***, ***reference types***, and ***variables*** in the C# language.</span></span>
* [<span data-ttu-id="34326-146">運算式</span><span class="sxs-lookup"><span data-stu-id="34326-146">Expressions</span></span>](expressions.md)
    - <span data-ttu-id="34326-147">「運算式」是由「運算元」和「運算子」建構而成。</span><span class="sxs-lookup"><span data-stu-id="34326-147">***Expressions*** are constructed from ***operands*** and ***operators***.</span></span> <span data-ttu-id="34326-148">運算式會產生值。</span><span class="sxs-lookup"><span data-stu-id="34326-148">Expressions produce a value.</span></span>
* [<span data-ttu-id="34326-149">陳述式</span><span class="sxs-lookup"><span data-stu-id="34326-149">Statements</span></span>](statements.md)
    - <span data-ttu-id="34326-150">您會使用***陳述式***來表達程式的動作。</span><span class="sxs-lookup"><span data-stu-id="34326-150">You use ***statements*** to express the actions of a program.</span></span>
* [<span data-ttu-id="34326-151">類別與物件</span><span class="sxs-lookup"><span data-stu-id="34326-151">Classes and objects</span></span>](classes-and-objects.md)
    - <span data-ttu-id="34326-152">***類別***是 C# 最基本的型別。</span><span class="sxs-lookup"><span data-stu-id="34326-152">***Classes*** are the most fundamental of C#'s types.</span></span> <span data-ttu-id="34326-153">***物件***是類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="34326-153">***Objects*** are instances of a class.</span></span> <span data-ttu-id="34326-154">類別是使用***成員*** (此主題中也有探討) 來建置。</span><span class="sxs-lookup"><span data-stu-id="34326-154">Classes are built using ***members***, which are also covered in this topic.</span></span>
* [<span data-ttu-id="34326-155">結構</span><span class="sxs-lookup"><span data-stu-id="34326-155">Structs</span></span>](structs.md)
    - <span data-ttu-id="34326-156">不同於類別，***結構***是屬於實值型別的資料結構。</span><span class="sxs-lookup"><span data-stu-id="34326-156">***Structs*** are data structures that, unlike classes, are value types.</span></span>
* [<span data-ttu-id="34326-157">陣列</span><span class="sxs-lookup"><span data-stu-id="34326-157">Arrays</span></span>](arrays.md)
    - <span data-ttu-id="34326-158">***陣列***是一種資料結構，其中包含一些可透過計算索引存取的變數。</span><span class="sxs-lookup"><span data-stu-id="34326-158">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span>
* [<span data-ttu-id="34326-159">介面</span><span class="sxs-lookup"><span data-stu-id="34326-159">Interfaces</span></span>](interfaces.md)
    - <span data-ttu-id="34326-160">「介面」定義可由類別和結構實作的合約。</span><span class="sxs-lookup"><span data-stu-id="34326-160">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="34326-161">介面可以包含方法、屬性、事件和索引子。</span><span class="sxs-lookup"><span data-stu-id="34326-161">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="34326-162">介面不提供它所定義之成員的實作 (它只會指定必須由類別提供的成員或實作介面的結構)。</span><span class="sxs-lookup"><span data-stu-id="34326-162">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>
* [<span data-ttu-id="34326-163">列舉</span><span class="sxs-lookup"><span data-stu-id="34326-163">Enums</span></span>](enums.md)
    - <span data-ttu-id="34326-164">「列舉型別」是含一組具名常數的相異實值型別。</span><span class="sxs-lookup"><span data-stu-id="34326-164">An ***enum type*** is a distinct value type with a set of named constants.</span></span>
* [<span data-ttu-id="34326-165">委派</span><span class="sxs-lookup"><span data-stu-id="34326-165">Delegates</span></span>](delegates.md)
    - <span data-ttu-id="34326-166">「委派型別」代表對方法的參考，其中含有特定參數清單與傳回型別。</span><span class="sxs-lookup"><span data-stu-id="34326-166">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="34326-167">委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。</span><span class="sxs-lookup"><span data-stu-id="34326-167">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="34326-168">委派就類似其他程式設計語言中的函式指標，但與函式指標的不同之處是，委派是物件導向且為型別安全。</span><span class="sxs-lookup"><span data-stu-id="34326-168">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>
* [<span data-ttu-id="34326-169">屬性</span><span class="sxs-lookup"><span data-stu-id="34326-169">Attributes</span></span>](attributes.md)
    * <span data-ttu-id="34326-170">***屬性***讓程式能指定型別、成員與實體的相關額外宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="34326-170">***Attributes*** enable programs to specify additional declarative information about types, members, and other entities.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="34326-171">下一步</span><span class="sxs-lookup"><span data-stu-id="34326-171">Next</span></span>](program-structure.md)
