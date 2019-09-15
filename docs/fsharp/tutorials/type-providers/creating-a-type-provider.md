---
title: 教學課程：建立型別提供者
description: 藉由檢查數個簡單F#的類型提供F#者來說明基本概念，以瞭解如何在3.0 中建立您自己的類型提供者。
ms.date: 02/02/2019
ms.openlocfilehash: 800b5a670b7f25f462e1ce23c3d40fd2eab3b102
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991871"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="87235-103">教學課程：建立型別提供者</span><span class="sxs-lookup"><span data-stu-id="87235-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="87235-104">中F#的型別提供者機制，是其對資訊豐富程式設計支援的重要部分。</span><span class="sxs-lookup"><span data-stu-id="87235-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="87235-105">本教學課程說明如何建立您自己的型別提供者，方法是逐步執行數個簡單型別提供者的開發，以說明基本概念。</span><span class="sxs-lookup"><span data-stu-id="87235-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="87235-106">如需中F#型別提供者機制的詳細資訊，請參閱[型別提供者](index.md)。</span><span class="sxs-lookup"><span data-stu-id="87235-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="87235-107">F#生態系統包含常用網際網路和企業資料服務的一系列型別提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="87235-108">例如：</span><span class="sxs-lookup"><span data-stu-id="87235-108">For example:</span></span>

- <span data-ttu-id="87235-109">[Fsharp.core：資料](https://fsharp.github.io/FSharp.Data/)報括 JSON、XML、CSV 和 HTML 檔案格式的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="87235-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/)透過物件對應和針對這些資料來源的 LINQ 查詢， F#提供 SQL 資料庫的強型別存取。</span><span class="sxs-lookup"><span data-stu-id="87235-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="87235-111">[SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)具有一組類型提供者，適用于編譯時期已核取的 t-sql F#。</span><span class="sxs-lookup"><span data-stu-id="87235-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="87235-112">[Fsharp.data.typeproviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是一組較舊的類型提供者，僅供用來存取 SQL、Entity Framework、ODATA 和 WSDL 資料服務的 .NET Framework 程式設計使用。</span><span class="sxs-lookup"><span data-stu-id="87235-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="87235-113">必要時，您可以建立自訂類型提供者，或者您可以參考其他人建立的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="87235-114">例如，您的組織可能會有一個資料服務，可提供大量且不斷成長的已命名資料集數目，而每個集合都有自己的穩定資料架構。</span><span class="sxs-lookup"><span data-stu-id="87235-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="87235-115">您可以建立一個型別提供者來讀取架構，並以強型別方式將目前的資料集呈現給程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="87235-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="87235-116">在開始之前</span><span class="sxs-lookup"><span data-stu-id="87235-116">Before You Start</span></span>

<span data-ttu-id="87235-117">型別提供者機制主要是設計用來在F#程式設計經驗中插入穩定的資料和服務資訊空間。</span><span class="sxs-lookup"><span data-stu-id="87235-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="87235-118">這項機制並非設計用來插入在程式執行期間架構變更的資訊空間（以與程式邏輯相關的方式）。</span><span class="sxs-lookup"><span data-stu-id="87235-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="87235-119">此外，這種機制並不是針對語言中繼程式設計，即使該網域包含一些有效的用法。</span><span class="sxs-lookup"><span data-stu-id="87235-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="87235-120">您應該只在必要時使用此機制，而在其中開發類型提供者會產生非常高的值。</span><span class="sxs-lookup"><span data-stu-id="87235-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="87235-121">您應該避免撰寫無法使用架構的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="87235-122">同樣地，您應該避免撰寫一個一般（或甚至是現有） .NET 程式庫所能滿足的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="87235-123">開始之前，您可能會提出下列問題：</span><span class="sxs-lookup"><span data-stu-id="87235-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="87235-124">您有資訊來源的架構嗎？</span><span class="sxs-lookup"><span data-stu-id="87235-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="87235-125">若是如此，與 .NET 型別系統的F#對應為何？</span><span class="sxs-lookup"><span data-stu-id="87235-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="87235-126">您可以使用現有的（動態型別） API 作為您的實作為起點嗎？</span><span class="sxs-lookup"><span data-stu-id="87235-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="87235-127">您和您的組織是否有足夠的使用型別提供者，讓他們有價值？</span><span class="sxs-lookup"><span data-stu-id="87235-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="87235-128">一般的 .NET 程式庫是否符合您的需求？</span><span class="sxs-lookup"><span data-stu-id="87235-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="87235-129">您的架構變更了多少？</span><span class="sxs-lookup"><span data-stu-id="87235-129">How much will your schema change?</span></span>

- <span data-ttu-id="87235-130">在編碼期間是否會變更？</span><span class="sxs-lookup"><span data-stu-id="87235-130">Will it change during coding?</span></span>

- <span data-ttu-id="87235-131">它會在編碼會話之間變更嗎？</span><span class="sxs-lookup"><span data-stu-id="87235-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="87235-132">它會在程式執行期間變更嗎？</span><span class="sxs-lookup"><span data-stu-id="87235-132">Will it change during program execution?</span></span>

<span data-ttu-id="87235-133">型別提供者最適用于架構在執行時間穩定的情況，以及在已編譯器代碼的存留期間。</span><span class="sxs-lookup"><span data-stu-id="87235-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="87235-134">簡單型別提供者</span><span class="sxs-lookup"><span data-stu-id="87235-134">A Simple Type Provider</span></span>

<span data-ttu-id="87235-135">這個範例是 HelloWorldTypeProvider，類似于`examples` [ F#類型提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)目錄中的範例。</span><span class="sxs-lookup"><span data-stu-id="87235-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="87235-136">提供者提供的「類型空間」包含100已清除的類型，如下列程式碼所示， F#會使用簽章語法，並省略除了`Type1`以外的所有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="87235-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="87235-137">如需已清除之類型的詳細資訊，請參閱本主題稍後的已[清除之提供類型的詳細資料](#details-about-erased-provided-types)。</span><span class="sxs-lookup"><span data-stu-id="87235-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="87235-138">請注意，所提供的類型和成員集合是靜態已知的。</span><span class="sxs-lookup"><span data-stu-id="87235-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="87235-139">這個範例不會利用提供者提供相依于架構之類型的能力。</span><span class="sxs-lookup"><span data-stu-id="87235-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="87235-140">下列程式碼概述型別提供者的執行，而詳細資料則會在本主題的後續章節中討論。</span><span class="sxs-lookup"><span data-stu-id="87235-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="87235-141">此程式碼與線上範例之間可能有差異。</span><span class="sxs-lookup"><span data-stu-id="87235-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="87235-142">若要使用此提供者，請開啟 Visual Studio 的個別實例、 F#建立腳本，然後使用 #r，從您的腳本中新增提供者的參考，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="87235-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="87235-143">然後尋找類型提供者所`Samples.HelloWorldTypeProvider`產生之命名空間下的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="87235-144">重新編譯提供者之前，請確定您已關閉所有使用提供者 DLL 的F# Visual Studio 和 Interactive 實例。</span><span class="sxs-lookup"><span data-stu-id="87235-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="87235-145">否則，會發生組建錯誤，因為輸出 DLL 會被鎖定。</span><span class="sxs-lookup"><span data-stu-id="87235-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="87235-146">若要使用 print 語句來進行這項提供者的偵錯工具，請建立會向提供者公開問題的腳本，然後使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="87235-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="87235-147">若要使用 Visual Studio 來調試此提供者，請使用系統管理認證開啟 Visual Studio 的開發人員命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="87235-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="87235-148">或者，開啟 Visual Studio，開啟 [偵錯工具] 功能表，選擇`Debug/Attach to process…`，然後附加至您`devenv`正在編輯腳本的另一個進程。</span><span class="sxs-lookup"><span data-stu-id="87235-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="87235-149">藉由使用這個方法，您可以更輕鬆地以類型提供者中的特定邏輯為目標，方法是以互動方式將運算式輸入至第二個實例（具有完整的 IntelliSense 和其他功能）。</span><span class="sxs-lookup"><span data-stu-id="87235-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="87235-150">您可以停用 Just My Code 的偵錯工具，以更清楚地識別產生的程式碼錯誤。</span><span class="sxs-lookup"><span data-stu-id="87235-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="87235-151">如需如何啟用或停用這項功能的相關資訊，請參閱[使用偵錯工具流覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。</span><span class="sxs-lookup"><span data-stu-id="87235-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="87235-152">此外，您也可以開啟`Debug`功能表，然後選擇`Exceptions` [Ctrl + Alt + `Exceptions` E 鍵] 來開啟對話方塊，以設定第一個可能發生的例外狀況捕捉。</span><span class="sxs-lookup"><span data-stu-id="87235-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="87235-153">在該對話方塊中，選取`Common Language Runtime Exceptions`[] 下`Thrown`的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="87235-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="87235-154">實作為型別提供者</span><span class="sxs-lookup"><span data-stu-id="87235-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="87235-155">本節將逐步引導您完成類型提供者實作為的主要區段。</span><span class="sxs-lookup"><span data-stu-id="87235-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="87235-156">首先，您要定義自訂類型提供者本身的類型：</span><span class="sxs-lookup"><span data-stu-id="87235-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="87235-157">此類型必須是公用的，而且您必須使用[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性加以標記，如此一來，當個別F#的專案參考包含該類型的元件時，編譯器才會辨識該類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="87235-158">*Config*參數是選擇性的，如果存在，則會包含F#編譯器所建立之型別提供者實例的內容相關設定資訊。</span><span class="sxs-lookup"><span data-stu-id="87235-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="87235-159">接下來，您會執行[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。</span><span class="sxs-lookup"><span data-stu-id="87235-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="87235-160">在此情況下，您會`TypeProviderForNamespaces`使用`ProvidedTypes` API 中的型別做為基底型別。</span><span class="sxs-lookup"><span data-stu-id="87235-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="87235-161">此協助程式類型可以提供立即提供之命名空間的有限集合，其中每一個都直接包含有限數目的固定、立即提供的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="87235-162">在此內容中，提供者*立即*會產生類型，即使不需要或未使用它們也一樣。</span><span class="sxs-lookup"><span data-stu-id="87235-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="87235-163">接下來，定義本機私用值，以指定所提供類型的命名空間，並尋找類型提供者元件本身。</span><span class="sxs-lookup"><span data-stu-id="87235-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="87235-164">此元件稍後會用來做為所提供之已清除類型的邏輯父類型。</span><span class="sxs-lookup"><span data-stu-id="87235-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="87235-165">接下來，建立函式來提供每個類型 Type1 。Type100.</span><span class="sxs-lookup"><span data-stu-id="87235-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="87235-166">本主題稍後將會詳細說明此函式。</span><span class="sxs-lookup"><span data-stu-id="87235-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="87235-167">接下來，產生100提供的類型：</span><span class="sxs-lookup"><span data-stu-id="87235-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="87235-168">接下來，新增類型做為提供的命名空間：</span><span class="sxs-lookup"><span data-stu-id="87235-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="87235-169">最後，新增元件屬性，以指出您正在建立類型提供者 DLL：</span><span class="sxs-lookup"><span data-stu-id="87235-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="87235-170">提供一種類型和其成員</span><span class="sxs-lookup"><span data-stu-id="87235-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="87235-171">`makeOneProvidedType`函式會執行提供其中一種類型的實際工作。</span><span class="sxs-lookup"><span data-stu-id="87235-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="87235-172">此步驟說明此函式的執行方式。</span><span class="sxs-lookup"><span data-stu-id="87235-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="87235-173">首先，建立提供的類型（例如，Type1，當 n = 1，或 Type57，當 n = 57 時）。</span><span class="sxs-lookup"><span data-stu-id="87235-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="87235-174">您應該要注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="87235-174">You should note the following points:</span></span>

- <span data-ttu-id="87235-175">已清除此提供的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-175">This provided type is erased.</span></span>  <span data-ttu-id="87235-176">因為您表示基底類型為`obj`，所以實例會在編譯的程式碼中顯示為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)類型的值。</span><span class="sxs-lookup"><span data-stu-id="87235-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="87235-177">當您指定非巢狀型別時，您必須指定元件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="87235-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="87235-178">若為已清除的類型，元件應該是類型提供者元件本身。</span><span class="sxs-lookup"><span data-stu-id="87235-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="87235-179">接下來，將 XML 檔加入至類型。</span><span class="sxs-lookup"><span data-stu-id="87235-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="87235-180">這是延遲的檔，也就是，如果主機編譯器需要，則視需要計算。</span><span class="sxs-lookup"><span data-stu-id="87235-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="87235-181">接下來，您要將提供的靜態屬性新增至類型：</span><span class="sxs-lookup"><span data-stu-id="87235-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="87235-182">取得此屬性一律會評估為字串 "Hello！"。</span><span class="sxs-lookup"><span data-stu-id="87235-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="87235-183">屬性`GetterCode`的會使用F#引號，這代表主機編譯器為了取得屬性而產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="87235-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="87235-184">如需報價的詳細資訊，請參閱程式[代碼報價（F#）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。</span><span class="sxs-lookup"><span data-stu-id="87235-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="87235-185">將 XML 檔加入至屬性。</span><span class="sxs-lookup"><span data-stu-id="87235-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="87235-186">現在，將提供的屬性附加至提供的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="87235-187">您必須將提供的成員附加至一種類型。</span><span class="sxs-lookup"><span data-stu-id="87235-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="87235-188">否則，將永遠無法存取該成員。</span><span class="sxs-lookup"><span data-stu-id="87235-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="87235-189">現在，請建立不採用任何參數的提供的函式。</span><span class="sxs-lookup"><span data-stu-id="87235-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="87235-190">此函式F#的會傳回引號，表示呼叫此函式時，主機編譯器所產生的程式碼。 `InvokeCode`</span><span class="sxs-lookup"><span data-stu-id="87235-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="87235-191">例如，您可以使用下列的函數：</span><span class="sxs-lookup"><span data-stu-id="87235-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="87235-192">所提供類型的實例將會以基礎資料「物件資料」建立。</span><span class="sxs-lookup"><span data-stu-id="87235-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="87235-193">加上引號的程式碼包含對[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)的轉換，因為該類型是此提供類型的抹除（如同您在宣告提供的類型時所指定）。</span><span class="sxs-lookup"><span data-stu-id="87235-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="87235-194">將 XML 檔加入至此函式，並將提供的函式加入至提供的類型：</span><span class="sxs-lookup"><span data-stu-id="87235-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="87235-195">建立第二個提供的函式，以接受一個參數：</span><span class="sxs-lookup"><span data-stu-id="87235-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="87235-196">此函式F#的會再次傳回引號，代表主機編譯器為呼叫方法所產生的程式碼。 `InvokeCode`</span><span class="sxs-lookup"><span data-stu-id="87235-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="87235-197">例如，您可以使用下列的函數：</span><span class="sxs-lookup"><span data-stu-id="87235-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="87235-198">所提供類型的實例是使用基礎資料 "十" 所建立。</span><span class="sxs-lookup"><span data-stu-id="87235-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="87235-199">您可能已經注意到`InvokeCode`函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="87235-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="87235-200">此函式的輸入是運算式的清單，每個函式參數一個。</span><span class="sxs-lookup"><span data-stu-id="87235-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="87235-201">在此情況下，可以在中`args.[0]`使用代表單一參數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="87235-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="87235-202">呼叫此函式的程式碼會將傳回值強制轉型為已`obj`清除的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="87235-203">將第二個提供的函式加入至類型之後，您會建立提供的實例屬性：</span><span class="sxs-lookup"><span data-stu-id="87235-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="87235-204">取得此屬性會傳回字串的長度，也就是標記法物件。</span><span class="sxs-lookup"><span data-stu-id="87235-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="87235-205">屬性會傳回F#報價，指定主機編譯器所產生的程式碼，以取得屬性。 `GetterCode`</span><span class="sxs-lookup"><span data-stu-id="87235-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="87235-206">`InvokeCode`如同`GetterCode` ，函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="87235-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="87235-207">主機編譯器會使用引數清單來呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="87235-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="87235-208">在此情況下，引數只會包含單一運算式，代表要在其上呼叫 getter 的實例，您可以使用`args.[0]`來存取它。</span><span class="sxs-lookup"><span data-stu-id="87235-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="87235-209">然後，將接合至已清除類型`obj`的結果引號，並使用 cast 來滿足編譯器用來檢查物件是否為字串之類型的機制。 `GetterCode`</span><span class="sxs-lookup"><span data-stu-id="87235-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="87235-210">的下一個部分`makeOneProvidedType`會提供具有一個參數的實例方法。</span><span class="sxs-lookup"><span data-stu-id="87235-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="87235-211">最後，建立包含100嵌套屬性的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="87235-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="87235-212">建立此巢狀型別及其屬性會延遲，也就是視需要計算。</span><span class="sxs-lookup"><span data-stu-id="87235-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="87235-213">已清除之提供類型的詳細資料</span><span class="sxs-lookup"><span data-stu-id="87235-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="87235-214">本節中的範例只提供已*清除的提供類型*，在下列情況下特別有用：</span><span class="sxs-lookup"><span data-stu-id="87235-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="87235-215">當您針對只包含資料和方法的資訊空間撰寫提供者時。</span><span class="sxs-lookup"><span data-stu-id="87235-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="87235-216">當您撰寫提供者，其中正確的執行時間型別語義對資訊空間的實際使用並不重要。</span><span class="sxs-lookup"><span data-stu-id="87235-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="87235-217">當您撰寫的資訊空間提供者很大且相互關聯時，在技術上並不能為資訊空間產生真正的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="87235-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="87235-218">在此範例中，會將每個提供的`obj`型別清除成型別，而該型別的`obj`所有用法都會在已編譯的程式碼中顯示成型別。</span><span class="sxs-lookup"><span data-stu-id="87235-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="87235-219">事實上，這些範例中的基礎物件都是字串，但型別在 .net 編譯器`System.Object`代碼中會顯示為。</span><span class="sxs-lookup"><span data-stu-id="87235-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="87235-220">如同抹除類型的所有用法，您可以使用明確的裝箱、取消裝箱，以及轉換成破壞清除的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="87235-221">在此情況下，當使用物件時，可能會導致不正確轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="87235-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="87235-222">提供者執行時間可以定義自己的私用標記法類型，以協助防止 false 標記法。</span><span class="sxs-lookup"><span data-stu-id="87235-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="87235-223">您無法在本身定義已F#清除的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="87235-224">只有提供的類型可以清除。</span><span class="sxs-lookup"><span data-stu-id="87235-224">Only provided types may be erased.</span></span> <span data-ttu-id="87235-225">您必須瞭解使用類型提供者的已清除類型，或提供已清除類型之提供者的後果，包括實際和語義。</span><span class="sxs-lookup"><span data-stu-id="87235-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="87235-226">已清除的類型沒有真正的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="87235-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="87235-227">因此，您無法對型別執行精確的反映，而且如果您使用執行時間轉換和其他依賴實際執行時間型別語義的技術，則可能會破壞已清除的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="87235-228">已清除類型的 Subversion 經常會在執行時間產生類型轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="87235-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="87235-229">選擇已清除之提供類型的標記法</span><span class="sxs-lookup"><span data-stu-id="87235-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="87235-230">對於已清除之提供類型的某些用法，不需要任何標記法。</span><span class="sxs-lookup"><span data-stu-id="87235-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="87235-231">例如，已清除的提供類型可能只包含靜態屬性和成員，而且沒有任何方法或屬性會傳回類型的實例。</span><span class="sxs-lookup"><span data-stu-id="87235-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="87235-232">如果您可以到達已清除之提供類型的實例，則必須考慮下列問題：</span><span class="sxs-lookup"><span data-stu-id="87235-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="87235-233">**所提供類型的抹除是什麼？**</span><span class="sxs-lookup"><span data-stu-id="87235-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="87235-234">所提供類型的抹除是該類型在已編譯的 .NET 程式碼中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="87235-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="87235-235">在類型的繼承鏈中，所提供之已清除類別類型的抹除一律是第一個未清除的基底類型。</span><span class="sxs-lookup"><span data-stu-id="87235-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="87235-236">所提供之已清除介面類別型的抹除一律`System.Object`為。</span><span class="sxs-lookup"><span data-stu-id="87235-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="87235-237">**提供類型的標記法為何？**</span><span class="sxs-lookup"><span data-stu-id="87235-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="87235-238">已清除之提供類型的一組可能物件稱為其標記法。</span><span class="sxs-lookup"><span data-stu-id="87235-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="87235-239">在本檔的範例中，所有已清除之提供類型`Type1.Type100`的表示一律為 string 物件。</span><span class="sxs-lookup"><span data-stu-id="87235-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="87235-240">所提供類型的所有表示都必須與所提供類型的抹除相容。</span><span class="sxs-lookup"><span data-stu-id="87235-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="87235-241">（否則， F#編譯器會提供使用型別提供者的錯誤，否則會產生不正確無法驗證的 .net 程式碼。</span><span class="sxs-lookup"><span data-stu-id="87235-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="87235-242">如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。</span><span class="sxs-lookup"><span data-stu-id="87235-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="87235-243">您可以使用下列其中一種方法來選擇所提供物件的標記法，這兩者都很常見：</span><span class="sxs-lookup"><span data-stu-id="87235-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="87235-244">如果您只是在現有的 .NET 類型上提供強型別包裝函式，則您的型別會清除為該型別，請使用該型別的實例做為標記法，或兩者皆是。</span><span class="sxs-lookup"><span data-stu-id="87235-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="87235-245">當使用強型別版本時，該型別上大部分的現有方法仍有意義，這是適當的方法。</span><span class="sxs-lookup"><span data-stu-id="87235-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="87235-246">如果您想要建立與任何現有 .NET API 截然不同的 API，建立執行時間類型將會是所提供類型的抹除和標記法，是合理的做法。</span><span class="sxs-lookup"><span data-stu-id="87235-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="87235-247">本檔中的範例使用字串作為所提供物件的標記法。</span><span class="sxs-lookup"><span data-stu-id="87235-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="87235-248">通常，針對標記法使用其他物件可能是適當的方式。</span><span class="sxs-lookup"><span data-stu-id="87235-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="87235-249">例如，您可以使用字典做為屬性包：</span><span class="sxs-lookup"><span data-stu-id="87235-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="87235-250">或者，您也可以在型別提供者中定義一個類型，以便在執行時間用來形成標記法，以及一或多個執行時間作業：</span><span class="sxs-lookup"><span data-stu-id="87235-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="87235-251">提供的成員可以接著建立此物件類型的實例：</span><span class="sxs-lookup"><span data-stu-id="87235-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="87235-252">在這種情況下，您可以（選擇性地）使用此類型做為型別抹除，方法`baseType`是在`ProvidedTypeDefinition`建立時將此型別指定為：</span><span class="sxs-lookup"><span data-stu-id="87235-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="87235-253">重要課程</span><span class="sxs-lookup"><span data-stu-id="87235-253">Key Lessons</span></span>

<span data-ttu-id="87235-254">上一節說明如何建立簡單的抹除類型提供者，以提供類型、屬性和方法的範圍。</span><span class="sxs-lookup"><span data-stu-id="87235-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="87235-255">本節也說明了抹除類型的概念，包括從類型提供者提供已清除類型的一些優缺點，以及已清除類型的標記法。</span><span class="sxs-lookup"><span data-stu-id="87235-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="87235-256">使用靜態參數的類型提供者</span><span class="sxs-lookup"><span data-stu-id="87235-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="87235-257">透過靜態資料參數化型別提供者的能力，可實現許多有趣的案例，即使提供者不需要存取任何本機或遠端資料也一樣。</span><span class="sxs-lookup"><span data-stu-id="87235-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="87235-258">在本節中，您將瞭解將這類提供者放在一起的一些基本技巧。</span><span class="sxs-lookup"><span data-stu-id="87235-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="87235-259">類型已核取的 Regex 提供者</span><span class="sxs-lookup"><span data-stu-id="87235-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="87235-260">假設您想要在提供下列編譯時間保證的介面中，針對包裝<xref:System.Text.RegularExpressions.Regex> .net 程式庫的正則運算式，執行型別提供者：</span><span class="sxs-lookup"><span data-stu-id="87235-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="87235-261">正在驗證正則運算式是否有效。</span><span class="sxs-lookup"><span data-stu-id="87235-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="87235-262">根據正則運算式中的任何組名，提供相符專案的命名屬性。</span><span class="sxs-lookup"><span data-stu-id="87235-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="87235-263">本節說明如何使用型別提供者建立`RegexTyped`正則運算式模式所參數化的型別，以提供這些優點。</span><span class="sxs-lookup"><span data-stu-id="87235-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="87235-264">如果提供的模式無效，則編譯器會報告錯誤，而且型別提供者可以從模式中解壓縮群組，讓您可以使用相符專案上的命名屬性來存取它們。</span><span class="sxs-lookup"><span data-stu-id="87235-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="87235-265">當您設計型別提供者時，應該考慮其公開的 API 應如何向使用者顯示，以及此設計將如何轉譯為 .NET 程式碼。</span><span class="sxs-lookup"><span data-stu-id="87235-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="87235-266">下列範例顯示如何使用這類 API 來取得區碼的元件：</span><span class="sxs-lookup"><span data-stu-id="87235-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="87235-267">下列範例顯示型別提供者轉譯這些呼叫的方式：</span><span class="sxs-lookup"><span data-stu-id="87235-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="87235-268">請注意下列幾點:</span><span class="sxs-lookup"><span data-stu-id="87235-268">Note the following points:</span></span>

- <span data-ttu-id="87235-269">標準 Regex 類型代表參數化`RegexTyped`類型。</span><span class="sxs-lookup"><span data-stu-id="87235-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="87235-270">此`RegexTyped`函式會產生 Regex 函式的呼叫，並傳入模式的靜態類型引數。</span><span class="sxs-lookup"><span data-stu-id="87235-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="87235-271">`Match`方法的結果是以標準<xref:System.Text.RegularExpressions.Match>型別表示。</span><span class="sxs-lookup"><span data-stu-id="87235-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="87235-272">每個命名群組都會產生提供的屬性，而存取屬性會導致在相符的`Groups`集合上使用索引子。</span><span class="sxs-lookup"><span data-stu-id="87235-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="87235-273">下列程式碼是執行這類提供者之邏輯的核心，而此範例會省略將所有成員加入至提供之類型的動作。</span><span class="sxs-lookup"><span data-stu-id="87235-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="87235-274">如需每個新增成員的詳細資訊，請參閱本主題稍後的適當章節。</span><span class="sxs-lookup"><span data-stu-id="87235-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="87235-275">如需完整的程式碼，請從 CodePlex 網站上的[ F# 3.0 範例套件](https://archive.codeplex.com/?p=fsharp3sample)下載範例。</span><span class="sxs-lookup"><span data-stu-id="87235-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="87235-276">請注意下列幾點:</span><span class="sxs-lookup"><span data-stu-id="87235-276">Note the following points:</span></span>

- <span data-ttu-id="87235-277">型別提供者接受兩個靜態參數`pattern`：，這是必要的， `options`而是選擇性的（因為提供了預設值）。</span><span class="sxs-lookup"><span data-stu-id="87235-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="87235-278">提供靜態引數之後，您可以建立正則運算式的實例。</span><span class="sxs-lookup"><span data-stu-id="87235-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="87235-279">如果 Regex 的格式不正確，這個實例就會擲回例外狀況，而且會向使用者回報此錯誤。</span><span class="sxs-lookup"><span data-stu-id="87235-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="87235-280">`DefineStaticParameters`在回呼內，您會定義要在提供引數之後傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="87235-281">這段程式`HideObjectMethods`代碼會將設定為 true，讓 IntelliSense 體驗保持順暢。</span><span class="sxs-lookup"><span data-stu-id="87235-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="87235-282">這個屬性會使`Equals`、 `GetHashCode`、 `Finalize`和`GetType`成員從提供之物件的 IntelliSense 清單中隱藏。</span><span class="sxs-lookup"><span data-stu-id="87235-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="87235-283">您會`obj`使用做為方法的基底類型，但您會`Regex`使用物件做為此類型的運行時程表示法，如下一個範例所示。</span><span class="sxs-lookup"><span data-stu-id="87235-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="87235-284">當正則運算式`Regex`無效時，對此函式的呼叫會擲回。 <xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="87235-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="87235-285">編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者報告錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="87235-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="87235-286">這個例外狀況可讓您驗證正則運算式，而不需要執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="87235-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="87235-287">上述定義的類型並不實用，因為它不包含任何有意義的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="87235-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="87235-288">首先，新增靜態`IsMatch`方法：</span><span class="sxs-lookup"><span data-stu-id="87235-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="87235-289">先前的程式碼會定義`IsMatch`方法，以接受字串做為輸入，並`bool`傳回。</span><span class="sxs-lookup"><span data-stu-id="87235-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="87235-290">唯一棘手的部分是在`args` `InvokeCode`定義內使用引數。</span><span class="sxs-lookup"><span data-stu-id="87235-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="87235-291">在此範例中`args` ，是代表這個方法之引數的引號清單。</span><span class="sxs-lookup"><span data-stu-id="87235-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="87235-292">如果方法是實例方法，則第一個引數代表`this`引數。</span><span class="sxs-lookup"><span data-stu-id="87235-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="87235-293">不過，對於靜態方法，引數只是方法的明確引數而已。</span><span class="sxs-lookup"><span data-stu-id="87235-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="87235-294">請注意，引號值的類型應符合指定的傳回類型（在此案例`bool`中為）。</span><span class="sxs-lookup"><span data-stu-id="87235-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="87235-295">另請注意，此程式碼`AddXmlDoc`會使用方法來確定提供的方法也有實用的檔，您可以透過 IntelliSense 提供此功能。</span><span class="sxs-lookup"><span data-stu-id="87235-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="87235-296">接下來，新增實例 Match 方法。</span><span class="sxs-lookup"><span data-stu-id="87235-296">Next, add an instance Match method.</span></span> <span data-ttu-id="87235-297">不過，這個方法應該會傳回所提供`Match`類型的值，以便以強型別方式來存取群組。</span><span class="sxs-lookup"><span data-stu-id="87235-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="87235-298">因此，您必須先`Match`宣告型別。</span><span class="sxs-lookup"><span data-stu-id="87235-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="87235-299">因為此型別取決於當做靜態引數提供的模式，所以這個型別必須嵌套在參數化型別定義內：</span><span class="sxs-lookup"><span data-stu-id="87235-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="87235-300">接著，您可以將一個屬性新增至每個群組的比對類型。</span><span class="sxs-lookup"><span data-stu-id="87235-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="87235-301">在執行時間，比對是以<xref:System.Text.RegularExpressions.Match>值表示，因此定義屬性的引號必須<xref:System.Text.RegularExpressions.Match.Groups>使用索引屬性來取得相關的群組。</span><span class="sxs-lookup"><span data-stu-id="87235-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="87235-302">同樣地，請注意，您要將 XML 檔新增至提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="87235-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="87235-303">也請注意，如果`GetterCode`提供了函式，就可以讀取屬性，而且`SetterCode`如果提供了函數，就可以寫入屬性，因此產生的屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="87235-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="87235-304">現在您可以建立傳回此`Match`類型值的實例方法：</span><span class="sxs-lookup"><span data-stu-id="87235-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="87235-305">因為您要建立實例方法， `args.[0]`所以代表呼叫方法所在的`RegexTyped`實例，而`args.[1]`則是輸入引數。</span><span class="sxs-lookup"><span data-stu-id="87235-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="87235-306">最後，提供一個可讓您建立所提供類型之實例的函式。</span><span class="sxs-lookup"><span data-stu-id="87235-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="87235-307">此函式只會清除建立標準 .net Regex 實例，這會再次加入至物件，因為`obj`是所提供類型的抹除。</span><span class="sxs-lookup"><span data-stu-id="87235-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="87235-308">隨著這項變更，稍早在本主題中指定的範例 API 使用方式會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="87235-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="87235-309">下列程式碼為 complete 和 final：</span><span class="sxs-lookup"><span data-stu-id="87235-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="87235-310">重要課程</span><span class="sxs-lookup"><span data-stu-id="87235-310">Key Lessons</span></span>

<span data-ttu-id="87235-311">本節說明如何建立可在其靜態參數上運作的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="87235-312">提供者會檢查靜態參數，並根據其值提供作業。</span><span class="sxs-lookup"><span data-stu-id="87235-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="87235-313">由本機資料支援的類型提供者</span><span class="sxs-lookup"><span data-stu-id="87235-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="87235-314">通常，您可能會希望型別提供者不僅以靜態參數為基礎來呈現 Api，也會顯示來自本機或遠端系統的資訊。</span><span class="sxs-lookup"><span data-stu-id="87235-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="87235-315">本節討論以本機資料為基礎的型別提供者，例如本機資料檔案。</span><span class="sxs-lookup"><span data-stu-id="87235-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="87235-316">簡單的 CSV 檔案提供者</span><span class="sxs-lookup"><span data-stu-id="87235-316">Simple CSV File Provider</span></span>

<span data-ttu-id="87235-317">做為簡單的範例，請考慮使用以逗號分隔值（CSV）格式來存取科學資料的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="87235-318">本節假設 CSV 檔案包含標頭資料列，後面接著浮點數據，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="87235-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="87235-319">距離（計量）</span><span class="sxs-lookup"><span data-stu-id="87235-319">Distance (meter)</span></span>|<span data-ttu-id="87235-320">時間（秒）</span><span class="sxs-lookup"><span data-stu-id="87235-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="87235-321">50.0</span><span class="sxs-lookup"><span data-stu-id="87235-321">50.0</span></span>|<span data-ttu-id="87235-322">3.7</span><span class="sxs-lookup"><span data-stu-id="87235-322">3.7</span></span>|
|<span data-ttu-id="87235-323">100.0</span><span class="sxs-lookup"><span data-stu-id="87235-323">100.0</span></span>|<span data-ttu-id="87235-324">5.2</span><span class="sxs-lookup"><span data-stu-id="87235-324">5.2</span></span>|
|<span data-ttu-id="87235-325">150.0</span><span class="sxs-lookup"><span data-stu-id="87235-325">150.0</span></span>|<span data-ttu-id="87235-326">6.4</span><span class="sxs-lookup"><span data-stu-id="87235-326">6.4</span></span>|

<span data-ttu-id="87235-327">本節說明如何提供一個型別，讓您用來取得`Distance`具有型`float<meter>`別屬性和`Time`型`float<second>`別之屬性的資料列。</span><span class="sxs-lookup"><span data-stu-id="87235-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="87235-328">為了簡單起見，會進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="87235-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="87235-329">標頭名稱不是單位或格式為 "Name （unit）"，且不包含逗號。</span><span class="sxs-lookup"><span data-stu-id="87235-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="87235-330">單位是[fsharp.core. UnitSystems. UnitNames moduleF#（）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義的所有系統國際（SI）單位。</span><span class="sxs-lookup"><span data-stu-id="87235-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="87235-331">單位全都簡單（例如，計量），而不是複合（例如，計量/秒）。</span><span class="sxs-lookup"><span data-stu-id="87235-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="87235-332">所有資料行都包含浮點數據。</span><span class="sxs-lookup"><span data-stu-id="87235-332">All columns contain floating point data.</span></span>

<span data-ttu-id="87235-333">較完整的提供者會放寬這些限制。</span><span class="sxs-lookup"><span data-stu-id="87235-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="87235-334">同樣地，第一個步驟是考慮 API 的外觀。</span><span class="sxs-lookup"><span data-stu-id="87235-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="87235-335">假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="87235-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="87235-336">在此情況下，編譯器應該將這些呼叫轉換成類似下列範例的內容：</span><span class="sxs-lookup"><span data-stu-id="87235-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="87235-337">最佳的轉譯會要求型別提供者在型別`CsvFile`提供者的元件中定義 real 型別。</span><span class="sxs-lookup"><span data-stu-id="87235-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="87235-338">型別提供者通常依賴幾個 helper 類型和方法來包裝重要的邏輯。</span><span class="sxs-lookup"><span data-stu-id="87235-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="87235-339">因為量值會在執行時間清除，所以您`float[]`可以使用做為資料列的清除類型。</span><span class="sxs-lookup"><span data-stu-id="87235-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="87235-340">編譯器會將不同的資料行視為具有不同的量數值型別。</span><span class="sxs-lookup"><span data-stu-id="87235-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="87235-341">例如，範例中的第一個資料行具有類型`float<meter>`，而`float<second>`第二個是。</span><span class="sxs-lookup"><span data-stu-id="87235-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="87235-342">不過，清除的標記法可以保持相當簡單。</span><span class="sxs-lookup"><span data-stu-id="87235-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="87235-343">下列程式碼會顯示執行的核心。</span><span class="sxs-lookup"><span data-stu-id="87235-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="87235-344">請注意下列有關執行的要點：</span><span class="sxs-lookup"><span data-stu-id="87235-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="87235-345">多載的函式允許讀取具有相同架構的原始檔案或。</span><span class="sxs-lookup"><span data-stu-id="87235-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="87235-346">當您撰寫本機或遠端資料源的型別提供者時，這個模式很常見，而此模式可讓本機檔案當做遠端資料的範本使用。</span><span class="sxs-lookup"><span data-stu-id="87235-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="87235-347">您可以使用傳入型別提供者函式的[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)值來解析相對檔案名。</span><span class="sxs-lookup"><span data-stu-id="87235-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="87235-348">您可以使用`AddDefinitionLocation`方法來定義所提供屬性的位置。</span><span class="sxs-lookup"><span data-stu-id="87235-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="87235-349">因此，如果您在`Go To Definition`提供的屬性上使用，CSV 檔案將會在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="87235-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="87235-350">您可以使用`ProvidedMeasureBuilder`類型來查閱 SI 單位，並產生相關`float<_>`的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="87235-351">重要課程</span><span class="sxs-lookup"><span data-stu-id="87235-351">Key Lessons</span></span>

<span data-ttu-id="87235-352">本節說明如何使用資料來源本身包含的簡單架構，建立本機資料來源的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="87235-353">進一步瞭解</span><span class="sxs-lookup"><span data-stu-id="87235-353">Going Further</span></span>

<span data-ttu-id="87235-354">下列各節包含進一步研究的建議。</span><span class="sxs-lookup"><span data-stu-id="87235-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="87235-355">查看已清除類型的已編譯器代碼</span><span class="sxs-lookup"><span data-stu-id="87235-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="87235-356">若要讓您瞭解如何使用型別提供者來對應到發出的程式碼，請使用`HelloWorldTypeProvider`本主題稍早所使用的來查看下列函數。</span><span class="sxs-lookup"><span data-stu-id="87235-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="87235-357">以下是使用 ildasm 所產生之程式碼反向組譯的影像：</span><span class="sxs-lookup"><span data-stu-id="87235-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="87235-358">如範例所示，所有提及的型`Type1`別`InstanceProperty`和屬性都已清除，只留下涉及的執行時間類型作業。</span><span class="sxs-lookup"><span data-stu-id="87235-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="87235-359">型別提供者的設計和命名慣例</span><span class="sxs-lookup"><span data-stu-id="87235-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="87235-360">撰寫型別提供者時，請觀察下列慣例。</span><span class="sxs-lookup"><span data-stu-id="87235-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="87235-361">**連接通訊協定的提供者**一般來說，資料和服務連線通訊協定（例如 OData 或 SQL 連接）的大部分提供者 dll 的名稱，都應該`TypeProvider`以`TypeProviders`或結尾。</span><span class="sxs-lookup"><span data-stu-id="87235-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="87235-362">例如，使用類似下列字串的 DLL 名稱：</span><span class="sxs-lookup"><span data-stu-id="87235-362">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="87235-363">請確定您提供的類型是對應命名空間的成員，並指出您所執行的連接通訊協定：</span><span class="sxs-lookup"><span data-stu-id="87235-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="87235-364">**一般程式碼撰寫的公用程式提供者**。</span><span class="sxs-lookup"><span data-stu-id="87235-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="87235-365">對於類似于正則運算式的公用程式類型提供者，類型提供者可能是基底程式庫的一部分，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="87235-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="87235-366">在此情況下，提供的類型會根據一般的 .NET 設計慣例，出現在適當的時間點：</span><span class="sxs-lookup"><span data-stu-id="87235-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="87235-367">**單一資料來源**。</span><span class="sxs-lookup"><span data-stu-id="87235-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="87235-368">某些類型提供者會連接到單一專用資料來源，並只提供資料。</span><span class="sxs-lookup"><span data-stu-id="87235-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="87235-369">在此情況下，您應該`TypeProvider`卸載尾碼，並使用一般的 .net 命名慣例：</span><span class="sxs-lookup"><span data-stu-id="87235-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="87235-370">如需詳細資訊，請`GetConnection`參閱本主題稍後所述的設計慣例。</span><span class="sxs-lookup"><span data-stu-id="87235-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="87235-371">型別提供者的設計模式</span><span class="sxs-lookup"><span data-stu-id="87235-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="87235-372">下列各節說明您可以在撰寫型別提供者時使用的設計模式。</span><span class="sxs-lookup"><span data-stu-id="87235-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="87235-373">GetConnection 設計模式</span><span class="sxs-lookup"><span data-stu-id="87235-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="87235-374">大部分的類型提供者都應該撰寫成`GetConnection`使用 fsharp.core. fsharp.data.typeproviders 中類型提供者所使用的模式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="87235-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="87235-375">由遠端資料和服務支援的類型提供者</span><span class="sxs-lookup"><span data-stu-id="87235-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="87235-376">在建立由遠端資料和服務支援的型別提供者之前，您必須考慮連線程式設計中固有的一系列問題。</span><span class="sxs-lookup"><span data-stu-id="87235-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="87235-377">這些問題包括下列考慮：</span><span class="sxs-lookup"><span data-stu-id="87235-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="87235-378">架構對應</span><span class="sxs-lookup"><span data-stu-id="87235-378">schema mapping</span></span>

- <span data-ttu-id="87235-379">發生架構變更時的活動和失效</span><span class="sxs-lookup"><span data-stu-id="87235-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="87235-380">架構快取</span><span class="sxs-lookup"><span data-stu-id="87235-380">schema caching</span></span>

- <span data-ttu-id="87235-381">資料存取作業的非同步執行</span><span class="sxs-lookup"><span data-stu-id="87235-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="87235-382">支援查詢，包括 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="87235-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="87235-383">認證和驗證</span><span class="sxs-lookup"><span data-stu-id="87235-383">credentials and authentication</span></span>

<span data-ttu-id="87235-384">本主題不會進一步探索這些問題。</span><span class="sxs-lookup"><span data-stu-id="87235-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="87235-385">其他撰寫技巧</span><span class="sxs-lookup"><span data-stu-id="87235-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="87235-386">當您撰寫自己的類型提供者時，您可能會想要使用下列其他技術。</span><span class="sxs-lookup"><span data-stu-id="87235-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="87235-387">視需要建立類型和成員</span><span class="sxs-lookup"><span data-stu-id="87235-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="87235-388">ProvidedType API 具有延遲的 AddMember 版本。</span><span class="sxs-lookup"><span data-stu-id="87235-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="87235-389">這些版本是用來建立隨選的類型空間。</span><span class="sxs-lookup"><span data-stu-id="87235-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="87235-390">提供陣列類型和泛型型別具現化</span><span class="sxs-lookup"><span data-stu-id="87235-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="87235-391">您可以在任何實例上使用`MakeArrayType`一般的、 <xref:System.Type> `MakePointerType`和`MakeGenericType` ，讓提供的成員（其簽章包含陣列類型、byref 類型和泛型型別的具現化`ProvidedTypeDefinitions`），包括。</span><span class="sxs-lookup"><span data-stu-id="87235-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="87235-392">在某些情況下，您可能必須在中`ProvidedTypeBuilder.MakeGenericType`使用 helper。</span><span class="sxs-lookup"><span data-stu-id="87235-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="87235-393">如需詳細資訊，請參閱[型別提供者 SDK 檔](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)。</span><span class="sxs-lookup"><span data-stu-id="87235-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="87235-394">提供測量單位注釋</span><span class="sxs-lookup"><span data-stu-id="87235-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="87235-395">ProvidedTypes API 提供 helper 來提供量值注釋。</span><span class="sxs-lookup"><span data-stu-id="87235-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="87235-396">例如，若要提供類型`float<kg>`，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="87235-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="87235-397">若要提供類型`Nullable<decimal<kg/m^2>>`，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="87235-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="87235-398">存取專案本機或腳本-本機資源</span><span class="sxs-lookup"><span data-stu-id="87235-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="87235-399">型別提供者的每個實例都可以`TypeProviderConfig`在結構中提供一個值。</span><span class="sxs-lookup"><span data-stu-id="87235-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="87235-400">此值包含提供者的「解析資料夾」（也就是編譯的專案資料夾或包含腳本的目錄）、參考的元件清單，以及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="87235-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="87235-401">失效</span><span class="sxs-lookup"><span data-stu-id="87235-401">Invalidation</span></span>

<span data-ttu-id="87235-402">提供者可以引發失效信號來通知F#語言服務，架構假設可能已變更。</span><span class="sxs-lookup"><span data-stu-id="87235-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="87235-403">當發生失效時，如果提供者是在 Visual Studio 中主控，則會重做 typecheck。</span><span class="sxs-lookup"><span data-stu-id="87235-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="87235-404">當提供者裝載于F#互動式或F#編譯器（fsc）時，將會忽略此信號。</span><span class="sxs-lookup"><span data-stu-id="87235-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="87235-405">快取架構資訊</span><span class="sxs-lookup"><span data-stu-id="87235-405">Caching Schema Information</span></span>

<span data-ttu-id="87235-406">提供者通常必須快取架構資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="87235-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="87235-407">快取的資料應該使用指定為靜態參數或使用者資料的檔案名來儲存。</span><span class="sxs-lookup"><span data-stu-id="87235-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="87235-408">架構快取的範例是`LocalSchemaFile` `FSharp.Data.TypeProviders`元件型別提供者中的參數。</span><span class="sxs-lookup"><span data-stu-id="87235-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="87235-409">在這些提供者的執行中，這個靜態參數會指示類型提供者使用指定本機檔案中的架構資訊，而不是透過網路存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="87235-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="87235-410">若要使用快取的架構資訊，您也必須將`ForceUpdate`靜態`false`參數設定為。</span><span class="sxs-lookup"><span data-stu-id="87235-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="87235-411">您可以使用類似的技術來啟用線上和離線資料存取。</span><span class="sxs-lookup"><span data-stu-id="87235-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="87235-412">支援元件</span><span class="sxs-lookup"><span data-stu-id="87235-412">Backing Assembly</span></span>

<span data-ttu-id="87235-413">當您編譯`.dll`或`.exe`檔案時，產生之類型的備份 .dll 檔案會以靜態方式連結到產生的元件。</span><span class="sxs-lookup"><span data-stu-id="87235-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="87235-414">建立此連結的方法是將中繼語言（IL）類型定義和任何受管理的資源從支援元件複製到最終元件。</span><span class="sxs-lookup"><span data-stu-id="87235-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="87235-415">當您使用F# Interactive 時，不會複製支援的 .dll 檔案，而會直接載入至F#互動式進程。</span><span class="sxs-lookup"><span data-stu-id="87235-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="87235-416">來自類型提供者的例外狀況和診斷</span><span class="sxs-lookup"><span data-stu-id="87235-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="87235-417">所有來自所提供類型之成員的用法可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="87235-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="87235-418">在所有情況下，如果型別提供者擲回例外狀況，則主機編譯器會將錯誤屬性設為特定的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="87235-419">型別提供者例外狀況不應該導致內部編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="87235-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="87235-420">型別提供者無法報告警告。</span><span class="sxs-lookup"><span data-stu-id="87235-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="87235-421">當型別提供者裝載于F#編譯器、 F#開發環境或F#互動式時，會攔截該提供者的所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="87235-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="87235-422">Message 屬性一律為錯誤文字，而且不會出現任何堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="87235-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="87235-423">如果您要擲回例外狀況，您可以擲回下列範例： `System.NotSupportedException`、 `System.IO.IOException`、 `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="87235-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="87235-424">提供產生的類型</span><span class="sxs-lookup"><span data-stu-id="87235-424">Providing Generated Types</span></span>

<span data-ttu-id="87235-425">到目前為止，本檔已說明如何提供已清除的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="87235-426">您也可以使用中F#的類型提供者機制來提供產生的類型，這會在使用者的程式中新增為實際的 .net 類型定義。</span><span class="sxs-lookup"><span data-stu-id="87235-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="87235-427">您必須使用類型定義來參考產生的提供類型。</span><span class="sxs-lookup"><span data-stu-id="87235-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="87235-428">屬於F# 3.0 版的 ProvidedTypes-0.2 helper 程式碼，只有提供所產生類型的有限支援。</span><span class="sxs-lookup"><span data-stu-id="87235-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="87235-429">針對產生的型別定義，下列語句必須為 true：</span><span class="sxs-lookup"><span data-stu-id="87235-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="87235-430">`isErased`必須設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="87235-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="87235-431">產生的類型必須加入至新`ProvidedAssembly()`建立的，其代表產生之程式碼片段的容器。</span><span class="sxs-lookup"><span data-stu-id="87235-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="87235-432">提供者的元件必須具有實際支援的 .NET .dll 檔案，且該檔案在磁片上具有相符的 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="87235-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="87235-433">規則和限制</span><span class="sxs-lookup"><span data-stu-id="87235-433">Rules and Limitations</span></span>

<span data-ttu-id="87235-434">當您撰寫型別提供者時，請記住下列規則和限制。</span><span class="sxs-lookup"><span data-stu-id="87235-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="87235-435">提供的類型必須是可連線的</span><span class="sxs-lookup"><span data-stu-id="87235-435">Provided types must be reachable</span></span>

<span data-ttu-id="87235-436">所有提供的類型都應該可從非嵌套的類型連線。</span><span class="sxs-lookup"><span data-stu-id="87235-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="87235-437">在呼叫`TypeProviderForNamespaces`函式或`AddNamespace`呼叫時，會提供非嵌套的類型。</span><span class="sxs-lookup"><span data-stu-id="87235-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="87235-438">例如，如果提供者提供類型`StaticClass.P : T`，您必須確定 T 是非嵌套的類型，或在其底下嵌套。</span><span class="sxs-lookup"><span data-stu-id="87235-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="87235-439">例如，某些提供者具有包含這些`DataTypes` `T1, T2, T3, ...`類型的靜態類別，例如。</span><span class="sxs-lookup"><span data-stu-id="87235-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="87235-440">否則，錯誤會指出已找到元件 A 中類型 T 的參考，但在該元件中找不到類型。</span><span class="sxs-lookup"><span data-stu-id="87235-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="87235-441">如果出現此錯誤，請確認您的所有子類型都可以從提供者類型中取得。</span><span class="sxs-lookup"><span data-stu-id="87235-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="87235-442">注意:這些`T1, T2, T3...`類型稱為 *「即時」類型。*</span><span class="sxs-lookup"><span data-stu-id="87235-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="87235-443">請記得將它們放在可存取的命名空間或父類型中。</span><span class="sxs-lookup"><span data-stu-id="87235-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="87235-444">型別提供者機制的限制</span><span class="sxs-lookup"><span data-stu-id="87235-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="87235-445">中F#的型別提供者機制具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="87235-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="87235-446">中F#類型提供者的基礎結構不支援提供的泛型型別或提供的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="87235-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="87235-447">此機制不支援具有靜態參數的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="87235-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="87235-448">開發秘訣</span><span class="sxs-lookup"><span data-stu-id="87235-448">Development Tips</span></span>

<span data-ttu-id="87235-449">在開發過程中，您可能會發現下列秘訣很有説明：</span><span class="sxs-lookup"><span data-stu-id="87235-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="87235-450">執行 Visual Studio 的兩個實例</span><span class="sxs-lookup"><span data-stu-id="87235-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="87235-451">您可以在一個實例中開發類型提供者，並在另一個實例中測試該提供者，因為測試 IDE 將會鎖定 .dll 檔案，以避免重建類型提供者。</span><span class="sxs-lookup"><span data-stu-id="87235-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="87235-452">因此，在第一個實例中建立提供者時，您必須關閉 Visual Studio 的第二個實例，然後您必須在建立提供者之後重新開啟第二個實例。</span><span class="sxs-lookup"><span data-stu-id="87235-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="87235-453">使用 fsc 調用的 Debug 型別提供者</span><span class="sxs-lookup"><span data-stu-id="87235-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="87235-454">您可以使用下列工具來叫用型別提供者：</span><span class="sxs-lookup"><span data-stu-id="87235-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="87235-455">fsc .exe （ F#命令列編譯器）</span><span class="sxs-lookup"><span data-stu-id="87235-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="87235-456">fsi.exe .exe （ F#互動式編譯器）</span><span class="sxs-lookup"><span data-stu-id="87235-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="87235-457">devenv （Visual Studio）</span><span class="sxs-lookup"><span data-stu-id="87235-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="87235-458">您通常可以在測試腳本檔案（例如 run.fsx）上使用 fsc，輕鬆地對型別提供者進行最簡單的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="87235-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="87235-459">您可以從命令提示字元啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="87235-459">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="87235-460">您可以使用列印到 stdout 記錄。</span><span class="sxs-lookup"><span data-stu-id="87235-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="87235-461">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87235-461">See also</span></span>

- [<span data-ttu-id="87235-462">類型提供者</span><span class="sxs-lookup"><span data-stu-id="87235-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="87235-463">型別提供者 SDK</span><span class="sxs-lookup"><span data-stu-id="87235-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
