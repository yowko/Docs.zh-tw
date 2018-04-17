---
title: '教學課程： 建立型別提供者 （F #）'
description: '了解如何在 F # 3.0 中建立您自己 F # 類型提供者，藉由檢查幾個簡單的型別提供者，來說明基本的概念。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: b2e83218184bd1aef8258378485b99697cc8cf8d
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="e6c1c-104">教學課程： 建立型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-104">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="e6c1c-105">F # 中的型別提供者機制是其支援資訊豐富程式設計的重要部分。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-105">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="e6c1c-106">本教學課程說明如何建立您自己的型別提供者帶您逐步說明的基本概念的幾個簡單的型別提供者的開發。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-106">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="e6c1c-107">如需在 F # 類型提供者機制的詳細資訊，請參閱[型別提供者](index.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-107">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="e6c1c-108">F # 生態系統包含常用的網際網路和企業資料服務的型別提供者的範圍。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-108">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="e6c1c-109">例如: </span><span class="sxs-lookup"><span data-stu-id="e6c1c-109">For example:</span></span>

- <span data-ttu-id="e6c1c-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/)包含型別提供者的 JSON、 XML、 CSV 及 HTML 文件格式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="e6c1c-111">[根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)提供強型別存取 SQL 資料庫，透過物件對應和 F # LINQ 查詢對這些資料來源。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="e6c1c-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)一組型別提供者的編譯時間檢查 T-SQL F # 中的內嵌。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="e6c1c-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)較舊型別提供者存取 SQL、 Entity Framework、 OData 和 WSDL 資料服務的.NET Framework 程式設計只能搭配使用的設定。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="e6c1c-114">在需要時，您可以建立自訂型別提供者，或您可以參考其他人所建立的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-114">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="e6c1c-115">例如，您的組織可能會有提供大量且不斷增加的具名資料集，每個都有自己的穩定資料結構描述的資料服務。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-115">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="e6c1c-116">您可以建立型別提供者，讀取結構描述，並對程式設計人員呈現目前資料集，強類型方式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-116">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="e6c1c-117">在開始之前</span><span class="sxs-lookup"><span data-stu-id="e6c1c-117">Before You Start</span></span>

<span data-ttu-id="e6c1c-118">型別提供者機制主要設計使注入穩定資料和服務的資訊空間 F # 程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-118">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="e6c1c-119">這項機制不被設計用於將資訊與程式邏輯的方式在程式執行期間變更其結構描述的空間。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-119">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="e6c1c-120">此外，機制不被設計為內部語言中繼程式設計，即使該網域包含一些有效的用法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-120">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="e6c1c-121">只有在需要時，您應該使用這項機制，其中的型別提供者開發會產生非常高的值。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-121">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="e6c1c-122">您應該避免撰寫結構描述不可以是型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-122">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="e6c1c-123">同樣地，您應該避免使用一般 （或甚至現有） 撰寫型別提供者.NET 程式庫即已足夠。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-123">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="e6c1c-124">開始之前，您可能會詢問下列問題：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-124">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="e6c1c-125">您是否有結構描述資訊來源？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-125">Do you have a schema for your information source?</span></span> <span data-ttu-id="e6c1c-126">如果是這樣，F # 和.NET 類型系統對應為何？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-126">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="e6c1c-127">可以使用現有的 （動態具型別） API 作為的起始點實作？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-127">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="e6c1c-128">將您和貴組織有不足，無法使用型別提供者進行寫入的含意有其價值？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-128">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="e6c1c-129">一般的.NET 程式庫會符合您的需求？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-129">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="e6c1c-130">多少會變更您的結構描述？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-130">How much will your schema change?</span></span>

- <span data-ttu-id="e6c1c-131">它會在撰寫程式碼變更嗎？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-131">Will it change during coding?</span></span>

- <span data-ttu-id="e6c1c-132">它會變更程式碼撰寫工作階段之間嗎？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-132">Will it change between coding sessions?</span></span>

- <span data-ttu-id="e6c1c-133">它會在程式執行期間變更嗎？</span><span class="sxs-lookup"><span data-stu-id="e6c1c-133">Will it change during program execution?</span></span>

<span data-ttu-id="e6c1c-134">型別提供者最適合的情況下的結構描述在執行階段和編譯的程式碼的存留期間穩定。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-134">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="e6c1c-135">簡單的型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-135">A Simple Type Provider</span></span>

<span data-ttu-id="e6c1c-136">這個範例是中的範例類似 Samples.HelloWorldTypeProvider`examples`目錄[F # 類型提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-136">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="e6c1c-137">提供者可提供 「 型別空間 」 含有 100 刪除的類型為下列程式碼顯示使用 F # 簽章語法並省略以外的所有詳細資料的`Type1`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-137">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="e6c1c-138">如需清除類型的詳細資訊，請參閱[詳細資料的相關清除提供型別](#details-about-erased-provided-types)本主題稍後。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-138">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

    /// This is an instance property.
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

<span data-ttu-id="e6c1c-139">請注意，型別和成員提供一組以靜態方式知道。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-139">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="e6c1c-140">此範例不會利用提供者能夠提供取決於結構描述的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-140">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="e6c1c-141">下列程式碼，所述的型別提供者實作和詳細資料會包含在本主題稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-141">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="e6c1c-142">可能有這段程式碼和線上範例之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-142">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="e6c1c-143">若要使用此提供者，開啟 Visual Studio 的個別執行個體、 建立 F # 指令碼，然後再將從指令碼提供者的參考 #r 使用下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-143">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="e6c1c-144">然後尋找下類型`Samples.HelloWorldTypeProvider`型別提供者產生的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-144">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="e6c1c-145">您重新編譯提供者之前，請確定您已關閉所有執行個體的 Visual Studio 和 F # Interactive 會使用提供者 DLL。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-145">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="e6c1c-146">否則，因為輸出 DLL 將會遭到鎖定，會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-146">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="e6c1c-147">若要使用 print 陳述式，偵錯此提供者，讓指令碼會公開提供者，有問題，然後使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-147">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="e6c1c-148">若要使用 Visual Studio 偵錯此提供者、 系統管理認證，以開啟 Visual Studio 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-148">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="e6c1c-149">或者，開啟 Visual Studio，開啟 偵錯 功能表，選擇`Debug/Attach to process…`，並附加至另一個`devenv`就可以在其中編輯指令碼的程序。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-149">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="e6c1c-150">使用此方法，您可以更輕鬆地以互動方式 （具有完整的 IntelliSense 和其他功能） 的第二個執行個體中輸入運算式目標型別提供者中的特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-150">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="e6c1c-151">您可以停用 Just My Code 偵錯更容易辨識產生的程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-151">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="e6c1c-152">如需如何啟用或停用此功能的資訊，請參閱[使用偵錯工具巡覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-152">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="e6c1c-153">此外，您也可以設定 first-chance 例外狀況來攔截開啟`Debug`功能表，然後選擇`Exceptions`或選擇 Ctrl + Alt + E 鍵以開啟`Exceptions` 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-153">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="e6c1c-154">在對話方塊中，在`Common Language Runtime Exceptions`，選取`Thrown`核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-154">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="e6c1c-155">型別提供者實作</span><span class="sxs-lookup"><span data-stu-id="e6c1c-155">Implementation of the Type Provider</span></span>

<span data-ttu-id="e6c1c-156">本節將引導您透過型別提供者實作的主要區段。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-156">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="e6c1c-157">首先，您可以定義類型的自訂型別提供者本身：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-157">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="e6c1c-158">此類型必須是公用的以及您必須將它與[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性，讓個別的 F # 專案參考組件包含的型別時，編譯器會辨識型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-158">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="e6c1c-159">*Config*參數為選擇性，而且，如果有的話，包含 F # 編譯器會建立型別提供者執行個體的內容相關的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-159">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="e6c1c-160">接下來，您實作[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-160">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="e6c1c-161">在此情況下，您使用`TypeProviderForNamespaces`從`ProvidedTypes`應用程式開發介面的基底類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-161">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="e6c1c-162">此協助程式類型可以立即提供有限的集合，提供命名空間，其中每個直接包含有限的固定，立即提供型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-162">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="e6c1c-163">在此內容中，提供者*熱切*產生型別，即使它們不需要或使用。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-163">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="e6c1c-164">接下來，定義本機私用的值，指定的命名空間提供的類型，並尋找型別提供者組件本身。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-164">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="e6c1c-165">這個組件稍後會使用所提供的清除類型的邏輯父型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-165">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="e6c1c-166">接下來，建立函數，以提供每種類型的類型 1...Type100。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-166">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="e6c1c-167">在本主題稍後的更詳細地說明此函式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-167">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="e6c1c-168">接下來，產生 100 提供的類型：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-168">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="e6c1c-169">接下來，加入類型為提供的命名空間：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-169">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="e6c1c-170">最後，加入組件的屬性，指出您要建立型別提供者 DLL:</span><span class="sxs-lookup"><span data-stu-id="e6c1c-170">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="e6c1c-171">提供一個型別和成員</span><span class="sxs-lookup"><span data-stu-id="e6c1c-171">Providing One Type And Its Members</span></span>

<span data-ttu-id="e6c1c-172">`makeOneProvidedType`函式會提供一種類型的實際工作。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-172">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="e6c1c-173">此步驟說明此函式的實作。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-173">This step explains the implementation of this function.</span></span> <span data-ttu-id="e6c1c-174">首先，建立將提供的類型 (類型 1，例如當 n = 1 或 Type57，當 n = 57)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-174">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="e6c1c-175">您應該注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-175">You should note the following points:</span></span>

- <span data-ttu-id="e6c1c-176">這提供型別會被清除。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-176">This provided type is erased.</span></span>  <span data-ttu-id="e6c1c-177">因為您指出基底型別為`obj`，執行個體將會顯示類型的值為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)中編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-177">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="e6c1c-178">當您指定的非巢狀類型時，您必須指定組件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-178">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="e6c1c-179">對於清除類型，應該將組件類型提供者組件本身。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-179">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="e6c1c-180">接下來，將 XML 文件集加入至類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-180">Next, add XML documentation to the type.</span></span> <span data-ttu-id="e6c1c-181">這份文件會延遲，也就是，計算指定，如果主機編譯器需要它。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-181">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="e6c1c-182">接下來將提供的靜態屬性加入至類型中：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-182">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="e6c1c-183">取得這個屬性永遠會評估為字串"Hello ！"。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-183">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="e6c1c-184">`GetterCode`屬性使用 F # 引號，代表主機編譯器產生的取得此屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-184">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="e6c1c-185">如需有關引號的詳細資訊，請參閱[程式碼引號 （F #）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-185">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="e6c1c-186">將 XML 文件集加入至屬性。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-186">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="e6c1c-187">現在將所提供的屬性附加至提供的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-187">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="e6c1c-188">您必須將提供的成員連接只能有一個型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-188">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="e6c1c-189">否則，成員將永遠不會成為可存取。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-189">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="e6c1c-190">現在建立提供的建構函式不接受參數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-190">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="e6c1c-191">`InvokeCode`的建構函式會傳回 F # 引號，代表呼叫建構函式時，主機編譯器產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-191">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="e6c1c-192">例如，您可以使用下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-192">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="e6c1c-193">提供類型的執行個體將會建立與基礎資料 「 物件資料 」。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-193">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="e6c1c-194">加上引號的程式碼包含的轉換[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型的清除提供此型別 （如您宣告時，指定您提供的型別）。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-194">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="e6c1c-195">將 XML 文件集加入至建構函式，並提供建構函式加入至提供的類型：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-195">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="e6c1c-196">建立的第二個提供建構函式會接受一個參數：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-196">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="e6c1c-197">`InvokeCode`的建構函式會再次傳回 F # 引號，代表主機編譯器產生的方法呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-197">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="e6c1c-198">例如，您可以使用下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-198">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="e6c1c-199">與基礎資料 「 10 」 建立所提供的型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-199">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="e6c1c-200">您可能已經注意到，`InvokeCode`函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-200">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="e6c1c-201">此函式的輸入是運算式，其中每個建構函式參數的清單。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-201">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="e6c1c-202">在此案例中，代表單一參數值的運算式是用於`args.[0]`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-202">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="e6c1c-203">建構函式呼叫的程式碼強制清除類型傳回值`obj`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-203">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="e6c1c-204">新增第二個提供的建構函式類型之後，您會建立提供的執行個體屬性：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-204">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="e6c1c-205">取得這個屬性會傳回字串，即表示物件的長度。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-205">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="e6c1c-206">`GetterCode`屬性會傳回 F # 引號，指定要取得屬性的主機編譯器產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-206">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="e6c1c-207">像`InvokeCode`、`GetterCode`函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-207">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="e6c1c-208">主機編譯器會呼叫此函式的引數清單。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-208">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="e6c1c-209">在此案例中的引數包括只單一運算式表示之執行個體的 getter 被呼叫時，您可以使用存取`args.[0]`。實作`GetterCode`然後 splices 結果引號，在清除類型到`obj`，以及用來滿足編譯器的機制，檢查此物件是字串類型轉換。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-209">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="e6c1c-210">下一個部分`makeOneProvidedType`提供一個參數的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="e6c1c-211">最後，建立巢狀的類型，其中包含 100 個巢狀的屬性。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="e6c1c-212">這個建立巢狀類型和其屬性將會延遲，也就是，計算隨。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () -> 
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () -> 
    let staticPropsInNestedType = 
      [ for i in 1 .. 100 do
          let valueOfTheProperty = "I am string "  + string i

          let p = 
            ProvidedProperty(propertyName = "StaticProperty" + string i, 
              propertyType = typeof<string>, 
              isStatic = true,
              getterCode= (fun args -> <@@ valueOfTheProperty @@>))

          p.AddXmlDocDelayed(fun () -> 
              sprintf "This is StaticProperty%d on NestedType" i)

          yield p ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="e6c1c-213">清除之提供類型有關的詳細資料</span><span class="sxs-lookup"><span data-stu-id="e6c1c-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="e6c1c-214">本節中的範例僅提供*清除提供的類型*，這是在下列情況中特別有用：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="e6c1c-215">當您要撰寫的提供者只包含資料和方法的資訊空間。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="e6c1c-216">當您要撰寫精確的執行階段型別語意不重要的資訊空間的實際用途是提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="e6c1c-217">當您要撰寫的提供者的資訊空間，所以大型且相互連結，它不會產生實際的.NET 型別資訊空間就技術上而言可行。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="e6c1c-218">在此範例中，提供的每一個型別會清除輸入`obj`，所有使用型別將會都顯示為型別和`obj`中編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="e6c1c-219">事實上，在這些範例中的基礎物件是字串，但類型將會顯示為`System.Object`.net 編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="e6c1c-220">所有使用的類型清除，您可以使用明確的 boxing，unboxing，以及轉型至破壞清除類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="e6c1c-221">在此情況下，使用物件時，可能會造成不是有效的轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="e6c1c-222">提供者執行階段可以定義自己的私用的表示法型別，以協助防範 false 表示相互轉換。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="e6c1c-223">您無法在 F # 本身中定義它們的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="e6c1c-224">提供的類型可能會被清除。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-224">Only provided types may be erased.</span></span> <span data-ttu-id="e6c1c-225">您必須了解後果，這兩個實際會加以語意，請使用清除您的型別提供者或提供的提供者的類型清除類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="e6c1c-226">清除的型別並沒有實際的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="e6c1c-227">因此，精準反映無法掌控型別，而且如果您使用執行階段轉換和其他技術，依賴確實執行階段的類型語意，您可能會破壞清除的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="e6c1c-228">清除型別的 subversion 經常會導致在執行階段類型轉型例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="e6c1c-229">選擇表示法的清除提供型別</span><span class="sxs-lookup"><span data-stu-id="e6c1c-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="e6c1c-230">至於清除之提供類型的一些用法，不表示法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="e6c1c-231">例如，清除提供型別可能會包含靜態屬性及成員及任何建構函式，而沒有方法或屬性會傳回類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="e6c1c-232">如果您可以連線的清除執行個體提供之類型，您必須考慮下列問題：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="e6c1c-233">**清除所提供的型別是什麼？**</span><span class="sxs-lookup"><span data-stu-id="e6c1c-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="e6c1c-234">清除所提供的型別是型別如何出現在已編譯的.NET 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="e6c1c-235">提供的清除的類別類型的清除永遠是第一個非清除基底類型繼承鏈結中的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="e6c1c-236">提供的清除的介面型別的清除永遠是`System.Object`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="e6c1c-237">**所提供之類型的表示是什麼？**</span><span class="sxs-lookup"><span data-stu-id="e6c1c-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="e6c1c-238">一組可能的清除提供之類型的物件會呼叫其表示法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="e6c1c-239">在本文範例中，類型的所有清除提供表示`Type1..Type100`一定是字串的物件。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="e6c1c-240">提供之類型的所有表示都必須與所提供的型別清除相容。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="e6c1c-241">（否則 F # 編譯器會產生錯誤的型別提供者，使用或將會產生無法驗證.NET 程式碼並不是有效的。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="e6c1c-242">如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="e6c1c-243">您可以使用下列方法，兩者都是很常見的選擇提供物件的表示法：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="e6c1c-244">如果您只透過現有的.NET 型別提供強類型包裝函式，很合理的清除為該類型，為表示法，或兩者都使用該類型的執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="e6c1c-245">當現有的方法，該型別上的大部分仍能呼應使用強類型的版本時，這個方法是適當。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="e6c1c-246">如果您想要從任何現有的.NET API 大幅建立不同的 API，因此才會建立執行階段類型將會針對提供的類型與類型清除。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="e6c1c-247">這份文件中的範例會使用所提供之物件的表示為字串。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="e6c1c-248">通常，它可能適合使用其他物件，用於表示法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="e6c1c-249">例如，您可能會使用字典當做屬性包：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="e6c1c-250">或者，您可能會在您將在執行階段用來形成的表示法，以及一或多個執行階段作業的型別提供者定義類型：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="e6c1c-251">提供的成員然後可以建構此物件類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="e6c1c-252">在此情況下，您可能會 （選擇性） 使用此類型的類型清除為藉由指定此類型為`baseType`建構時`ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="e6c1c-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="e6c1c-253">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="e6c1c-253">Key Lessons</span></span>

<span data-ttu-id="e6c1c-254">上一節將說明如何建立簡單清除型別提供者提供了各式各樣的型別、 屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="e6c1c-255">本章節也說明的概念的類型清除，包括一些優點和缺點從型別提供者，提供它們的型別，並討論清除類型表示法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="e6c1c-256">使用靜態參數的型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="e6c1c-257">參數化的靜態資料的型別提供者的能力可讓許多有趣的情況下，即使在提供者不需要存取的任何本機或遠端資料時的情況下。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="e6c1c-258">在本節中，您將學習一些基本技術搭配使用這類提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="e6c1c-259">檢查 Regex 提供者類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="e6c1c-260">假設您想要實作規則運算式的型別提供者所包裝之.NET<xref:System.Text.RegularExpressions.Regex>文件庫中的介面會提供下列編譯時間保證：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="e6c1c-261">正在驗證是否為有效的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="e6c1c-262">提供具名的屬性比對規則運算式中的任何群組名稱為基礎。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="e6c1c-263">本節示範如何使用型別提供者來建立`RegexTyped`輸入規則運算式模式化為提供這些優點。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="e6c1c-264">如果提供的模式不是有效的而且型別提供者可以擷取的群組模式中，讓您可以使用名為相符項目上的屬性來存取它們，則編譯器會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="e6c1c-265">當您設計的類型提供者時，您應該考慮其公開的 API 的外觀以一般使用者與此設計會轉譯成.NET 程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="e6c1c-266">下列範例會示範如何使用這類 API 來取得區域程式碼的元件：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="e6c1c-267">下列範例會示範型別提供者將這些呼叫的轉譯：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="e6c1c-268">請注意下列重點：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-268">Note the following points:</span></span>

- <span data-ttu-id="e6c1c-269">標準的 Regex 型別代表參數化`RegexTyped`型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="e6c1c-270">`RegexTyped`建構函式會導致 Regex 建構函式呼叫，在模式比對的靜態型別引數中傳遞。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="e6c1c-271">結果`Match`方法都由標準<xref:System.Text.RegularExpressions.Match>型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="e6c1c-272">每個具名的群組導致所提供的屬性，並存取屬性導致系統使用的相符項目上的索引子的`Groups`集合。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="e6c1c-273">下列程式碼是核心的邏輯來實作這類提供者，以及這個範例省略了加入所有成員，以提供的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="e6c1c-274">每個加入的成員相關的資訊，請參閱本主題稍後的適當的區段。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="e6c1c-275">完整程式碼中，下載範例的[F # 3.0 的範例組件](https://fsharp3sample.codeplex.com)Codeplex 網站上。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="e6c1c-276">請注意下列重點：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-276">Note the following points:</span></span>

- <span data-ttu-id="e6c1c-277">型別提供者會採用兩個靜態參數： `pattern`，這是強制性，而`options`，這是選擇性的 （因為提供的預設值）。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="e6c1c-278">提供靜態引數之後，您會建立規則運算式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="e6c1c-279">如果 Regex 格式不正確，而且使用者會報告此錯誤，這個執行個體將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="e6c1c-280">內`DefineStaticParameters`回呼，定義將會傳回之後提供的引數的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="e6c1c-281">這個程式碼設定`HideObjectMethods`為 true，讓 IntelliSense 經驗會保持流暢。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="e6c1c-282">這個屬性會造成`Equals`， `GetHashCode`， `Finalize`，和`GetType`来隱藏的成員從提供的物件的 IntelliSense 清單。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="e6c1c-283">您使用`obj`為基底類型的方法，但您將使用`Regex`物件做為此類型的執行階段表示下一個範例所示。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="e6c1c-284">若要呼叫`Regex`建構函式會擲回<xref:System.ArgumentException>當規則運算式不是有效的。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="e6c1c-285">編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者回報的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="e6c1c-286">這個例外狀況可讓規則運算式，而不需執行應用程式進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="e6c1c-287">因為它並未包含任何有意義的方法或屬性，沒有尚未作用上述定義的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="e6c1c-288">首先，新增靜態`IsMatch`方法：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="e6c1c-289">先前的程式碼定義的方法`IsMatch`，會接受字串做為輸入，並傳回`bool`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="e6c1c-290">只有麻煩的部分就是使用`args`引數內`InvokeCode`定義。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="e6c1c-291">在此範例中，`args`是引號內的清單，代表這個方法的引數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="e6c1c-292">如果該方法是執行個體方法，第一個引數代表`this`引數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="e6c1c-293">不過，對於靜態方法，引數都只方法的明確引數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="e6c1c-294">請注意，加上引號的值的型別應該符合指定的傳回型別 (在此情況下， `bool`)。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="e6c1c-295">另外請注意，此程式碼使用`AddXmlDoc`來確定所提供的方法也有實用文件，您可以透過 IntelliSense 提供的方法。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="e6c1c-296">接下來，加入比對方法執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-296">Next, add an instance Match method.</span></span> <span data-ttu-id="e6c1c-297">不過，此方法應傳回值提供的`Match`型別，如此群組可以存取在強型別的方式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="e6c1c-298">因此，您先宣告`Match`型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="e6c1c-299">由於此類型取決於做為靜態引數提供的模式，這種類型都必須在參數化的類型定義中巢狀結構：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="e6c1c-300">然後，您會加入一個屬性為每個群組的相符項目型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="e6c1c-301">在執行階段，以表示相符項目<xref:System.Text.RegularExpressions.Match>值，因此必須使用定義的屬性引號<xref:System.Text.RegularExpressions.Match.Groups>編製索引的屬性，以取得相關的群組。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="e6c1c-302">同樣地，請注意，您要將 XML 文件新增到所提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="e6c1c-303">另外請注意，如果可讀取屬性`GetterCode`提供函式，且可以寫入屬性，如果`SetterCode`提供函式，所以產生的屬性唯讀。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="e6c1c-304">現在您可以建立傳回值，這個執行個體方法`Match`類型：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod = 
    ProvidedMethod(
        methodName = "Match", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = matchTy, 
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

<span data-ttu-id="e6c1c-305">因為您正在建立執行個體方法，`args.[0]`代表`RegexTyped`執行個體呼叫方法，和`args.[1]`是輸入引數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="e6c1c-306">最後，建構函式提供，以便可以建立執行個體所提供的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="e6c1c-307">建構函式只會清除建立的標準的.NET Regex 執行個體，這會再次進行 boxed 處理的物件由於`obj`是清除所提供的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="e6c1c-308">這項變更，指定稍早在本主題中的範例應用程式開發介面使用量會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="e6c1c-309">下列程式碼是完整和最終：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-309">The following code is complete and final:</span></span>

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
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

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

### <a name="key-lessons"></a><span data-ttu-id="e6c1c-310">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="e6c1c-310">Key Lessons</span></span>

<span data-ttu-id="e6c1c-311">本節說明如何建立作業的類型提供者在其靜態參數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="e6c1c-312">提供者會檢查靜態參數，並提供其值為基礎的作業。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-312">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="e6c1c-313">型別提供者，並受到本機資料</span><span class="sxs-lookup"><span data-stu-id="e6c1c-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="e6c1c-314">通常，您可能想顯示而不只是靜態參數從本機或遠端系統的資訊為基礎的應用程式開發介面的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="e6c1c-315">本章節討論本機資料，例如本機資料檔為基礎的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-315">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="e6c1c-316">簡單的 CSV 檔案提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-316">Simple CSV File Provider</span></span>

<span data-ttu-id="e6c1c-317">為簡單的範例，請考慮存取以逗號分隔值 (CSV) 格式的科學資料型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="e6c1c-318">本節假設，CSV 檔案包含標頭資料列，再浮動點資料，如下列表格所示：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>


|<span data-ttu-id="e6c1c-319">距離 （公尺）</span><span class="sxs-lookup"><span data-stu-id="e6c1c-319">Distance (meter)</span></span>|<span data-ttu-id="e6c1c-320">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="e6c1c-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="e6c1c-321">50.0</span><span class="sxs-lookup"><span data-stu-id="e6c1c-321">50.0</span></span>|<span data-ttu-id="e6c1c-322">3.7</span><span class="sxs-lookup"><span data-stu-id="e6c1c-322">3.7</span></span>|
|<span data-ttu-id="e6c1c-323">100.0</span><span class="sxs-lookup"><span data-stu-id="e6c1c-323">100.0</span></span>|<span data-ttu-id="e6c1c-324">5.2</span><span class="sxs-lookup"><span data-stu-id="e6c1c-324">5.2</span></span>|
|<span data-ttu-id="e6c1c-325">150.0</span><span class="sxs-lookup"><span data-stu-id="e6c1c-325">150.0</span></span>|<span data-ttu-id="e6c1c-326">6.4</span><span class="sxs-lookup"><span data-stu-id="e6c1c-326">6.4</span></span>|

<span data-ttu-id="e6c1c-327">本節說明如何提供可用來取得資料列的型別`Distance`型別的屬性`float<meter>`和`Time`型別的屬性`float<second>`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="e6c1c-328">為了簡單起見，請進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="e6c1c-329">標頭名稱都是無單位的或具有 「 名稱 （單位） 」 的格式，且不能包含逗號。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="e6c1c-330">單位是做為所有 Systeme 國際 (SI) 單位[Microsoft.FSharp.Data.UnitSystems.SI.UnitNames 模組 （F #）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-330">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="e6c1c-331">單位為所有簡單 （比方說，測量） 而非複合 （例如，計量表/秒）。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="e6c1c-332">所有資料行包含浮動點資料。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-332">All columns contain floating point data.</span></span>

<span data-ttu-id="e6c1c-333">更完整的提供者會放寬這些限制。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="e6c1c-334">一次的第一個步驟是考慮應用程式開發介面的外觀。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="e6c1c-335">假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="e6c1c-336">在此情況下，編譯器應該將這些呼叫轉換成結果類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="e6c1c-337">最佳的轉譯會需要的型別提供者來定義真實`CsvFile`型別提供者的組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="e6c1c-338">型別提供者通常依賴一些協助程式類型和方法，以重要的邏輯包裝。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="e6c1c-339">因為在執行階段刪除量值時，您可以使用`float[]`做為一個資料列的刪除類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="e6c1c-340">編譯器會將不同的資料行視為具有不同的量值類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="e6c1c-341">例如，在本例中的第一個資料行具有類型`float<meter>`，和第二個`float<second>`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="e6c1c-342">不過，它們的表示可以保持相當簡單。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="e6c1c-343">下列程式碼顯示實作的核心。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data = 
        seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
                 yield line.Split(',') |> Array.map float }
        |> Seq.cache
    member __.Data = data

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

<span data-ttu-id="e6c1c-344">請注意下列有關實作的重點：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="e6c1c-345">多載建構函式可讓原始的檔案或已讀取相同的結構描述的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="e6c1c-346">當您撰寫本機或遠端資料來源的型別提供者及此模式可讓本機檔案要作為範本用於遠端資料，此模式相當常見。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="e6c1c-347">您可以使用[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)會傳遞至型別提供者建構函式，來解析相對檔案名稱中的值。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="e6c1c-348">您可以使用`AddDefinitionLocation`方法來定義提供內容的位置。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="e6c1c-349">因此，如果您使用`Go To Definition`上提供的屬性，CSV 檔案會在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="e6c1c-350">您可以使用`ProvidedMeasureBuilder`查閱 SI 單位，並產生相關的型別`float<_>`型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="e6c1c-351">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="e6c1c-351">Key Lessons</span></span>

<span data-ttu-id="e6c1c-352">本節說明如何使用簡單的結構描述包含在資料來源本身建立的本機資料來源的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="e6c1c-353">繼續進行</span><span class="sxs-lookup"><span data-stu-id="e6c1c-353">Going Further</span></span>

<span data-ttu-id="e6c1c-354">下列各節包含進一步研究的建議。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-354">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="e6c1c-355">查看清除類型的已編譯的程式碼</span><span class="sxs-lookup"><span data-stu-id="e6c1c-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="e6c1c-356">若要讓型別提供者的使用方式對應至，就會發出程式碼的一些概念，看看下列的函式使用`HelloWorldTypeProvider`稍早在本主題中使用。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="e6c1c-357">以下是產生的程式碼解編使用 ildasm.exe 的映像：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```
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

<span data-ttu-id="e6c1c-358">如範例所示，所有提及的型別`Type1`和`InstanceProperty`屬性已被清除，離開只有在執行階段型別上的作業相關。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="e6c1c-359">設計和型別提供者的命名慣例</span><span class="sxs-lookup"><span data-stu-id="e6c1c-359">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="e6c1c-360">撰寫型別提供者時，請觀察下列慣例。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="e6c1c-361">**連接通訊協定的提供者**一般情況下，資料和服務的連線通訊協定，例如 OData 或 SQL 連接時，大部分提供者 Dll 的名稱應該結束`TypeProvider`或`TypeProviders`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="e6c1c-362">例如，使用類似如下的 DLL 名稱：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-362">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="e6c1c-363">請確定您提供的型別是對應的命名空間的成員，並指出您實作的連線通訊協定：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="e6c1c-364">**公用程式的一般程式碼撰寫的提供者**。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="e6c1c-365">公用程式類型提供者的規則運算式，型別提供者可能是基底文件庫的一部分，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="e6c1c-366">在此情況下，提供的型別會根據一般的.NET 設計慣例的適當時機出現：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="e6c1c-367">**單一資料來源**。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="e6c1c-368">某些型別提供者連接到單一專用的資料來源，並提供只有資料。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="e6c1c-369">在此情況下，您應該卸除`TypeProvider`尾碼和使用的.NET 命名標準的慣例：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="e6c1c-370">如需詳細資訊，請參閱`GetConnection`設計為在本主題稍後所述的慣例。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="e6c1c-371">型別提供者設計模式</span><span class="sxs-lookup"><span data-stu-id="e6c1c-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="e6c1c-372">下列章節說明撰寫型別提供者時，您可以使用設計模式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-372">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="e6c1c-373">GetConnection 設計模式</span><span class="sxs-lookup"><span data-stu-id="e6c1c-373">The GetConnection Design Pattern</span></span>
<span data-ttu-id="e6c1c-374">大部分的型別提供者應該將編寫成使用`GetConnection`由型別中的提供者 FSharp.Data.TypeProviders.dll，如下列範例所示的模式：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="e6c1c-375">備份遠端資料和服務的型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="e6c1c-376">建立遠端資料和服務所支援的類型提供者之前，您必須考慮各種連線程式設計中固有的問題。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="e6c1c-377">其中包括下列考量：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="e6c1c-378">結構描述對應</span><span class="sxs-lookup"><span data-stu-id="e6c1c-378">schema mapping</span></span>

- <span data-ttu-id="e6c1c-379">liveness 和結構描述變更時失效</span><span class="sxs-lookup"><span data-stu-id="e6c1c-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="e6c1c-380">結構描述快取</span><span class="sxs-lookup"><span data-stu-id="e6c1c-380">schema caching</span></span>

- <span data-ttu-id="e6c1c-381">資料存取作業的非同步實作</span><span class="sxs-lookup"><span data-stu-id="e6c1c-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="e6c1c-382">支援的查詢，包括 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="e6c1c-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="e6c1c-383">認證和驗證</span><span class="sxs-lookup"><span data-stu-id="e6c1c-383">credentials and authentication</span></span>

<span data-ttu-id="e6c1c-384">本主題不會探索這些進一步的問題。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="e6c1c-385">其他撰寫技巧</span><span class="sxs-lookup"><span data-stu-id="e6c1c-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="e6c1c-386">當您撰寫您自己的型別提供者時，您可以使用下列其他技巧。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="e6c1c-387">建立型別和成員視</span><span class="sxs-lookup"><span data-stu-id="e6c1c-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="e6c1c-388">ProvidedType API 具有延遲 AddMember 的版本。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="e6c1c-389">這些版本可用來建立隨空間的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="e6c1c-390">提供陣列型別和泛型類型具現化</span><span class="sxs-lookup"><span data-stu-id="e6c1c-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="e6c1c-391">使用一般進行 （其簽章包含陣列類型、 byref 類型和具現化的泛型型別） 的成員提供`MakeArrayType`， `MakePointerType`，和`MakeGenericType`的任何執行個體上<xref:System.Type>，包括`ProvidedTypeDefinitions`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="e6c1c-392">在某些情況下，您可能必須使用這個 helper `ProvidedTypeBuilder.MakeGenericType`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="e6c1c-393">請參閱[型別提供者 SDK 文件](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="e6c1c-394">提供的量值的附註的單位</span><span class="sxs-lookup"><span data-stu-id="e6c1c-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="e6c1c-395">ProvidedTypes API 會提供協助提供量值的註解。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="e6c1c-396">例如，若要提供的型別`float<kg>`，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="e6c1c-397">若要提供型別`Nullable<decimal<kg/m^2>>`，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="e6c1c-398">存取專案本機或指令碼本機資源</span><span class="sxs-lookup"><span data-stu-id="e6c1c-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="e6c1c-399">每個型別提供者執行個體可以有`TypeProviderConfig`在建構期間的值。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="e6c1c-400">這個值包含 「 解析資料夾 」 提供者 （也就是 [project] 資料夾的編譯或包含的指令碼的目錄）、 參考的組件的清單和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="e6c1c-401">失效</span><span class="sxs-lookup"><span data-stu-id="e6c1c-401">Invalidation</span></span>

<span data-ttu-id="e6c1c-402">提供者可以引發失效信號，通知可能已變更的結構描述假設 F # 語言服務。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="e6c1c-403">失效時，如果提供者裝載在 Visual Studio 中，會重做 typecheck。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="e6c1c-404">F # Interactive 中或 F # 編譯器 (fsc.exe) 所裝載的提供者時，將會忽略此訊號。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="e6c1c-405">快取的結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="e6c1c-405">Caching Schema Information</span></span>

<span data-ttu-id="e6c1c-406">提供者通常必須快取結構描述資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="e6c1c-407">使用指定的檔案名稱，做為靜態參數或做為使用者資料應該儲存快取的資料。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="e6c1c-408">舉例來說，結構描述快取是`LocalSchemaFile`參數中的型別提供者中`FSharp.Data.TypeProviders`組件。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="e6c1c-409">在這些提供者實作中，這個靜態參數會指示要用於指定的本機檔案，而不是透過網路存取資料來源的結構描述資訊的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="e6c1c-410">若要使用快取結構描述資訊，您也必須設定的靜態參數`ForceUpdate`至`false`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="e6c1c-411">若要啟用線上和離線的資料存取，您可以使用類似的技術。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="e6c1c-412">備份組件</span><span class="sxs-lookup"><span data-stu-id="e6c1c-412">Backing Assembly</span></span>

<span data-ttu-id="e6c1c-413">當您編譯`.dll`或`.exe`檔案，備份.dll 檔案產生的型別以靜態方式連結到產生的組件。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="e6c1c-414">此連結會建立從備份組件到最終組件複製的中繼語言 (IL) 型別定義和任何 managed 的資源。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="e6c1c-415">當您使用 F # Interactive 時，備份.dll 檔案不複製，並會改為直接載入至 F # 互動式處理序。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="e6c1c-416">例外狀況及診斷從型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="e6c1c-417">使用提供的類型中的所有成員的所有可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="e6c1c-418">在所有情況下，型別提供者會擲回的例外狀況，如果主機編譯器屬性錯誤的特定型別提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="e6c1c-419">內部編譯器錯誤應該永遠不會產生型別提供者的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="e6c1c-420">型別提供者無法報告警告。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="e6c1c-421">當型別提供者裝載在 F # 編譯器、 F # 開發環境中，或 F # Interactive 時，會攔截到該提供者的所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="e6c1c-422">訊息屬性一定是錯誤的文字，而且沒有堆疊追蹤會出現。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="e6c1c-423">如果您將會擲回例外狀況，您可以擲回下列的範例： `System.NotSupportedException`， `System.IO.IOException`， `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="e6c1c-424">提供產生的型別</span><span class="sxs-lookup"><span data-stu-id="e6c1c-424">Providing Generated Types</span></span>

<span data-ttu-id="e6c1c-425">目前為止，本文件說明如何提供它們的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="e6c1c-426">您也可以使用在 F # 中的型別提供者機制，提供產生的型別，可加入做為實際的.NET 型別定義，到使用者的程式。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="e6c1c-427">您必須參考產生提供使用型別定義的類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="e6c1c-428">是 F # 3.0 版中的一部分 ProvidedTypes 0.2 協助程式程式碼只具有有限的支援，提供產生的型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="e6c1c-429">下列陳述式必須是產生的型別定義，則為 true:</span><span class="sxs-lookup"><span data-stu-id="e6c1c-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="e6c1c-430">`isErased` 必須設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="e6c1c-431">產生的型別必須新增至新建構`ProvidedAssembly()`，表示為產生的程式碼片段的容器。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="e6c1c-432">提供者必須具有相符的.dll 檔案在磁碟上的實際備份.NET.dll 檔案的組件。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="e6c1c-433">規則和限制</span><span class="sxs-lookup"><span data-stu-id="e6c1c-433">Rules and Limitations</span></span>

<span data-ttu-id="e6c1c-434">當您撰寫型別提供者時，請記住下列規則和限制。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-434">When you write type providers, keep the following rules and limitations in mind.</span></span>


### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="e6c1c-435">提供的類型必須是可連線</span><span class="sxs-lookup"><span data-stu-id="e6c1c-435">Provided types must be reachable</span></span>

<span data-ttu-id="e6c1c-436">所有提供的類型應該是從非巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="e6c1c-437">呼叫中指定的非巢狀型別`TypeProviderForNamespaces`建構函式或呼叫`AddNamespace`。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="e6c1c-438">例如，如果提供者提供的型別`StaticClass.P : T`，您必須確定 T 的非巢狀類型或巢狀方式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="e6c1c-439">例如，某些提供者具有靜態類別，例如`DataTypes`，包含這些`T1, T2, T3, ...`型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="e6c1c-440">否則，錯誤為找不到組件 A 中的型別 T 的參考，但在該組件中找不到型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="e6c1c-441">如果出現這個錯誤，請確認您所有的子類型，可以達到從提供者類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="e6c1c-442">注意： 這些`T1, T2, T3...`類型稱為*上即時*型別。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="e6c1c-443">請記得將它們放在可存取的命名空間或父類型。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="e6c1c-444">型別提供者機制的限制</span><span class="sxs-lookup"><span data-stu-id="e6c1c-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="e6c1c-445">F # 中的型別提供者機制有下列限制：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="e6c1c-446">提供給泛型類型或泛型方法所提供，不支援 F # 中的型別提供者的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="e6c1c-447">機制並不支援巢狀的類型的靜態參數。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="e6c1c-448">開發秘訣</span><span class="sxs-lookup"><span data-stu-id="e6c1c-448">Development Tips</span></span>

<span data-ttu-id="e6c1c-449">您可能會發現下列秘訣有助於在開發程序。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-449">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="e6c1c-450">執行 Visual Studio 的兩個執行個體</span><span class="sxs-lookup"><span data-stu-id="e6c1c-450">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="e6c1c-451">您可以開發一個執行個體中的型別提供者，並測試其他的提供者，因為測試 IDE 將會防止型別提供者正在重建的.dll 檔案鎖定。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="e6c1c-452">因此，您必須關閉 Visual Studio 的第二個執行個體時，第一個執行個體中，內建提供者，然後您必須重新開啟第二個執行個體後建置提供者。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="e6c1c-453">偵錯使用 fsc.exe 的引動過程的型別提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="e6c1c-454">您可以使用下列工具來叫用型別提供者：</span><span class="sxs-lookup"><span data-stu-id="e6c1c-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="e6c1c-455">fsc.exe （F # 命令列編譯器）</span><span class="sxs-lookup"><span data-stu-id="e6c1c-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="e6c1c-456">fsi.exe （F # Interactive 編譯器）</span><span class="sxs-lookup"><span data-stu-id="e6c1c-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="e6c1c-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e6c1c-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="e6c1c-458">您可以經常使用偵錯型別提供者最容易 fsc.exe 的測試指令碼檔案 (例如，script.fsx) 上。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="e6c1c-459">您可以啟動偵錯工具從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-459">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="e6c1c-460">您可以使用列印至 stdout 記錄。</span><span class="sxs-lookup"><span data-stu-id="e6c1c-460">You can use print-to-stdout logging.</span></span>


## <a name="see-also"></a><span data-ttu-id="e6c1c-461">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c1c-461">See Also</span></span>

* [<span data-ttu-id="e6c1c-462">類型提供者</span><span class="sxs-lookup"><span data-stu-id="e6c1c-462">Type Providers</span></span>](index.md)

* [<span data-ttu-id="e6c1c-463">型別提供者 SDK</span><span class="sxs-lookup"><span data-stu-id="e6c1c-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)

