---
title: 教程：創建類型提供程式
description: 通過檢查幾個簡單類型提供程式來說明基本概念，瞭解如何在 F# 3.0 中創建自己的 F# 類型提供程式。
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186116"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="7df16-103">教程：創建類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="7df16-104">F# 中的類型提供程式機制是其支援資訊豐富程式設計的重要組成部分。</span><span class="sxs-lookup"><span data-stu-id="7df16-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="7df16-105">本教程介紹如何通過引導您完成幾個簡單類型提供程式的開發來說明基本概念，從而創建自己的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="7df16-106">有關 F# 中的類型提供程式機制的詳細資訊，請參閱[類型提供程式](index.md)。</span><span class="sxs-lookup"><span data-stu-id="7df16-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="7df16-107">F# 生態系統包含一系列用於常用 Internet 和企業資料服務的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="7df16-108">例如：</span><span class="sxs-lookup"><span data-stu-id="7df16-108">For example:</span></span>

- <span data-ttu-id="7df16-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/)包括 JSON、XML、CSV 和 HTML 文檔格式的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="7df16-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/)通過物件映射和針對這些資料來源的 F# LINQ 查詢提供對 SQL 資料庫的強型別訪問。</span><span class="sxs-lookup"><span data-stu-id="7df16-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="7df16-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)具有一組類型提供程式，用於在 F# 中編譯時檢查的 T-SQL 嵌入。</span><span class="sxs-lookup"><span data-stu-id="7df16-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="7df16-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是一組較舊的類型提供程式，僅用於 .NET 框架程式設計，用於訪問 SQL、實體框架、OData 和 WSDL 資料服務。</span><span class="sxs-lookup"><span data-stu-id="7df16-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="7df16-113">必要時，您可以創建自訂類型提供程式，也可以引用其他人創建的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="7df16-114">例如，您的組織可以有一個資料服務，該服務提供大量且不斷增加的命名資料集，每個資料集都有自己的穩定資料架構。</span><span class="sxs-lookup"><span data-stu-id="7df16-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="7df16-115">您可以創建一個類型提供程式，用於讀取架構，並以強型別方式向程式師顯示當前資料集。</span><span class="sxs-lookup"><span data-stu-id="7df16-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7df16-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="7df16-116">Before You Start</span></span>

<span data-ttu-id="7df16-117">類型提供程式機制主要用於將穩定的資料和服務資訊空間注入 F# 程式設計體驗。</span><span class="sxs-lookup"><span data-stu-id="7df16-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="7df16-118">此機制不是為注入資訊空間而設計的，其架構在程式執行期間以與程式邏輯相關的方式更改。</span><span class="sxs-lookup"><span data-stu-id="7df16-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="7df16-119">此外，該機制不是為語言內部元程式設計而設計的，即使該域包含一些有效的用途。</span><span class="sxs-lookup"><span data-stu-id="7df16-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="7df16-120">僅當必要且類型提供程式的開發產生非常高的值時，才應使用此機制。</span><span class="sxs-lookup"><span data-stu-id="7df16-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="7df16-121">應避免編寫架構不可用的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="7df16-122">同樣，應避免編寫普通（甚至現有）.NET 庫就足夠了的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="7df16-123">在開始之前，您可能會提出以下問題：</span><span class="sxs-lookup"><span data-stu-id="7df16-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="7df16-124">您是否有資訊源的架構？</span><span class="sxs-lookup"><span data-stu-id="7df16-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="7df16-125">如果是，則什麼是映射到 F# 和 .NET 類型系統？</span><span class="sxs-lookup"><span data-stu-id="7df16-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="7df16-126">能否使用現有（動態類型）API 作為實現的起點？</span><span class="sxs-lookup"><span data-stu-id="7df16-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="7df16-127">您和您的組織是否有足夠的類型提供程式的使用來使編寫它是值得的？</span><span class="sxs-lookup"><span data-stu-id="7df16-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="7df16-128">普通的 .NET 庫能滿足您的需求嗎？</span><span class="sxs-lookup"><span data-stu-id="7df16-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="7df16-129">架構將更改多少？</span><span class="sxs-lookup"><span data-stu-id="7df16-129">How much will your schema change?</span></span>

- <span data-ttu-id="7df16-130">在編碼過程中會發生變化嗎？</span><span class="sxs-lookup"><span data-stu-id="7df16-130">Will it change during coding?</span></span>

- <span data-ttu-id="7df16-131">它會在編碼會話之間更改嗎？</span><span class="sxs-lookup"><span data-stu-id="7df16-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="7df16-132">在程式執行期間會更改嗎？</span><span class="sxs-lookup"><span data-stu-id="7df16-132">Will it change during program execution?</span></span>

<span data-ttu-id="7df16-133">類型提供程式最適合在運行時和編譯代碼的存留期內架構穩定的情況。</span><span class="sxs-lookup"><span data-stu-id="7df16-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="7df16-134">簡單類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-134">A Simple Type Provider</span></span>

<span data-ttu-id="7df16-135">此示例是示例。HelloWorldTypeProvider，類似于`examples`[F# 類型提供程式 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)目錄中的示例。</span><span class="sxs-lookup"><span data-stu-id="7df16-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="7df16-136">提供程式提供包含 100 種擦除類型的"類型空間"，如下代碼通過使用 F# 簽名語法和省略除 之外`Type1`的所有代碼的詳細資訊來顯示的。</span><span class="sxs-lookup"><span data-stu-id="7df16-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="7df16-137">有關擦除類型的詳細資訊，請參閱本主題後面的[有關已擦除提供類型的詳細資訊](#details-about-erased-provided-types)。</span><span class="sxs-lookup"><span data-stu-id="7df16-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="7df16-138">請注意，提供的類型和成員集是靜態已知的。</span><span class="sxs-lookup"><span data-stu-id="7df16-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="7df16-139">此示例不利用提供程式提供依賴于架構的類型的能力。</span><span class="sxs-lookup"><span data-stu-id="7df16-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="7df16-140">類型提供程式的實現在以下代碼中概述，本主題的後續部分將介紹詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7df16-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="7df16-141">此代碼和連線示例之間可能存在差異。</span><span class="sxs-lookup"><span data-stu-id="7df16-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="7df16-142">要使用此提供程式，請打開 Visual Studio 的單獨實例，創建 F# 腳本，然後使用#r添加對提供程式的引用，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="7df16-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="7df16-143">然後查找類型提供程式生成的`Samples.HelloWorldTypeProvider`命名空間下的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="7df16-144">在重新編譯提供程式之前，請確保已關閉使用提供程式 DLL 的所有 Visual Studio 和 F# 互動式實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="7df16-145">否則，將發生建置錯誤，因為輸出 DLL 將被鎖定。</span><span class="sxs-lookup"><span data-stu-id="7df16-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="7df16-146">要使用列印語句調試此提供程式，請製作一個顯示提供程式問題的腳本，然後使用以下代碼：</span><span class="sxs-lookup"><span data-stu-id="7df16-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="7df16-147">要使用 Visual Studio 調試此提供程式，請使用管理認證打開 Visual Studio 的開發人員命令提示符，並運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="7df16-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="7df16-148">作為替代，打開 Visual Studio，打開調試功能表，選擇`Debug/Attach to process…`，並附加到編輯`devenv`腳本的其他進程。</span><span class="sxs-lookup"><span data-stu-id="7df16-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="7df16-149">通過使用此方法，您可以通過將運算式交互地鍵入第二個實例（具有完整的 IntelliSense 和其他功能）來更輕鬆地定位類型提供程式中的特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="7df16-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="7df16-150">您可以禁用"僅我的代碼"調試，以便更好地識別生成的代碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7df16-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="7df16-151">有關如何啟用或禁用此功能的資訊，請參閱[使用調試器 通過代碼導航](/visualstudio/debugger/navigating-through-code-with-the-debugger)。</span><span class="sxs-lookup"><span data-stu-id="7df16-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="7df16-152">此外，您還可以通過打開`Debug`功能表，然後選擇或選擇`Exceptions`Ctrl_Alt_E 鍵來打開`Exceptions`對話方塊來設置第一次異常捕獲。</span><span class="sxs-lookup"><span data-stu-id="7df16-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="7df16-153">在該對話方塊中，在`Common Language Runtime Exceptions`下，`Thrown`選擇核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7df16-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="7df16-154">類型提供程式的實現</span><span class="sxs-lookup"><span data-stu-id="7df16-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="7df16-155">本節將介紹類型提供程式實現的主要部分。</span><span class="sxs-lookup"><span data-stu-id="7df16-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="7df16-156">首先，定義自訂類型提供程式本身的類型：</span><span class="sxs-lookup"><span data-stu-id="7df16-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="7df16-157">此類型必須是公共的，並且必須使用[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性標記它，以便編譯器在單獨的 F# 專案引用包含該類型的程式集時識別類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="7df16-158">*配置*參數是可選的，如果存在，則包含 F# 編譯器創建的類型提供程式實例的上下文配置資訊。</span><span class="sxs-lookup"><span data-stu-id="7df16-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="7df16-159">接下來，實現[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。</span><span class="sxs-lookup"><span data-stu-id="7df16-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="7df16-160">在這種情況下，您將 API`TypeProviderForNamespaces`中的`ProvidedTypes`類型用作基本類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="7df16-161">此説明器類型可以提供熱切提供的命名空間的有限集合，每個命名空間都直接包含有限數量的固定、熱切提供的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="7df16-162">在此上下文中，提供程式*熱切地*組建類型，即使它們不需要或使用。</span><span class="sxs-lookup"><span data-stu-id="7df16-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="7df16-163">接下來，定義指定提供類型的命名空間的本地私有值，並查找類型提供程式程式集本身。</span><span class="sxs-lookup"><span data-stu-id="7df16-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="7df16-164">稍後，此程式集用作提供的擦除類型的邏輯父類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="7df16-165">接下來，創建一個函數來提供 Type1...類型 100。</span><span class="sxs-lookup"><span data-stu-id="7df16-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="7df16-166">本主題稍後將更詳細地介紹此功能。</span><span class="sxs-lookup"><span data-stu-id="7df16-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="7df16-167">接下來，生成 100 個提供的類型：</span><span class="sxs-lookup"><span data-stu-id="7df16-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="7df16-168">接下來，將類型添加為提供的命名空間：</span><span class="sxs-lookup"><span data-stu-id="7df16-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="7df16-169">最後，添加一個程式集屬性，指示要創建類型提供程式 DLL：</span><span class="sxs-lookup"><span data-stu-id="7df16-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="7df16-170">提供一種類型及其成員</span><span class="sxs-lookup"><span data-stu-id="7df16-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="7df16-171">函數`makeOneProvidedType`執行提供其中一種類型的實際工作。</span><span class="sxs-lookup"><span data-stu-id="7df16-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="7df16-172">此步驟解釋了此函數的實現。</span><span class="sxs-lookup"><span data-stu-id="7df16-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="7df16-173">首先，創建提供的類型（例如，類型 1，當 n = 1 時，或 Type57，當 n = 57）。</span><span class="sxs-lookup"><span data-stu-id="7df16-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="7df16-174">您應該注意以下幾點：</span><span class="sxs-lookup"><span data-stu-id="7df16-174">You should note the following points:</span></span>

- <span data-ttu-id="7df16-175">此提供的類型將被刪除。</span><span class="sxs-lookup"><span data-stu-id="7df16-175">This provided type is erased.</span></span>  <span data-ttu-id="7df16-176">由於您指示基類型為`obj`，因此實例將在編譯代碼中顯示為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)類型的值。</span><span class="sxs-lookup"><span data-stu-id="7df16-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="7df16-177">指定非巢狀型別時，必須指定程式集和命名空間。</span><span class="sxs-lookup"><span data-stu-id="7df16-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="7df16-178">對於擦除的類型，程式集應是類型提供程式程式集本身。</span><span class="sxs-lookup"><span data-stu-id="7df16-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="7df16-179">接下來，將 XML 文檔添加到類型中。</span><span class="sxs-lookup"><span data-stu-id="7df16-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="7df16-180">本文檔延遲，即，如果主機編譯器需要，則按需計算。</span><span class="sxs-lookup"><span data-stu-id="7df16-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="7df16-181">接下來，向類型添加提供的靜態屬性：</span><span class="sxs-lookup"><span data-stu-id="7df16-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="7df16-182">獲取此屬性將始終評估到字串"你好！</span><span class="sxs-lookup"><span data-stu-id="7df16-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="7df16-183">屬性`GetterCode`使用 F# 引號，它表示主機編譯器為獲取該屬性而生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="7df16-184">有關報價單的詳細資訊，請參閱[代碼報價 （F#）。](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)</span><span class="sxs-lookup"><span data-stu-id="7df16-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="7df16-185">將 XML 文檔添加到屬性。</span><span class="sxs-lookup"><span data-stu-id="7df16-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="7df16-186">現在，將提供的屬性附加到提供的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="7df16-187">您必須將提供的成員附加到一種和僅一種類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="7df16-188">否則，該成員將永遠無法訪問。</span><span class="sxs-lookup"><span data-stu-id="7df16-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="7df16-189">現在創建一個不需要參數的提供的建構函式。</span><span class="sxs-lookup"><span data-stu-id="7df16-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="7df16-190">構造`InvokeCode`函數返回一個 F# 引號，它表示在調用建構函式時主機編譯器生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="7df16-191">例如，可以使用以下建構函式：</span><span class="sxs-lookup"><span data-stu-id="7df16-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="7df16-192">使用基礎資料"物件資料"創建提供的類型的實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="7df16-193">引號代碼包括轉換為[obj，](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型是此提供類型的擦除（如您聲明提供的類型時指定的）。</span><span class="sxs-lookup"><span data-stu-id="7df16-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="7df16-194">將 XML 文檔添加到建構函式，並將提供的建構函式添加到提供的類型：</span><span class="sxs-lookup"><span data-stu-id="7df16-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="7df16-195">創建第二個提供的建構函式，該建構函式採用一個參數：</span><span class="sxs-lookup"><span data-stu-id="7df16-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="7df16-196">構造`InvokeCode`函數的 引號再次返回一個 F# 引號，它表示主機編譯器為調用 方法生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="7df16-197">例如，可以使用以下建構函式：</span><span class="sxs-lookup"><span data-stu-id="7df16-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="7df16-198">使用基礎資料"10"創建提供的類型的實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="7df16-199">您可能已經注意到函數`InvokeCode`返回引號。</span><span class="sxs-lookup"><span data-stu-id="7df16-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="7df16-200">此函數的輸入是運算式清單，每個建構函式參數一個。</span><span class="sxs-lookup"><span data-stu-id="7df16-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="7df16-201">在這種情況下，表示單個參數值的運算式在 中`args.[0]`可用。</span><span class="sxs-lookup"><span data-stu-id="7df16-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="7df16-202">調用建構函式的代碼強制傳回值到擦除的類型`obj`。</span><span class="sxs-lookup"><span data-stu-id="7df16-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="7df16-203">將第二個提供的建構函式添加到類型後，將創建一個提供的實例屬性：</span><span class="sxs-lookup"><span data-stu-id="7df16-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="7df16-204">獲取此屬性將返回字串的長度，該長度是表示物件。</span><span class="sxs-lookup"><span data-stu-id="7df16-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="7df16-205">該`GetterCode`屬性返回一個 F# 引號，該引號指定主機編譯器為獲取該屬性而生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="7df16-206">與`InvokeCode`一`GetterCode`樣，函數返回引號。</span><span class="sxs-lookup"><span data-stu-id="7df16-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="7df16-207">主機編譯器使用參數清單調用此函數。</span><span class="sxs-lookup"><span data-stu-id="7df16-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="7df16-208">在這種情況下，參數僅包括表示調用 getter 的實例的單個運算式，您可以使用 訪問 該運算式`args.[0]`。</span><span class="sxs-lookup"><span data-stu-id="7df16-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="7df16-209">`GetterCode`然後在擦除類型`obj`中拼接到結果引號中的實現，以及強制轉換用於滿足編譯器檢查物件是字串的類型的機制。</span><span class="sxs-lookup"><span data-stu-id="7df16-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="7df16-210">的下`makeOneProvidedType`一部分提供了一個實例方法，其中有一個參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="7df16-211">最後，創建包含 100 個嵌套屬性的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="7df16-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="7df16-212">此巢狀型別的創建及其屬性延遲，即按需計算。</span><span class="sxs-lookup"><span data-stu-id="7df16-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="7df16-213">有關已擦除提供的類型的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7df16-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="7df16-214">本節中的示例僅提供*擦除的提供類型*，這些類型在以下情況下特別有用：</span><span class="sxs-lookup"><span data-stu-id="7df16-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="7df16-215">為僅包含資料和方法的資訊空間編寫提供程式時。</span><span class="sxs-lookup"><span data-stu-id="7df16-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="7df16-216">編寫提供程式時，準確運行時類型的語義對於實際使用資訊空間並不重要。</span><span class="sxs-lookup"><span data-stu-id="7df16-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="7df16-217">當您為資訊空間編寫提供程式時，該提供程式非常大且相互關聯，因此在技術上為資訊空間生成真正的 .NET 類型是不可行的。</span><span class="sxs-lookup"><span data-stu-id="7df16-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="7df16-218">在此示例中，每個提供的類型將擦除為類型`obj`，並且該類型的所有用途都將在編譯的代碼中顯示為類型`obj`。</span><span class="sxs-lookup"><span data-stu-id="7df16-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="7df16-219">事實上，這些示例中的基礎物件是字串，但類型將顯示為`System.Object`.NET 編譯代碼中。</span><span class="sxs-lookup"><span data-stu-id="7df16-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="7df16-220">與類型擦除的所有用途一樣，您可以使用顯式裝箱、取消裝箱和強制轉換來顛覆擦除的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="7df16-221">在這種情況下，當使用物件時，可能會出現不正確強制轉換異常。</span><span class="sxs-lookup"><span data-stu-id="7df16-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="7df16-222">提供程式運行時可以定義其自己的私有表示類型，以説明防止虛假陳述。</span><span class="sxs-lookup"><span data-stu-id="7df16-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="7df16-223">不能在 F# 本身中定義已擦除的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="7df16-224">只能擦除提供的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-224">Only provided types may be erased.</span></span> <span data-ttu-id="7df16-225">您必須瞭解為類型提供程式或提供擦除類型的提供程式使用擦除類型的後果（無論是實際的還是語義的）。</span><span class="sxs-lookup"><span data-stu-id="7df16-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="7df16-226">擦除的類型沒有實際的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="7df16-227">因此，您不能對類型進行準確反射，如果使用運行時強制轉換和其他依賴于精確運行時類型語義的技術，則可能會顛覆擦除的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="7df16-228">擦除類型的顛覆經常導致運行時的類型強制異常。</span><span class="sxs-lookup"><span data-stu-id="7df16-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="7df16-229">為已擦除的提供類型選擇表示形式</span><span class="sxs-lookup"><span data-stu-id="7df16-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="7df16-230">對於已擦除提供的類型的某些用途，不需要表示形式。</span><span class="sxs-lookup"><span data-stu-id="7df16-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="7df16-231">例如，擦除的提供類型可能僅包含靜態屬性和成員，並且不包含建構函式，並且任何方法或屬性都無法返回類型的實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="7df16-232">如果可以到達已擦除提供的類型的實例，則必須考慮以下問題：</span><span class="sxs-lookup"><span data-stu-id="7df16-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="7df16-233">**提供類型的擦除是什麼？**</span><span class="sxs-lookup"><span data-stu-id="7df16-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="7df16-234">提供類型的擦除是該類型在編譯的 .NET 代碼中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7df16-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="7df16-235">提供的擦除類類型的擦除始終是類型繼承鏈中的第一個未擦除基類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="7df16-236">提供的擦除介面類別型的擦除始終`System.Object`為 。</span><span class="sxs-lookup"><span data-stu-id="7df16-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="7df16-237">**提供的類型的表示形式是什麼？**</span><span class="sxs-lookup"><span data-stu-id="7df16-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="7df16-238">擦除提供的類型的可能物件的集稱為其表示形式。</span><span class="sxs-lookup"><span data-stu-id="7df16-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="7df16-239">在本文檔中的示例中，所有擦除提供的類型的`Type1..Type100`表示形式始終是字串物件。</span><span class="sxs-lookup"><span data-stu-id="7df16-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="7df16-240">提供類型的所有表示形式必須與提供的類型的擦除相容。</span><span class="sxs-lookup"><span data-stu-id="7df16-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="7df16-241">（否則，F# 編譯器將給出使用類型提供程式的錯誤，或者將生成不正確不可驗證的 .NET 代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="7df16-242">如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。</span><span class="sxs-lookup"><span data-stu-id="7df16-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="7df16-243">可以使用以下任一方法為提供的物件選擇表示形式，這兩種方法都很常見：</span><span class="sxs-lookup"><span data-stu-id="7df16-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="7df16-244">如果只是在現有 .NET 類型上提供強型別包裝，則類型通常可以擦除到該類型，使用該類型的實例作為表示，或者兩者兼而有之。</span><span class="sxs-lookup"><span data-stu-id="7df16-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="7df16-245">當使用強型別版本時，該類型上的大多數現有方法仍然有意義時，此方法是合適的。</span><span class="sxs-lookup"><span data-stu-id="7df16-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="7df16-246">如果要創建與任何現有 .NET API 有顯著差異的 API，則創建運行時類型是提供的類型擦除和表示形式，這是有道理的。</span><span class="sxs-lookup"><span data-stu-id="7df16-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="7df16-247">本文檔中的示例使用字串作為提供物件的表示形式。</span><span class="sxs-lookup"><span data-stu-id="7df16-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="7df16-248">通常，使用其他物件進行表示可能很合適。</span><span class="sxs-lookup"><span data-stu-id="7df16-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="7df16-249">例如，您可以將字典用作屬性包：</span><span class="sxs-lookup"><span data-stu-id="7df16-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="7df16-250">作為替代方法，您可以在類型提供程式中定義將在運行時用於形成表示的類型以及一個或多個運行時操作：</span><span class="sxs-lookup"><span data-stu-id="7df16-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="7df16-251">然後，如果成員可以構造此物件類型的實例：</span><span class="sxs-lookup"><span data-stu-id="7df16-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="7df16-252">在這種情況下，您可以（有選擇地）在構造 時`baseType``ProvidedTypeDefinition`將此類型指定為</span><span class="sxs-lookup"><span data-stu-id="7df16-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="7df16-253">重點課程</span><span class="sxs-lookup"><span data-stu-id="7df16-253">Key Lessons</span></span>

<span data-ttu-id="7df16-254">上一節介紹了如何創建一個簡單的解排類型提供程式，該提供程式提供一系列類型、屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="7df16-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="7df16-255">本節還解釋了類型擦除的概念，包括從類型提供程式提供擦除類型的一些優點和缺點，並討論了擦除類型的表示形式。</span><span class="sxs-lookup"><span data-stu-id="7df16-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="7df16-256">使用靜態參數的類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="7df16-257">通過靜態資料對類型提供程式進行參數化的能力支援許多有趣的方案，即使提供程式不需要訪問任何本地或遠端資料也是如此。</span><span class="sxs-lookup"><span data-stu-id="7df16-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="7df16-258">在本節中，您將學習一些組合此類提供程式的基本技術。</span><span class="sxs-lookup"><span data-stu-id="7df16-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="7df16-259">鍵入已檢查的正則運算式提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="7df16-260">假設您要為正則運算式實現類型提供程式，該正則運算式在提供以下編譯時間<xref:System.Text.RegularExpressions.Regex>保證的介面中包裝 .NET 庫：</span><span class="sxs-lookup"><span data-stu-id="7df16-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="7df16-261">驗證正則運算式是否有效。</span><span class="sxs-lookup"><span data-stu-id="7df16-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="7df16-262">在基於正則運算式中的任何組名稱的匹配項上提供命名屬性。</span><span class="sxs-lookup"><span data-stu-id="7df16-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="7df16-263">本節介紹如何使用類型提供程式創建`RegexTyped`正則運算式模式參數化類別型以提供這些好處。</span><span class="sxs-lookup"><span data-stu-id="7df16-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="7df16-264">如果提供的模式無效，編譯器將報告錯誤，並且類型提供程式可以從模式中提取組，以便可以使用匹配上的命名屬性訪問這些組。</span><span class="sxs-lookup"><span data-stu-id="7df16-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="7df16-265">在設計類型提供程式時，應考慮其公開的 API 應如何查看最終使用者，以及此設計將如何轉換為 .NET 代碼。</span><span class="sxs-lookup"><span data-stu-id="7df16-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="7df16-266">下面的示例演示如何使用此類 API 獲取區號元件：</span><span class="sxs-lookup"><span data-stu-id="7df16-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="7df16-267">下面的示例顯示了類型提供程式如何轉換這些調用：</span><span class="sxs-lookup"><span data-stu-id="7df16-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="7df16-268">請注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="7df16-268">Note the following points:</span></span>

- <span data-ttu-id="7df16-269">標準 Regex 類型表示參數化`RegexTyped`類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="7df16-270">構造`RegexTyped`函數會導致對 Regex 建構函式的調用，從而傳入模式的靜態類型參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="7df16-271">`Match`該方法的結果由標準<xref:System.Text.RegularExpressions.Match>類型表示。</span><span class="sxs-lookup"><span data-stu-id="7df16-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="7df16-272">每個命名組都會導致提供的屬性，訪問該屬性會導致在匹配的集合`Groups`上使用索引子。</span><span class="sxs-lookup"><span data-stu-id="7df16-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="7df16-273">以下代碼是實現此類提供程式的邏輯的核心，此示例省略了向提供的類型添加所有成員。</span><span class="sxs-lookup"><span data-stu-id="7df16-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="7df16-274">有關每個添加成員的資訊，請參閱本主題後面的相應部分。</span><span class="sxs-lookup"><span data-stu-id="7df16-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="7df16-275">有關完整代碼，請從 CodePlex 網站上的[F# 3.0 示例包](https://archive.codeplex.com/?p=fsharp3sample)下載示例。</span><span class="sxs-lookup"><span data-stu-id="7df16-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="7df16-276">請注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="7df16-276">Note the following points:</span></span>

- <span data-ttu-id="7df16-277">類型提供程式採用兩個靜態參數：`pattern`必填項和 可選的`options`。（因為提供了預設值）。</span><span class="sxs-lookup"><span data-stu-id="7df16-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="7df16-278">提供靜態參數後，將創建正則運算式的實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="7df16-279">如果 Regex 格式不正確，此實例將引發異常，並且此錯誤將報告給使用者。</span><span class="sxs-lookup"><span data-stu-id="7df16-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="7df16-280">在回檔`DefineStaticParameters`中，定義提供參數後將返回的類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="7df16-281">此代碼設置`HideObjectMethods`為 true，以便 IntelliSense 體驗將保持流線型。</span><span class="sxs-lookup"><span data-stu-id="7df16-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="7df16-282">此屬性會導致`Equals`從提供物件的`GetHashCode` `Finalize`IntelliSense 清單中禁止 、 和`GetType`成員。</span><span class="sxs-lookup"><span data-stu-id="7df16-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="7df16-283">使用作為`obj`方法的基礎類型，但您將使用`Regex`物件作為此類型的運行時表示形式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="7df16-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="7df16-284">當正則運算式`Regex`無效時，對<xref:System.ArgumentException>建構函式的調用將引發 。</span><span class="sxs-lookup"><span data-stu-id="7df16-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="7df16-285">編譯器捕獲此異常，並在編譯時或在 Visual Studio 編輯器中向使用者報告錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7df16-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="7df16-286">此異常允許在不運行應用程式的情況下驗證正則運算式。</span><span class="sxs-lookup"><span data-stu-id="7df16-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="7df16-287">上面定義的類型還不用，因為它不包含任何有意義的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="7df16-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="7df16-288">首先，添加靜態`IsMatch`方法：</span><span class="sxs-lookup"><span data-stu-id="7df16-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="7df16-289">前面的代碼定義一個方法`IsMatch`，該方法以字串作為輸入並返回 。 `bool`</span><span class="sxs-lookup"><span data-stu-id="7df16-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="7df16-290">唯一棘手的部分是在`args``InvokeCode`定義中使用參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="7df16-291">在此示例中，`args`是表示此方法的參數的報價單清單。</span><span class="sxs-lookup"><span data-stu-id="7df16-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="7df16-292">如果該方法是實例方法，則第一個參數表示參數`this`。</span><span class="sxs-lookup"><span data-stu-id="7df16-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="7df16-293">但是，對於靜態方法，參數都只是方法的顯式參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="7df16-294">請注意，引號值的類型應與指定的返回類型匹配（在本例中為`bool`）。</span><span class="sxs-lookup"><span data-stu-id="7df16-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="7df16-295">另請注意，此代碼使用`AddXmlDoc`方法可確保提供的方法也具有有用的文檔，您可以通過 IntelliSense 提供這些文檔。</span><span class="sxs-lookup"><span data-stu-id="7df16-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="7df16-296">接下來，添加實例匹配方法。</span><span class="sxs-lookup"><span data-stu-id="7df16-296">Next, add an instance Match method.</span></span> <span data-ttu-id="7df16-297">但是，此方法應返回提供的`Match`類型的值，以便以強型別方式訪問組。</span><span class="sxs-lookup"><span data-stu-id="7df16-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="7df16-298">因此，您首先聲明類型`Match`。</span><span class="sxs-lookup"><span data-stu-id="7df16-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="7df16-299">由於此類型取決於作為靜態參數提供的模式，因此此類型必須嵌套在參數化型別定義中：</span><span class="sxs-lookup"><span data-stu-id="7df16-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="7df16-300">然後，向每個組的"匹配"類型添加一個屬性。</span><span class="sxs-lookup"><span data-stu-id="7df16-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="7df16-301">在運行時，匹配表示為<xref:System.Text.RegularExpressions.Match>值，因此定義屬性的報價單必須使用<xref:System.Text.RegularExpressions.Match.Groups>索引屬性來獲取相關組。</span><span class="sxs-lookup"><span data-stu-id="7df16-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="7df16-302">同樣，請注意，您將 XML 文檔添加到提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="7df16-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="7df16-303">另請注意，如果提供了`GetterCode`函數，則可以讀取屬性，如果提供了`SetterCode`函數，則可以寫入該屬性，因此生成的屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="7df16-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="7df16-304">現在，您可以創建返回此`Match`類型值的實例方法：</span><span class="sxs-lookup"><span data-stu-id="7df16-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="7df16-305">因為您正在創建實例方法，表示`args.[0]`正在調用`RegexTyped`該方法的實例，並且`args.[1]`是輸入參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="7df16-306">最後，提供一個建構函式，以便可以創建提供類型的實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="7df16-307">建構函式僅擦除為創建標準 .NET Regex 實例，該實例再次盒裝到物件，因為`obj`是提供類型的擦除。</span><span class="sxs-lookup"><span data-stu-id="7df16-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="7df16-308">通過該更改，主題前面指定的示例 API 用法將按預期方式工作。</span><span class="sxs-lookup"><span data-stu-id="7df16-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="7df16-309">以下代碼已完成且最終：</span><span class="sxs-lookup"><span data-stu-id="7df16-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="7df16-310">重點課程</span><span class="sxs-lookup"><span data-stu-id="7df16-310">Key Lessons</span></span>

<span data-ttu-id="7df16-311">本節介紹如何創建對其靜態參數運行的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="7df16-312">提供程式檢查靜態參數，並根據其值提供操作。</span><span class="sxs-lookup"><span data-stu-id="7df16-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="7df16-313">由本地資料支援的類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="7df16-314">通常，您可能希望類型提供程式不僅基於靜態參數，還基於本地或遠端系統的資訊來顯示 API。</span><span class="sxs-lookup"><span data-stu-id="7df16-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="7df16-315">本節討論基於本地資料（如本地資料檔案）的類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="7df16-316">簡單的 CSV 檔提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-316">Simple CSV File Provider</span></span>

<span data-ttu-id="7df16-317">作為一個簡單的示例，請考慮一個類型提供程式，用於以逗號分隔值 （CSV） 格式訪問科學資料。</span><span class="sxs-lookup"><span data-stu-id="7df16-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="7df16-318">本節假定 CSV 檔包含標頭行，後跟浮點數據，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="7df16-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="7df16-319">距離（米）</span><span class="sxs-lookup"><span data-stu-id="7df16-319">Distance (meter)</span></span>|<span data-ttu-id="7df16-320">時間（秒）</span><span class="sxs-lookup"><span data-stu-id="7df16-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="7df16-321">50.0</span><span class="sxs-lookup"><span data-stu-id="7df16-321">50.0</span></span>|<span data-ttu-id="7df16-322">3.7</span><span class="sxs-lookup"><span data-stu-id="7df16-322">3.7</span></span>|
|<span data-ttu-id="7df16-323">100.0</span><span class="sxs-lookup"><span data-stu-id="7df16-323">100.0</span></span>|<span data-ttu-id="7df16-324">5.2</span><span class="sxs-lookup"><span data-stu-id="7df16-324">5.2</span></span>|
|<span data-ttu-id="7df16-325">150.0</span><span class="sxs-lookup"><span data-stu-id="7df16-325">150.0</span></span>|<span data-ttu-id="7df16-326">6.4</span><span class="sxs-lookup"><span data-stu-id="7df16-326">6.4</span></span>|

<span data-ttu-id="7df16-327">本節演示如何提供一種類型，可用於`Distance`獲取具有類型`float<meter>`屬性和類型的`Time``float<second>`屬性的行。</span><span class="sxs-lookup"><span data-stu-id="7df16-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="7df16-328">為簡單起見，我們做了以下假設：</span><span class="sxs-lookup"><span data-stu-id="7df16-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="7df16-329">標題名稱不是無單元的，或者有"名稱（單位）"的表單，並且不包含逗號。</span><span class="sxs-lookup"><span data-stu-id="7df16-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="7df16-330">單位均為[Microsoft.FSharp.Data.UnitSystems.SI.單元名稱模組 （F#）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義的系統國際 （SI） 單元。</span><span class="sxs-lookup"><span data-stu-id="7df16-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="7df16-331">單位都是簡單的（例如，儀錶），而不是複合的（例如，儀錶/秒）。</span><span class="sxs-lookup"><span data-stu-id="7df16-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="7df16-332">所有列都包含浮點數據。</span><span class="sxs-lookup"><span data-stu-id="7df16-332">All columns contain floating point data.</span></span>

<span data-ttu-id="7df16-333">更完整的供應商將放鬆這些限制。</span><span class="sxs-lookup"><span data-stu-id="7df16-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="7df16-334">同樣，第一步是考慮 API 的外觀。</span><span class="sxs-lookup"><span data-stu-id="7df16-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="7df16-335">假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="7df16-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="7df16-336">在這種情況下，編譯器應將這些調用轉換為類似以下示例的內容：</span><span class="sxs-lookup"><span data-stu-id="7df16-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="7df16-337">最佳轉換將要求類型提供程式在類型提供程式的程式集中定義`CsvFile`實際類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="7df16-338">類型提供程式通常依賴于一些説明器類型和方法來包裝重要邏輯。</span><span class="sxs-lookup"><span data-stu-id="7df16-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="7df16-339">由於度量值在運行時被擦除，因此可以使用 作為`float[]`行的擦除類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="7df16-340">編譯器將不同的列視為具有不同的度量數值型別。</span><span class="sxs-lookup"><span data-stu-id="7df16-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="7df16-341">例如，我們示例中的第一列具有類型`float<meter>`，第二列具有`float<second>`。</span><span class="sxs-lookup"><span data-stu-id="7df16-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="7df16-342">但是，擦除的表示形式可以保持非常簡單。</span><span class="sxs-lookup"><span data-stu-id="7df16-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="7df16-343">以下代碼顯示了實現的核心。</span><span class="sxs-lookup"><span data-stu-id="7df16-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="7df16-344">請注意有關實現的以下幾點：</span><span class="sxs-lookup"><span data-stu-id="7df16-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="7df16-345">重載建構函式允許讀取原始檔案或具有相同架構的檔。</span><span class="sxs-lookup"><span data-stu-id="7df16-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="7df16-346">當您為本地或遠端資料源編寫類型提供程式時，此模式很常見，並且此模式允許將本地檔用作遠端資料的範本。</span><span class="sxs-lookup"><span data-stu-id="7df16-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="7df16-347">您可以使用傳遞給類型提供程式建構函式的[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)值解析相對檔案名。</span><span class="sxs-lookup"><span data-stu-id="7df16-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="7df16-348">可以使用 方法`AddDefinitionLocation`定義提供的屬性的位置。</span><span class="sxs-lookup"><span data-stu-id="7df16-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="7df16-349">因此，如果您在提供的屬性`Go To Definition`上使用，CSV 檔將在 Visual Studio 中打開。</span><span class="sxs-lookup"><span data-stu-id="7df16-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="7df16-350">您可以使用 類型`ProvidedMeasureBuilder`查找 SI 單位並生成相關`float<_>`類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="7df16-351">重點課程</span><span class="sxs-lookup"><span data-stu-id="7df16-351">Key Lessons</span></span>

<span data-ttu-id="7df16-352">本節介紹如何使用資料來源本身中包含的簡單架構為本地資料來源創建類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="7df16-353">更進一步</span><span class="sxs-lookup"><span data-stu-id="7df16-353">Going Further</span></span>

<span data-ttu-id="7df16-354">以下各節包括進一步研究的建議。</span><span class="sxs-lookup"><span data-stu-id="7df16-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="7df16-355">查看已編譯的擦除類型代碼</span><span class="sxs-lookup"><span data-stu-id="7df16-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="7df16-356">為了讓您瞭解類型提供程式的使用如何與所發出的代碼相對應，請使用`HelloWorldTypeProvider`本主題前面使用的代碼來查看以下函數。</span><span class="sxs-lookup"><span data-stu-id="7df16-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="7df16-357">下面是使用 ildasm.exe 編譯的結果代碼的圖像：</span><span class="sxs-lookup"><span data-stu-id="7df16-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="7df16-358">如示例所示，所有提及的類型`Type1`和`InstanceProperty`屬性都已被刪除，僅保留有關運行時類型的操作。</span><span class="sxs-lookup"><span data-stu-id="7df16-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="7df16-359">類型提供程式的設計和命名約定</span><span class="sxs-lookup"><span data-stu-id="7df16-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="7df16-360">創作類型提供程式時，請遵守以下約定。</span><span class="sxs-lookup"><span data-stu-id="7df16-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="7df16-361">**連線協定的提供程式**通常，大多數提供程式 DlL 用於資料和服務連線協定（如 OData 或 SQL 連接）的名稱應以`TypeProvider``TypeProviders`或 結尾。</span><span class="sxs-lookup"><span data-stu-id="7df16-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="7df16-362">例如，使用類似于以下字串的 DLL 名稱：</span><span class="sxs-lookup"><span data-stu-id="7df16-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="7df16-363">確保您提供的類型是相應命名空間的成員，並指示您實現的連線協定：</span><span class="sxs-lookup"><span data-stu-id="7df16-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="7df16-364">**通用編碼提供程式**。</span><span class="sxs-lookup"><span data-stu-id="7df16-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="7df16-365">對於實用程式類型提供程式（如正則運算式提供程式），類型提供程式可能是基本庫的一部分，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="7df16-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="7df16-366">在這種情況下，根據正常的 .NET 設計約定，提供的類型將顯示在適當的點：</span><span class="sxs-lookup"><span data-stu-id="7df16-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="7df16-367">**單頓資料來源**.</span><span class="sxs-lookup"><span data-stu-id="7df16-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="7df16-368">某些類型提供程式連接到單個專用資料來源，並且僅提供資料。</span><span class="sxs-lookup"><span data-stu-id="7df16-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="7df16-369">在這種情況下，應刪除`TypeProvider`尾碼，並使用正常的約定進行 .NET 命名：</span><span class="sxs-lookup"><span data-stu-id="7df16-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="7df16-370">有關詳細資訊，請參閱本主題後面`GetConnection`介紹的設計約定。</span><span class="sxs-lookup"><span data-stu-id="7df16-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="7df16-371">類型提供程式的設計模式</span><span class="sxs-lookup"><span data-stu-id="7df16-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="7df16-372">以下各節介紹在創作類型提供程式時可以使用的設計模式。</span><span class="sxs-lookup"><span data-stu-id="7df16-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="7df16-373">獲取連接設計模式</span><span class="sxs-lookup"><span data-stu-id="7df16-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="7df16-374">大多數類型提供程式都應編寫用於使用 FSharp.Data.TypeProvider.dll 中類型提供程式使用的`GetConnection`模式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="7df16-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="7df16-375">由遠端資料和服務支援的類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="7df16-376">在創建由遠端資料和服務支援的類型提供程式之前，必須考慮連接程式設計中固有的一系列問題。</span><span class="sxs-lookup"><span data-stu-id="7df16-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="7df16-377">這些問題包括以下注意事項：</span><span class="sxs-lookup"><span data-stu-id="7df16-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="7df16-378">架構映射</span><span class="sxs-lookup"><span data-stu-id="7df16-378">schema mapping</span></span>

- <span data-ttu-id="7df16-379">存在架構更改時的即時性和失效性</span><span class="sxs-lookup"><span data-stu-id="7df16-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="7df16-380">架構緩存</span><span class="sxs-lookup"><span data-stu-id="7df16-380">schema caching</span></span>

- <span data-ttu-id="7df16-381">資料訪問操作的非同步實現</span><span class="sxs-lookup"><span data-stu-id="7df16-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="7df16-382">支援查詢，包括 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="7df16-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="7df16-383">憑據和身份驗證</span><span class="sxs-lookup"><span data-stu-id="7df16-383">credentials and authentication</span></span>

<span data-ttu-id="7df16-384">本主題沒有進一步探討這些問題。</span><span class="sxs-lookup"><span data-stu-id="7df16-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="7df16-385">其他創作技術</span><span class="sxs-lookup"><span data-stu-id="7df16-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="7df16-386">編寫自己的類型提供程式時，可能需要使用以下附加技術。</span><span class="sxs-lookup"><span data-stu-id="7df16-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="7df16-387">按需創建類型和成員</span><span class="sxs-lookup"><span data-stu-id="7df16-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="7df16-388">提供類型 API 已延遲添加成員版本。</span><span class="sxs-lookup"><span data-stu-id="7df16-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="7df16-389">這些版本用於創建類型的按需空間。</span><span class="sxs-lookup"><span data-stu-id="7df16-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="7df16-390">提供陣列類型和通用類型具現化</span><span class="sxs-lookup"><span data-stu-id="7df16-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="7df16-391">通過使用`MakeArrayType`法線 和`MakePointerType`的任何`MakeGenericType`實例<xref:System.Type>（包括`ProvidedTypeDefinitions`） 使提供的成員（其簽名包括陣列類型、byref 類型和泛型型別的實例）。</span><span class="sxs-lookup"><span data-stu-id="7df16-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="7df16-392">在某些情況下，您可能需要在 中使用`ProvidedTypeBuilder.MakeGenericType`協助程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="7df16-393">有關詳細資訊，請參閱[類型提供程式 SDK 文檔](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)。</span><span class="sxs-lookup"><span data-stu-id="7df16-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="7df16-394">提供度量單位注釋</span><span class="sxs-lookup"><span data-stu-id="7df16-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="7df16-395">提供類型 API 提供用於提供度量值注釋的説明器。</span><span class="sxs-lookup"><span data-stu-id="7df16-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="7df16-396">例如，要提供類型`float<kg>`，請使用以下代碼：</span><span class="sxs-lookup"><span data-stu-id="7df16-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="7df16-397">要提供類型`Nullable<decimal<kg/m^2>>`，請使用以下代碼：</span><span class="sxs-lookup"><span data-stu-id="7df16-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="7df16-398">訪問專案-本地資源或腳本本地資源</span><span class="sxs-lookup"><span data-stu-id="7df16-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="7df16-399">類型提供程式的每個實例都可以在構造期間給出一`TypeProviderConfig`個值。</span><span class="sxs-lookup"><span data-stu-id="7df16-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="7df16-400">此值包含提供程式的"解析資料夾"（即編譯的專案資料夾或包含腳本的目錄）、引用程式集的清單和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="7df16-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="7df16-401">失效</span><span class="sxs-lookup"><span data-stu-id="7df16-401">Invalidation</span></span>

<span data-ttu-id="7df16-402">提供程式可以引發失效信號，以通知 F# 語言服務架構假設可能已更改。</span><span class="sxs-lookup"><span data-stu-id="7df16-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="7df16-403">當發生失效時，如果提供程式在 Visual Studio 中託管，則重新檢查類型檢查。</span><span class="sxs-lookup"><span data-stu-id="7df16-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="7df16-404">當提供程式託管在 F# 互動式或 F# 編譯器 （fsc.exe） 中時，將忽略此信號。</span><span class="sxs-lookup"><span data-stu-id="7df16-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="7df16-405">緩存架構資訊</span><span class="sxs-lookup"><span data-stu-id="7df16-405">Caching Schema Information</span></span>

<span data-ttu-id="7df16-406">提供程式必須經常緩存對架構資訊的訪問。</span><span class="sxs-lookup"><span data-stu-id="7df16-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="7df16-407">緩存的資料應使用作為靜態參數或使用者資料給出的檔案名進行存儲。</span><span class="sxs-lookup"><span data-stu-id="7df16-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="7df16-408">架構緩存的一個示例是`LocalSchemaFile``FSharp.Data.TypeProviders`程式集類型提供程式中的參數。</span><span class="sxs-lookup"><span data-stu-id="7df16-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="7df16-409">在實現這些提供程式時，此靜態參數指示類型提供程式在指定的本地檔中使用架構資訊，而不是通過網路訪問資料來源。</span><span class="sxs-lookup"><span data-stu-id="7df16-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="7df16-410">要使用緩存的架構資訊，還必須將靜態參數`ForceUpdate`設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="7df16-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="7df16-411">您可以使用類似的技術來啟用連線和離線資料訪問。</span><span class="sxs-lookup"><span data-stu-id="7df16-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="7df16-412">支援程式集</span><span class="sxs-lookup"><span data-stu-id="7df16-412">Backing Assembly</span></span>

<span data-ttu-id="7df16-413">編譯`.dll`或`.exe`檔時，生成的類型的備份 .DLL 檔案將靜態連結到生成的程式集中。</span><span class="sxs-lookup"><span data-stu-id="7df16-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="7df16-414">此連結是通過將中間語言 （IL） 類型定義和任何託管資源從備份程式集複製到最終程式集來創建的。</span><span class="sxs-lookup"><span data-stu-id="7df16-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="7df16-415">使用 F# 互動式時，不會複製支援 .DLL 檔案，而是直接載入到 F# 互動式進程中。</span><span class="sxs-lookup"><span data-stu-id="7df16-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="7df16-416">來自類型提供程式的異常和診斷</span><span class="sxs-lookup"><span data-stu-id="7df16-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="7df16-417">提供類型中所有成員的所有使用都可能會引發異常。</span><span class="sxs-lookup"><span data-stu-id="7df16-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="7df16-418">在所有情況下，如果類型提供程式引發異常，主機編譯器將錯誤屬性歸因於特定類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="7df16-419">類型提供程式異常不應導致內部編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7df16-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="7df16-420">類型提供程式無法報告警告。</span><span class="sxs-lookup"><span data-stu-id="7df16-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="7df16-421">當類型提供程式託管在 F# 編譯器、F# 開發環境或 F# 互動式中時，將捕獲該提供程式的所有異常。</span><span class="sxs-lookup"><span data-stu-id="7df16-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="7df16-422">消息屬性始終是錯誤文本，並且不顯示堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="7df16-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="7df16-423">如果要引發異常，可以引發以下示例： `System.NotSupportedException`、 `System.IO.IOException`。 `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="7df16-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="7df16-424">提供生成的類型</span><span class="sxs-lookup"><span data-stu-id="7df16-424">Providing Generated Types</span></span>

<span data-ttu-id="7df16-425">到目前為止，本文檔已解釋如何提供擦除類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="7df16-426">您還可以使用 F# 中的類型提供程式機制提供生成的類型，這些類型將作為真正的 .NET 類型定義添加到使用者的程式中。</span><span class="sxs-lookup"><span data-stu-id="7df16-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="7df16-427">您必須使用類型定義來引用生成的提供類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="7df16-428">作為 F# 3.0 版本的一部分的"提供類型-0.2 説明器"代碼對提供生成的類型的支援有限。</span><span class="sxs-lookup"><span data-stu-id="7df16-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="7df16-429">對於生成的類型定義，以下語句必須為 true：</span><span class="sxs-lookup"><span data-stu-id="7df16-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="7df16-430">`isErased` 必須設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7df16-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="7df16-431">生成的類型必須添加到新構造`ProvidedAssembly()`的 ，該類型表示生成的代碼片段的容器。</span><span class="sxs-lookup"><span data-stu-id="7df16-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="7df16-432">提供程式必須具有具有實際支援 .NET .DLL 檔案的程式集，該檔在磁片上具有匹配的 .DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="7df16-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="7df16-433">規則和限制</span><span class="sxs-lookup"><span data-stu-id="7df16-433">Rules and Limitations</span></span>

<span data-ttu-id="7df16-434">編寫類型提供程式時，請記住以下規則和限制。</span><span class="sxs-lookup"><span data-stu-id="7df16-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="7df16-435">提供的類型必須可到達</span><span class="sxs-lookup"><span data-stu-id="7df16-435">Provided types must be reachable</span></span>

<span data-ttu-id="7df16-436">所有提供的類型都應從非巢狀型別中進行。</span><span class="sxs-lookup"><span data-stu-id="7df16-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="7df16-437">非巢狀型別在對`TypeProviderForNamespaces`建構函式的調用或對`AddNamespace`的調用中給出。</span><span class="sxs-lookup"><span data-stu-id="7df16-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="7df16-438">例如，如果提供程式提供類型`StaticClass.P : T`，則必須確保 T 是非巢狀型別或嵌套在一個類型下。</span><span class="sxs-lookup"><span data-stu-id="7df16-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="7df16-439">例如，某些提供程式具有包含這些`DataTypes``T1, T2, T3, ...`類型的靜態類。</span><span class="sxs-lookup"><span data-stu-id="7df16-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="7df16-440">否則，錯誤表示在程式集 A 中找到對類型 T 的引用，但在該程式集中找不到該類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="7df16-441">如果出現此錯誤，請驗證可以從提供程式類型中到達所有子類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="7df16-442">注意：這些`T1, T2, T3...`類型稱為*動態*類型。</span><span class="sxs-lookup"><span data-stu-id="7df16-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="7df16-443">請記住將它們放在可訪問的命名空間或父類型中。</span><span class="sxs-lookup"><span data-stu-id="7df16-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="7df16-444">類型提供程式機制的限制</span><span class="sxs-lookup"><span data-stu-id="7df16-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="7df16-445">F# 中的類型提供程式機制具有以下限制：</span><span class="sxs-lookup"><span data-stu-id="7df16-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="7df16-446">F# 中類型提供程式的基礎基礎結構不支援提供泛型型別或提供泛型方法。</span><span class="sxs-lookup"><span data-stu-id="7df16-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="7df16-447">該機制不支援具有靜態參數的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="7df16-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="7df16-448">開發秘訣</span><span class="sxs-lookup"><span data-stu-id="7df16-448">Development Tips</span></span>

<span data-ttu-id="7df16-449">您可能會發現以下提示在開發過程中很有説明：</span><span class="sxs-lookup"><span data-stu-id="7df16-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="7df16-450">運行視覺化工作室的兩個實例</span><span class="sxs-lookup"><span data-stu-id="7df16-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="7df16-451">您可以在一個實例中開發類型提供程式，並在另一個實例中測試提供程式，因為測試 IDE 將對 .DLL 檔案進行鎖定，以防止重新組建類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="7df16-452">因此，在第一個實例中生成提供程式時，必須關閉 Visual Studio 的第二個實例，然後在構建提供程式後重新打開第二個實例。</span><span class="sxs-lookup"><span data-stu-id="7df16-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="7df16-453">使用 fsc.exe 調用調試類型提供程式</span><span class="sxs-lookup"><span data-stu-id="7df16-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="7df16-454">您可以使用以下工具調用類型提供程式：</span><span class="sxs-lookup"><span data-stu-id="7df16-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="7df16-455">fsc.exe（F# 命令列編譯器）</span><span class="sxs-lookup"><span data-stu-id="7df16-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="7df16-456">fsi.exe（F# 互動式編譯器）</span><span class="sxs-lookup"><span data-stu-id="7df16-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="7df16-457">德文夫.exe（視覺工作室）</span><span class="sxs-lookup"><span data-stu-id="7df16-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="7df16-458">通常，通過在測試指令檔（例如，腳本.fsx）上使用 fsc.exe，您通常最容易調試類型提供程式。</span><span class="sxs-lookup"><span data-stu-id="7df16-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="7df16-459">可以從命令提示符啟動調試器。</span><span class="sxs-lookup"><span data-stu-id="7df16-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="7df16-460">您可以使用列印到列印的日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="7df16-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="7df16-461">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df16-461">See also</span></span>

- [<span data-ttu-id="7df16-462">類型提供者</span><span class="sxs-lookup"><span data-stu-id="7df16-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="7df16-463">類型提供程式 SDK</span><span class="sxs-lookup"><span data-stu-id="7df16-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
