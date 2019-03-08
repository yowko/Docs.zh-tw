---
title: 教學課程：建立型別提供者
description: 了解如何建立您自己F#型別中的提供者F#3.0 藉由檢查幾個簡單的型別提供者，來說明基本概念。
ms.date: 02/02/2019
ms.openlocfilehash: 14e3035d03438aaaa2f6e64210f99e1f149db274
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678419"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="db585-103">教學課程：建立型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="db585-104">中的型別提供者機制F#是其支援資訊豐富程式設計的重要部分。</span><span class="sxs-lookup"><span data-stu-id="db585-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="db585-105">本教學課程說明如何建立您自己的型別提供者，方法是逐步說明的基本概念的幾個簡單的型別提供者的開發。</span><span class="sxs-lookup"><span data-stu-id="db585-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="db585-106">如需中的型別提供者機制F#，請參閱[型別提供者](index.md)。</span><span class="sxs-lookup"><span data-stu-id="db585-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="db585-107">F#生態系統包含一組常用的網際網路和企業資料服務的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="db585-108">例如: </span><span class="sxs-lookup"><span data-stu-id="db585-108">For example:</span></span>

- <span data-ttu-id="db585-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/)包含型別提供者，如 JSON、 XML、 CSV 和 HTML 文件格式。</span><span class="sxs-lookup"><span data-stu-id="db585-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="db585-110">[根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)可讓強型別存取透過 「 物件 」 對應的 SQL 資料庫和F#針對這些資料來源的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="db585-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="db585-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)編譯時期的型別提供者的一組簽入內嵌 T-SQL 中的F#。</span><span class="sxs-lookup"><span data-stu-id="db585-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="db585-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是較舊型別提供者只能搭配.NET Framework 程式設計中存取 SQL、 Entity Framework、 OData 及 WSDL 資料服務使用的集合。</span><span class="sxs-lookup"><span data-stu-id="db585-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="db585-113">必要時，您可以建立自訂的型別提供者，或您可以參考其他人所建立的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="db585-114">例如，您的組織可能會有提供大量且不斷增加的已命名的資料集，各有自己的穩定資料結構描述的資料服務。</span><span class="sxs-lookup"><span data-stu-id="db585-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="db585-115">您可以建立型別提供者讀取結構描述，並採用強類型的方式，呈現給程式設計人員的目前的資料集。</span><span class="sxs-lookup"><span data-stu-id="db585-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="db585-116">在開始之前</span><span class="sxs-lookup"><span data-stu-id="db585-116">Before You Start</span></span>

<span data-ttu-id="db585-117">型別提供者機制主要設計使插入穩定的資料和服務的資訊空間到F#程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="db585-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="db585-118">這項機制的目的不是讓您插入結構描述變更的相關程式邏輯的方式在程式執行期間的資訊空間。</span><span class="sxs-lookup"><span data-stu-id="db585-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="db585-119">此外，機制不被專為內部語言中繼程式設計，即使該網域包含一些有效的用法。</span><span class="sxs-lookup"><span data-stu-id="db585-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="db585-120">只有在必要時，您應該使用這項機制，其中的型別提供者開發會產生非常高的值。</span><span class="sxs-lookup"><span data-stu-id="db585-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="db585-121">您應該避免撰寫結構描述無法使用其中的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="db585-122">同樣地，您應該避免在一般 （或甚至有），撰寫型別提供者.NET 程式庫即已足夠。</span><span class="sxs-lookup"><span data-stu-id="db585-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="db585-123">在開始之前，您可能會詢問下列問題：</span><span class="sxs-lookup"><span data-stu-id="db585-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="db585-124">您有結構描述資訊來源？</span><span class="sxs-lookup"><span data-stu-id="db585-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="db585-125">因此，項目是否對應至F#和.NET 型別系統？</span><span class="sxs-lookup"><span data-stu-id="db585-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="db585-126">可以您使用現有的 （動態型別） API 做為起點實作？</span><span class="sxs-lookup"><span data-stu-id="db585-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="db585-127">將您和貴組織有不足，無法使用的型別提供者，可撰寫其值得嗎？</span><span class="sxs-lookup"><span data-stu-id="db585-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="db585-128">一般的.NET 程式庫會符合您的需求？</span><span class="sxs-lookup"><span data-stu-id="db585-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="db585-129">多少會變更您的結構描述？</span><span class="sxs-lookup"><span data-stu-id="db585-129">How much will your schema change?</span></span>

- <span data-ttu-id="db585-130">它會變更期間撰寫程式碼嗎？</span><span class="sxs-lookup"><span data-stu-id="db585-130">Will it change during coding?</span></span>

- <span data-ttu-id="db585-131">它將編碼工作階段之間變更嗎？</span><span class="sxs-lookup"><span data-stu-id="db585-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="db585-132">它會在程式執行期間變更嗎？</span><span class="sxs-lookup"><span data-stu-id="db585-132">Will it change during program execution?</span></span>

<span data-ttu-id="db585-133">型別提供者最適合的結構描述在執行階段和編譯的程式碼的存留期內穩定的情況。</span><span class="sxs-lookup"><span data-stu-id="db585-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="db585-134">簡單的型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-134">A Simple Type Provider</span></span>

<span data-ttu-id="db585-135">這個範例是中的範例類似 sampleproviders\providers`examples`目錄[F#型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)。</span><span class="sxs-lookup"><span data-stu-id="db585-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="db585-136">提供者會使用 「 類型空間 」，其中包含 100 清除的型別，為下列程式碼示範使用F#簽章語法和省略詳細資料，如以外的所有`Type1`。</span><span class="sxs-lookup"><span data-stu-id="db585-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="db585-137">如需清除類型的詳細資訊，請參閱 <<c0> [ 詳細資料的相關清除提供類型](#details-about-erased-provided-types)本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="db585-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="db585-138">請注意已確知的一組型別和成員提供。</span><span class="sxs-lookup"><span data-stu-id="db585-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="db585-139">此範例不會使用提供者能夠提供取決於結構描述的類型。</span><span class="sxs-lookup"><span data-stu-id="db585-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="db585-140">型別提供者實作會概述下列程式碼，以及本主題稍後的章節涵蓋詳細資料。</span><span class="sxs-lookup"><span data-stu-id="db585-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="db585-141">可能會有這段程式碼與線上範例之間的差異。</span><span class="sxs-lookup"><span data-stu-id="db585-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="db585-142">若要使用此提供者，請開啟 Visual Studio 的個別執行個體，建立F#指令碼，，然後再使用下列程式碼所示的 #r 新增從您的指令碼提供者的參考：</span><span class="sxs-lookup"><span data-stu-id="db585-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="db585-143">然後尋找下方類型`Samples.HelloWorldTypeProvider`型別提供者產生的命名空間。</span><span class="sxs-lookup"><span data-stu-id="db585-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="db585-144">重新編譯提供者之前，請確定您已關閉所有 Visual Studio 執行個體和F#會使用提供者 DLL 的互動。</span><span class="sxs-lookup"><span data-stu-id="db585-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="db585-145">因為輸出 DLL 將會遭到鎖定，否則會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="db585-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="db585-146">若要使用 print 陳述式，偵錯此提供者，請公開 （expose） 的提供者的問題的指令碼並接著使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="db585-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="db585-147">若要使用 Visual Studio 偵錯此提供者，使用系統管理認證，開啟適用於 Visual Studio 的開發人員命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="db585-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="db585-148">或者，開啟 Visual Studio，開啟 偵錯 功能表，選擇`Debug/Attach to process…`，並將附加至另一個`devenv`您要在其中編輯指令碼的程序。</span><span class="sxs-lookup"><span data-stu-id="db585-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="db585-149">使用此方法，您可以更輕鬆地以互動方式 （使用完整的 IntelliSense 和其他功能） 的第二個執行個體中輸入運算式目標型別提供者中的特定邏輯。</span><span class="sxs-lookup"><span data-stu-id="db585-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="db585-150">您可以停用 Just My Code 偵錯，以更精確識別產生程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="db585-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="db585-151">如需有關如何啟用或停用這項功能的資訊，請參閱 <<c0> [ 使用偵錯工具巡覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。</span><span class="sxs-lookup"><span data-stu-id="db585-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="db585-152">此外，您也可以設定開啟攔截 first-chance 例外狀況`Debug`功能表，然後選擇`Exceptions`或 [選擇 Ctrl + Alt + E 鍵以開啟`Exceptions`] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db585-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="db585-153">在該對話方塊中，在`Common Language Runtime Exceptions`，選取`Thrown`核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db585-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="db585-154">型別提供者實作</span><span class="sxs-lookup"><span data-stu-id="db585-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="db585-155">本節會引導您的型別提供者實作的主要區段。</span><span class="sxs-lookup"><span data-stu-id="db585-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="db585-156">首先，您可以定義型別本身的自訂型別提供者：</span><span class="sxs-lookup"><span data-stu-id="db585-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="db585-157">這種類型必須是公用，而且必須加以標示[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性，讓編譯器會辨識的型別提供者時不同的F#專案會參考該組件包含的類型。</span><span class="sxs-lookup"><span data-stu-id="db585-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="db585-158">*Config*參數為選擇性，而且，如果有的話，包含內容的組態資訊的型別提供者執行個體的F#編譯器會建立。</span><span class="sxs-lookup"><span data-stu-id="db585-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="db585-159">接下來，您會實作[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。</span><span class="sxs-lookup"><span data-stu-id="db585-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="db585-160">在此案例中，您會使用`TypeProviderForNamespaces`從輸入`ProvidedTypes`API 的基底類型。</span><span class="sxs-lookup"><span data-stu-id="db585-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="db585-161">此協助程式類型可以立即提供有限的集合，提供命名空間，其中每一個直接包含有限數量的其修正中，立即提供型別。</span><span class="sxs-lookup"><span data-stu-id="db585-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="db585-162">在此情況下，提供者*提早*產生型別，即使它們不需要或使用。</span><span class="sxs-lookup"><span data-stu-id="db585-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="db585-163">接下來，定義本機私用的值，指定的命名空間提供的類型，並尋找型別提供者組件本身。</span><span class="sxs-lookup"><span data-stu-id="db585-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="db585-164">這個組件做為項目的邏輯父類型的類型清除所提供的更新版本。</span><span class="sxs-lookup"><span data-stu-id="db585-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="db585-165">接下來，建立函數，以提供每個型別 Type1...Type100。</span><span class="sxs-lookup"><span data-stu-id="db585-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="db585-166">本主題稍後更詳細地說明此函式。</span><span class="sxs-lookup"><span data-stu-id="db585-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="db585-167">接下來，產生 100 提供的類型：</span><span class="sxs-lookup"><span data-stu-id="db585-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="db585-168">接下來，新增類型為提供的命名空間：</span><span class="sxs-lookup"><span data-stu-id="db585-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="db585-169">最後，新增組件的屬性，指出您要建立型別提供者 DLL:</span><span class="sxs-lookup"><span data-stu-id="db585-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="db585-170">提供一種類型和其成員</span><span class="sxs-lookup"><span data-stu-id="db585-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="db585-171">`makeOneProvidedType`函式會提供一種類型的實際工作。</span><span class="sxs-lookup"><span data-stu-id="db585-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="db585-172">此步驟說明此函式的實作。</span><span class="sxs-lookup"><span data-stu-id="db585-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="db585-173">首先，建立 提供的型別 (例如 Type1，當 n = 1 或 Type57，當 n = 57)。</span><span class="sxs-lookup"><span data-stu-id="db585-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="db585-174">您應該注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="db585-174">You should note the following points:</span></span>

- <span data-ttu-id="db585-175">這提供型別會清除。</span><span class="sxs-lookup"><span data-stu-id="db585-175">This provided type is erased.</span></span>  <span data-ttu-id="db585-176">因為您指定的基底類型是`obj`，執行個體將會顯示為類型的值[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)中編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="db585-177">當您指定的非巢狀型別時，您必須指定組件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="db585-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="db585-178">對於它們的類型，應該將組件類型提供者組件本身。</span><span class="sxs-lookup"><span data-stu-id="db585-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="db585-179">接下來，加入類型的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="db585-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="db585-180">這份文件會延遲，也就是，如果主機編譯器需要計算點播。</span><span class="sxs-lookup"><span data-stu-id="db585-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="db585-181">接下來將提供的靜態屬性加入類型：</span><span class="sxs-lookup"><span data-stu-id="db585-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="db585-182">取得這個屬性一律會評估為字串"Hello ！"。</span><span class="sxs-lookup"><span data-stu-id="db585-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="db585-183">`GetterCode`屬性會使用F#引號，表示主編譯器產生的取得此屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="db585-184">如需有關引號的詳細資訊，請參閱 <<c0> [ 程式碼引號 (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。</c0></span><span class="sxs-lookup"><span data-stu-id="db585-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="db585-185">將 XML 文件加入至屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="db585-186">現在提供的型別中附加所提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="db585-187">您必須將提供的成員附加至只能有一個型別。</span><span class="sxs-lookup"><span data-stu-id="db585-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="db585-188">否則，成員絕對不會存取。</span><span class="sxs-lookup"><span data-stu-id="db585-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="db585-189">現在建立提供的建構函式未採用參數。</span><span class="sxs-lookup"><span data-stu-id="db585-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="db585-190">`InvokeCode`的建構函式會傳回F#引號，代表呼叫建構函式時，主編譯器產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="db585-191">例如，您可以使用下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="db585-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="db585-192">提供型別的執行個體將會建立與基礎資料 「 物件資料 」。</span><span class="sxs-lookup"><span data-stu-id="db585-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="db585-193">加上引號的程式碼包含到轉換[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型的清除提供此型別 （如您指定當您宣告提供的型別）。</span><span class="sxs-lookup"><span data-stu-id="db585-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="db585-194">將 XML 文件加入建構函式，然後將提供的建構函式提供的型別：</span><span class="sxs-lookup"><span data-stu-id="db585-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="db585-195">建立的第二個提供建構函式會採用一個參數：</span><span class="sxs-lookup"><span data-stu-id="db585-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="db585-196">`InvokeCode`建構函式一次傳回的F#引號，表示主編譯器產生的方法呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="db585-197">例如，您可以使用下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="db585-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="db585-198">提供型別的執行個體被建立與基礎資料 「 10 」。</span><span class="sxs-lookup"><span data-stu-id="db585-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="db585-199">您可能已經發現，`InvokeCode`函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="db585-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="db585-200">此函式的輸入是運算式，其中每個建構函式參數清單。</span><span class="sxs-lookup"><span data-stu-id="db585-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="db585-201">在此案例中，代表單一參數值的運算式是用於`args.[0]`。</span><span class="sxs-lookup"><span data-stu-id="db585-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="db585-202">建構函式呼叫的程式碼強制清除類型的傳回值轉型`obj`。</span><span class="sxs-lookup"><span data-stu-id="db585-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="db585-203">您將第二個提供的建構函式加入至型別之後，您會建立提供的執行個體屬性：</span><span class="sxs-lookup"><span data-stu-id="db585-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="db585-204">取得這個屬性會傳回字串，表示物件的長度。</span><span class="sxs-lookup"><span data-stu-id="db585-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="db585-205">`GetterCode`屬性會傳回F#，指定要取得其屬性的主編譯器產生的程式碼引號。</span><span class="sxs-lookup"><span data-stu-id="db585-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="db585-206">像是`InvokeCode`，則`GetterCode`函式會傳回引號。</span><span class="sxs-lookup"><span data-stu-id="db585-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="db585-207">主機編譯器會呼叫此函式的引數清單。</span><span class="sxs-lookup"><span data-stu-id="db585-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="db585-208">在此情況下，引數包含只是單一運算式，表示執行個體的呼叫 getter，您可以存取使用`args.[0]`。實作`GetterCode`然後將結果的引號在清除輸入到 splices `obj`，並轉型來滿足編譯器的機制，來檢查此物件是字串類型。</span><span class="sxs-lookup"><span data-stu-id="db585-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="db585-209">下一個部分`makeOneProvidedType`提供一個參數的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="db585-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="db585-210">最後，建立巢狀的類型，其中包含 100 個巢狀的屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="db585-211">這個建立巢狀類型和其屬性會延遲，也就是，計算點播。</span><span class="sxs-lookup"><span data-stu-id="db585-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="db585-212">它們提供類型的詳細資料</span><span class="sxs-lookup"><span data-stu-id="db585-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="db585-213">在這一節，提供僅*清除所提供的型別*，這是在下列情況中特別有用：</span><span class="sxs-lookup"><span data-stu-id="db585-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="db585-214">當您在撰寫只包含資料和方法的資訊空間的提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="db585-215">當您在撰寫正確的執行階段型別語意不重要的資訊空間的實際用途是提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="db585-216">當您在撰寫且因此大型互連，不產生真正的.NET 類型的資訊空間技術上可行的資訊空間的提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="db585-217">在此範例中，提供的每一個型別會清除輸入`obj`，所有使用的類型會都顯示為型別及`obj`中編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="db585-218">事實上，在這些範例中的基礎物件是字串，但類型會顯示為`System.Object`在.NET 中編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="db585-219">所有使用的類型清除，您可以使用明確的 boxing 處理，unboxing，並將轉換可以破壞清除類型。</span><span class="sxs-lookup"><span data-stu-id="db585-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="db585-220">在此情況下，使用物件時，可能會造成無效轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db585-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="db585-221">提供者執行階段可以定義自己的私用表示型別，以協助防範 false 表示法。</span><span class="sxs-lookup"><span data-stu-id="db585-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="db585-222">您不能定義中清除的型別F#本身。</span><span class="sxs-lookup"><span data-stu-id="db585-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="db585-223">提供的類型可能會被刪除。</span><span class="sxs-lookup"><span data-stu-id="db585-223">Only provided types may be erased.</span></span> <span data-ttu-id="db585-224">您必須了解後果，這兩個實際會加以語意，使用 清除您的型別提供者或提供的提供者的類型清除類型。</span><span class="sxs-lookup"><span data-stu-id="db585-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="db585-225">它們的類型都有沒有真正的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="db585-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="db585-226">因此，您無法準確的反映類型，而且您可能會破壞它們的型別，如果您使用執行階段轉換和其他技術，依賴確切執行階段型別語意。</span><span class="sxs-lookup"><span data-stu-id="db585-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="db585-227">清除類型的 subversion 經常會導致在執行階段的類型轉換例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db585-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="db585-228">選擇表示法，如清除所提供的類型</span><span class="sxs-lookup"><span data-stu-id="db585-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="db585-229">如需清除的提供類型的一些用途，不表示需要。</span><span class="sxs-lookup"><span data-stu-id="db585-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="db585-230">比方說，它們提供型別可能會包含靜態屬性和成員並沒有建構函式，而沒有方法或屬性，則會傳回型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db585-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="db585-231">如果您可以連線到它們的執行個體提供型別，您必須考慮下列問題：</span><span class="sxs-lookup"><span data-stu-id="db585-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="db585-232">**在提供型別的清除是什麼？**</span><span class="sxs-lookup"><span data-stu-id="db585-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="db585-233">在提供型別的清除是類型出現在已編譯的.NET 程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="db585-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="db585-234">提供它們的類別型別的清除永遠是第一個非清除基底類型繼承鏈結中的型別。</span><span class="sxs-lookup"><span data-stu-id="db585-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="db585-235">提供的清除的介面型別的清除總是`System.Object`。</span><span class="sxs-lookup"><span data-stu-id="db585-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="db585-236">**提供的型別表示有哪些？**</span><span class="sxs-lookup"><span data-stu-id="db585-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="db585-237">一組可能的物件，為它們提供型別會呼叫其表示法。</span><span class="sxs-lookup"><span data-stu-id="db585-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="db585-238">在本文中範例中，所有清除所提供的表示型別`Type1..Type100`永遠是字串的物件。</span><span class="sxs-lookup"><span data-stu-id="db585-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="db585-239">所有提供的型別表示法必須與提供的類型清除相容。</span><span class="sxs-lookup"><span data-stu-id="db585-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="db585-240">(否則可能是F#編譯器將使用的型別提供者，會發生錯誤，或將會產生無法驗證不是有效的.NET 程式碼。</span><span class="sxs-lookup"><span data-stu-id="db585-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="db585-241">如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。</span><span class="sxs-lookup"><span data-stu-id="db585-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="db585-242">您可以使用下列其中一個方法，這兩者都是很常見的其中一種選擇提供物件的表示法：</span><span class="sxs-lookup"><span data-stu-id="db585-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="db585-243">如果您只需透過現有的.NET 型別提供強型別包裝函式，它通常適合您若要清除為該型別，表示法，或兩者皆為使用該類型的執行個體的類型。</span><span class="sxs-lookup"><span data-stu-id="db585-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="db585-244">當該類型上的現有方法的大部分仍能呼應使用強類型的版本時，適合使用這種方法。</span><span class="sxs-lookup"><span data-stu-id="db585-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="db585-245">如果您想要從任何現有的.NET API 大幅建立不同的 API，合理來建立要提供的類型的表示法與型別清除執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="db585-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="db585-246">這份文件中的範例會使用字串，以提供物件的表示法。</span><span class="sxs-lookup"><span data-stu-id="db585-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="db585-247">通常，可能適合用於表示法中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="db585-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="db585-248">比方說，您可能會使用字典，為屬性包：</span><span class="sxs-lookup"><span data-stu-id="db585-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="db585-249">或者，您可能在您將在執行階段用來形成的表示法，以及一或多個執行階段作業的型別提供者中定義類型：</span><span class="sxs-lookup"><span data-stu-id="db585-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="db585-250">提供的成員可以再建構此物件類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="db585-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="db585-251">在此情況下，您可能 （選擇性） 使用此類型為型別清除藉由指定為此型別`baseType`建構時`ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="db585-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="db585-252">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="db585-252">Key Lessons</span></span>

<span data-ttu-id="db585-253">上一節會說明如何建立簡單清除型別提供者提供了各式各樣的型別、 屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="db585-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="db585-254">本節也說明類型清除，包括的一些優點和缺點提供它們的型別從型別提供者的概念，並討論它們的類型表示法。</span><span class="sxs-lookup"><span data-stu-id="db585-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="db585-255">使用靜態參數的型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="db585-256">將參數化的靜態資料的型別提供者的能力可讓許多有趣的情況下，即使是在提供者不需要存取任何本機或遠端資料的情況下。</span><span class="sxs-lookup"><span data-stu-id="db585-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="db585-257">在本節中，您將學習一些基本技術搭配使用這類提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="db585-258">檢查 Regex 提供者類型。</span><span class="sxs-lookup"><span data-stu-id="db585-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="db585-259">假設您想要實作規則運算式的型別提供者包裝.NET<xref:System.Text.RegularExpressions.Regex>提供以下的編譯時期保證的介面中的程式庫：</span><span class="sxs-lookup"><span data-stu-id="db585-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="db585-260">正在驗證規則運算式是否有效。</span><span class="sxs-lookup"><span data-stu-id="db585-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="db585-261">提供比對規則運算式中的任何群組名稱為基礎的具名的屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="db585-262">本節說明如何使用型別提供者來建立`RegexTyped`輸入規則運算式模式會將參數化以提供這些優點。</span><span class="sxs-lookup"><span data-stu-id="db585-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="db585-263">如果提供的模式不是有效的而且型別提供者可以擷取群組模式中，讓您可以使用名為 比對的屬性來存取它們，編譯器會報告發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="db585-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="db585-264">當您設計型別提供者時，您應該考慮其公開的 API 外觀一般使用者與此設計會轉譯成.NET 程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="db585-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="db585-265">下列範例示範如何使用這類 API 來取得區域程式碼的元件：</span><span class="sxs-lookup"><span data-stu-id="db585-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="db585-266">下列範例會顯示型別提供者將這些呼叫的轉譯：</span><span class="sxs-lookup"><span data-stu-id="db585-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="db585-267">請注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="db585-267">Note the following points:</span></span>

- <span data-ttu-id="db585-268">標準的 Regex 型別代表參數化`RegexTyped`型別。</span><span class="sxs-lookup"><span data-stu-id="db585-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="db585-269">`RegexTyped` Regex 建構函式、 靜態型別引數的模式比對中的呼叫會產生建構函式。</span><span class="sxs-lookup"><span data-stu-id="db585-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="db585-270">結果`Match`方法都由標準<xref:System.Text.RegularExpressions.Match>型別。</span><span class="sxs-lookup"><span data-stu-id="db585-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="db585-271">提供的屬性，會產生每個具名的群組，並存取屬性的相符項目上的索引子會產生`Groups`集合。</span><span class="sxs-lookup"><span data-stu-id="db585-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="db585-272">下列的程式碼來實作這類提供者，邏輯的核心，而且這個範例省略了提供的型別所有成員的加入。</span><span class="sxs-lookup"><span data-stu-id="db585-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="db585-273">如需每個新增的成員，請參閱本主題稍後的適當區段。</span><span class="sxs-lookup"><span data-stu-id="db585-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="db585-274">完整的程式碼，下載範例[ F# 3.0 範例套件](https://archive.codeplex.com/?p=fsharp3sample)CodePlex 網站上。</span><span class="sxs-lookup"><span data-stu-id="db585-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="db585-275">請注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="db585-275">Note the following points:</span></span>

- <span data-ttu-id="db585-276">型別提供者會採用兩個靜態參數： `pattern`，這是必要項目，而`options`，這是選擇性的 （因為提供的預設值）。</span><span class="sxs-lookup"><span data-stu-id="db585-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="db585-277">提供靜態引數之後，您會建立規則運算式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db585-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="db585-278">如果 Regex 的格式不正確，而且使用者將會報告此錯誤，這個執行個體將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db585-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="db585-279">內`DefineStaticParameters`回呼中，您定義之後提供的引數，將傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="db585-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="db585-280">此程式碼會設定`HideObjectMethods`為 true，讓 IntelliSense 體驗將會保持精簡。</span><span class="sxs-lookup"><span data-stu-id="db585-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="db585-281">這個屬性會導致`Equals`， `GetHashCode`， `Finalize`，和`GetType`来隱藏的成員從 IntelliSense 清單中提供的物件。</span><span class="sxs-lookup"><span data-stu-id="db585-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="db585-282">您使用`obj`作為基底類型的方法，但您將使用`Regex`物件做為下一個範例會示範這種執行階段表示。</span><span class="sxs-lookup"><span data-stu-id="db585-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="db585-283">若要在呼叫`Regex`建構函式會擲回<xref:System.ArgumentException>當規則運算式不是有效的。</span><span class="sxs-lookup"><span data-stu-id="db585-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="db585-284">編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者回報的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="db585-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="db585-285">這個例外狀況可讓規則運算式，而不需執行應用程式進行驗證。</span><span class="sxs-lookup"><span data-stu-id="db585-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="db585-286">上面所定義的型別尚未有用因為它並未包含任何有意義的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="db585-287">首先，新增靜態`IsMatch`方法：</span><span class="sxs-lookup"><span data-stu-id="db585-287">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="db585-288">先前的程式碼定義的方法`IsMatch`，它會接受字串做為輸入，並傳回`bool`。</span><span class="sxs-lookup"><span data-stu-id="db585-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="db585-289">唯一比較麻煩的部分就是使用`args`內的引數`InvokeCode`定義。</span><span class="sxs-lookup"><span data-stu-id="db585-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="db585-290">在此範例中，`args`是引號，代表這個方法的引數清單。</span><span class="sxs-lookup"><span data-stu-id="db585-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="db585-291">如果方法是執行個體方法，第一個引數代表`this`引數。</span><span class="sxs-lookup"><span data-stu-id="db585-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="db585-292">不過，對於靜態方法，引數是只方法的明確引數。</span><span class="sxs-lookup"><span data-stu-id="db585-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="db585-293">請注意，加上引號的值的型別應該符合指定的傳回型別 (在此情況下， `bool`)。</span><span class="sxs-lookup"><span data-stu-id="db585-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="db585-294">另外請注意，此程式碼使用`AddXmlDoc`方法以確定提供的方法也有您可以透過 IntelliSense 提供的有用文件。</span><span class="sxs-lookup"><span data-stu-id="db585-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="db585-295">接下來，新增執行個體比對方法。</span><span class="sxs-lookup"><span data-stu-id="db585-295">Next, add an instance Match method.</span></span> <span data-ttu-id="db585-296">不過，此方法應傳回所提供的值`Match`型別，如此群組可以存取在強型別的方式。</span><span class="sxs-lookup"><span data-stu-id="db585-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="db585-297">因此，您首先宣告`Match`型別。</span><span class="sxs-lookup"><span data-stu-id="db585-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="db585-298">因為此類型取決於提供靜態引數作為模式，這種類型都必須在參數化型的別定義中巢狀結構：</span><span class="sxs-lookup"><span data-stu-id="db585-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="db585-299">然後，您會加入一個屬性為每個群組的相符項目型別。</span><span class="sxs-lookup"><span data-stu-id="db585-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="db585-300">在執行階段，以表示相符項目<xref:System.Text.RegularExpressions.Match>值，因此必須使用定義的屬性將引號<xref:System.Text.RegularExpressions.Match.Groups>編製索引的屬性，以取得相關的群組。</span><span class="sxs-lookup"><span data-stu-id="db585-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="db585-301">同樣地，請注意，您要將 XML 文件新增到所提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="db585-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="db585-302">另外請注意，如果可讀取的屬性`GetterCode`提供函式，和可寫入屬性，如果`SetterCode`提供函式，因此產生的屬性唯讀。</span><span class="sxs-lookup"><span data-stu-id="db585-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="db585-303">現在您可以建立傳回值，這個執行個體方法`Match`類型：</span><span class="sxs-lookup"><span data-stu-id="db585-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="db585-304">因為您會建立執行個體方法，`args.[0]`代表`RegexTyped`執行個體呼叫方法，和`args.[1]`是輸入引數。</span><span class="sxs-lookup"><span data-stu-id="db585-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="db585-305">最後，提供一個建構函式，以便可以建立的提供類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="db585-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="db585-306">建構函式只會清除建立標準的.NET Regex 執行個體，這會再次進行 boxed 處理物件因為`obj`是提供的類型清除。</span><span class="sxs-lookup"><span data-stu-id="db585-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="db585-307">這項變更，與本主題稍早所述的範例 API 使用量會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="db585-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="db585-308">下列程式碼是完整且最終：</span><span class="sxs-lookup"><span data-stu-id="db585-308">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="db585-309">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="db585-309">Key Lessons</span></span>

<span data-ttu-id="db585-310">本節說明如何建立能在其靜態參數的運作方式的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="db585-311">提供者會檢查靜態參數，並提供其值為基礎的作業。</span><span class="sxs-lookup"><span data-stu-id="db585-311">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="db585-312">型別提供者，並受到本機資料</span><span class="sxs-lookup"><span data-stu-id="db585-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="db585-313">通常，您可以呈現 Api 的靜態參數不僅從本機或遠端系統的資訊為基礎的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="db585-314">本章節將討論本機資料，例如本機資料檔案為基礎的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-314">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="db585-315">簡易的 CSV 檔案提供者</span><span class="sxs-lookup"><span data-stu-id="db585-315">Simple CSV File Provider</span></span>

<span data-ttu-id="db585-316">簡單的範例，請考慮用於存取以逗號分隔值 (CSV) 格式的科學資料的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="db585-317">本節假設，CSV 檔案包含標頭資料列，再浮動點資料，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="db585-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="db585-318">距離 （計量）</span><span class="sxs-lookup"><span data-stu-id="db585-318">Distance (meter)</span></span>|<span data-ttu-id="db585-319">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="db585-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="db585-320">50.0</span><span class="sxs-lookup"><span data-stu-id="db585-320">50.0</span></span>|<span data-ttu-id="db585-321">3.7</span><span class="sxs-lookup"><span data-stu-id="db585-321">3.7</span></span>|
|<span data-ttu-id="db585-322">100.0</span><span class="sxs-lookup"><span data-stu-id="db585-322">100.0</span></span>|<span data-ttu-id="db585-323">5.2</span><span class="sxs-lookup"><span data-stu-id="db585-323">5.2</span></span>|
|<span data-ttu-id="db585-324">150.0</span><span class="sxs-lookup"><span data-stu-id="db585-324">150.0</span></span>|<span data-ttu-id="db585-325">6.4</span><span class="sxs-lookup"><span data-stu-id="db585-325">6.4</span></span>|

<span data-ttu-id="db585-326">本節說明如何提供您可用來取得資料列型別`Distance`型別的屬性`float<meter>`並`Time`型別的屬性`float<second>`。</span><span class="sxs-lookup"><span data-stu-id="db585-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="db585-327">為了簡單起見，會進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="db585-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="db585-328">標頭名稱都是無單位或 「 名稱 （單位） 」 的格式，並不包含逗號。</span><span class="sxs-lookup"><span data-stu-id="db585-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="db585-329">單位是為所有系統 International (SI) 單位[Microsoft.FSharp.Data.UnitSystems.SI.UnitNames 模組 (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義。</span><span class="sxs-lookup"><span data-stu-id="db585-329">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="db585-330">單位是所有簡單 （例如，計量） 而不是複合 （比方說，計量表/秒）。</span><span class="sxs-lookup"><span data-stu-id="db585-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="db585-331">所有的資料行包含浮點數資料。</span><span class="sxs-lookup"><span data-stu-id="db585-331">All columns contain floating point data.</span></span>

<span data-ttu-id="db585-332">更完整的提供者會放寬這些限制。</span><span class="sxs-lookup"><span data-stu-id="db585-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="db585-333">同樣地，首先是 API 的外觀，請考慮。</span><span class="sxs-lookup"><span data-stu-id="db585-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="db585-334">假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="db585-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="db585-335">在此情況下，編譯器應該將這些呼叫轉換成類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="db585-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="db585-336">最佳的轉譯會需要型別提供者，來定義真實`CsvFile`型別提供者的組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="db585-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="db585-337">型別提供者通常需仰賴幾個協助程式類型和方法，來包裝重要邏輯而定。</span><span class="sxs-lookup"><span data-stu-id="db585-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="db585-338">由於量值就會清除在執行階段，您可以使用`float[]`做為清除類型的資料列。</span><span class="sxs-lookup"><span data-stu-id="db585-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="db585-339">編譯器會將不同的資料行視為具有不同的量值類型。</span><span class="sxs-lookup"><span data-stu-id="db585-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="db585-340">例如，在本例中的第一個資料行具有類型`float<meter>`，第二個`float<second>`。</span><span class="sxs-lookup"><span data-stu-id="db585-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="db585-341">不過，它們的表示可以保持相當簡單。</span><span class="sxs-lookup"><span data-stu-id="db585-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="db585-342">下列程式碼會顯示實作的核心。</span><span class="sxs-lookup"><span data-stu-id="db585-342">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="db585-343">請注意下列有關實作的重點：</span><span class="sxs-lookup"><span data-stu-id="db585-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="db585-344">原始檔或可讀取相同的結構描述，可讓多載的建構函式。</span><span class="sxs-lookup"><span data-stu-id="db585-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="db585-345">當您撰寫本機或遠端資料來源的型別提供者並將此模式可讓本機檔案做為遠端資料範本，此模式相當常見。</span><span class="sxs-lookup"><span data-stu-id="db585-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="db585-346">您可以使用[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)會傳遞至型別提供者建構函式，來解析相對檔案名稱中的值。</span><span class="sxs-lookup"><span data-stu-id="db585-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="db585-347">您可以使用`AddDefinitionLocation`方法來定義所提供的屬性位置。</span><span class="sxs-lookup"><span data-stu-id="db585-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="db585-348">因此，如果您使用`Go To Definition`上提供的屬性，CSV 檔案會在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="db585-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="db585-349">您可以使用`ProvidedMeasureBuilder`若要查詢的 SI 單位，並產生相關的型別`float<_>`型別。</span><span class="sxs-lookup"><span data-stu-id="db585-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="db585-350">索引鍵的課程</span><span class="sxs-lookup"><span data-stu-id="db585-350">Key Lessons</span></span>

<span data-ttu-id="db585-351">本節說明如何使用簡單的結構描述包含在資料來源本身中建立本機資料來源的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="db585-352">繼續進行</span><span class="sxs-lookup"><span data-stu-id="db585-352">Going Further</span></span>

<span data-ttu-id="db585-353">下列各節包含需進一步的研究的建議。</span><span class="sxs-lookup"><span data-stu-id="db585-353">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="db585-354">看看清除類型的已編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="db585-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="db585-355">為了讓您了解如何使用型別提供者對應，就會發出的程式碼，看看下列函式使用`HelloWorldTypeProvider`用稍早在本主題中。</span><span class="sxs-lookup"><span data-stu-id="db585-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="db585-356">以下是產生的程式碼使用 ildasm.exe 反向組譯的映像：</span><span class="sxs-lookup"><span data-stu-id="db585-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="db585-357">如範例所示，型別的所有提及`Type1`而`InstanceProperty`屬性已清除，保留所涉及的只有在執行階段型別上的作業。</span><span class="sxs-lookup"><span data-stu-id="db585-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="db585-358">設計和型別提供者的命名慣例</span><span class="sxs-lookup"><span data-stu-id="db585-358">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="db585-359">撰寫型別提供者時，請觀察下列慣例。</span><span class="sxs-lookup"><span data-stu-id="db585-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="db585-360">**提供者的連接通訊協定**一般而言，大部分的提供者 Dll 的資料和服務的連線通訊協定，例如 OData 或 SQL 連接時，名稱應該結束於`TypeProvider`或`TypeProviders`。</span><span class="sxs-lookup"><span data-stu-id="db585-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="db585-361">例如，使用類似如下的 DLL 名稱：</span><span class="sxs-lookup"><span data-stu-id="db585-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="db585-362">請確定您提供的型別是對應的命名空間的成員，並指出您所實作的連線通訊協定：</span><span class="sxs-lookup"><span data-stu-id="db585-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="db585-363">**撰寫一般程式碼的公用程式提供者**。</span><span class="sxs-lookup"><span data-stu-id="db585-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="db585-364">公用程式類型提供者，例如規則運算式，型別提供者可能屬於基底的程式庫，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="db585-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="db585-365">在此情況下，提供的型別會出現在適當的時間點，根據一般的.NET 設計慣例：</span><span class="sxs-lookup"><span data-stu-id="db585-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="db585-366">**單一資料來源**。</span><span class="sxs-lookup"><span data-stu-id="db585-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="db585-367">某些型別提供者連接到單一的專用的資料來源，並只提供資料。</span><span class="sxs-lookup"><span data-stu-id="db585-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="db585-368">在此情況下，您應該卸除`TypeProvider`後置詞，並使用一般的慣例，.NET 命名：</span><span class="sxs-lookup"><span data-stu-id="db585-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="db585-369">如需詳細資訊，請參閱`GetConnection`設計會在本主題稍後描述的慣例。</span><span class="sxs-lookup"><span data-stu-id="db585-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="db585-370">型別提供者設計模式</span><span class="sxs-lookup"><span data-stu-id="db585-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="db585-371">下列各節說明您可以撰寫型別提供者時使用的設計模式。</span><span class="sxs-lookup"><span data-stu-id="db585-371">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="db585-372">GetConnection 設計模式</span><span class="sxs-lookup"><span data-stu-id="db585-372">The GetConnection Design Pattern</span></span>

<span data-ttu-id="db585-373">大部分的型別提供者應撰寫成使用`GetConnection`模式，可由型別中的提供者 FSharp.Data.TypeProviders.dll，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="db585-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="db585-374">遠端資料和服務所支援的型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="db585-375">建立遠端資料和服務所支援的類型提供者之前，您必須考慮各種連線程式設計中固有的問題。</span><span class="sxs-lookup"><span data-stu-id="db585-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="db585-376">這些問題包括下列考量：</span><span class="sxs-lookup"><span data-stu-id="db585-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="db585-377">結構描述對應</span><span class="sxs-lookup"><span data-stu-id="db585-377">schema mapping</span></span>

- <span data-ttu-id="db585-378">作用與結構描述變更時失效</span><span class="sxs-lookup"><span data-stu-id="db585-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="db585-379">結構描述快取</span><span class="sxs-lookup"><span data-stu-id="db585-379">schema caching</span></span>

- <span data-ttu-id="db585-380">非同步處理實作的資料存取作業</span><span class="sxs-lookup"><span data-stu-id="db585-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="db585-381">支援的查詢，包括 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="db585-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="db585-382">認證和驗證</span><span class="sxs-lookup"><span data-stu-id="db585-382">credentials and authentication</span></span>

<span data-ttu-id="db585-383">本主題不會探索這些在進一步的問題。</span><span class="sxs-lookup"><span data-stu-id="db585-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="db585-384">其他的撰寫技術</span><span class="sxs-lookup"><span data-stu-id="db585-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="db585-385">當您撰寫您自己的型別提供者時，您可以使用下列其他技巧。</span><span class="sxs-lookup"><span data-stu-id="db585-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="db585-386">建立型別和成員依需求</span><span class="sxs-lookup"><span data-stu-id="db585-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="db585-387">ProvidedType API 已延遲 AddMember 的版本。</span><span class="sxs-lookup"><span data-stu-id="db585-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="db585-388">這些版本用來建立隨空間的型別。</span><span class="sxs-lookup"><span data-stu-id="db585-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="db585-389">提供陣列型別和泛型類型具現化</span><span class="sxs-lookup"><span data-stu-id="db585-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="db585-390">要提供的成員 （其簽章包含陣列類型、 byref 類型和具現化的泛型型別） 使用一般`MakeArrayType`， `MakePointerType`，並`MakeGenericType`任何執行個體上<xref:System.Type>，其中包括`ProvidedTypeDefinitions`。</span><span class="sxs-lookup"><span data-stu-id="db585-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="db585-391">在某些情況下，您可能必須使用這個 helper `ProvidedTypeBuilder.MakeGenericType`。</span><span class="sxs-lookup"><span data-stu-id="db585-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="db585-392">請參閱[型別提供者 SDK 文件](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="db585-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="db585-393">提供的量值註釋的單位</span><span class="sxs-lookup"><span data-stu-id="db585-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="db585-394">ProvidedTypes API 會提供協助程式，提供量值註釋。</span><span class="sxs-lookup"><span data-stu-id="db585-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="db585-395">例如，若要提供型別`float<kg>`，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="db585-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="db585-396">若要提供型別`Nullable<decimal<kg/m^2>>`，使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="db585-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="db585-397">存取專案-本機位址或指令碼-本機資源</span><span class="sxs-lookup"><span data-stu-id="db585-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="db585-398">您可以指定每個型別提供者執行個體`TypeProviderConfig`在建構期間的值。</span><span class="sxs-lookup"><span data-stu-id="db585-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="db585-399">此值包含 「 解析資料夾 」 提供者 （也就是編譯或包含的指令碼的目錄的專案資料夾）、 參考組件、 清單和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="db585-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="db585-400">失效</span><span class="sxs-lookup"><span data-stu-id="db585-400">Invalidation</span></span>

<span data-ttu-id="db585-401">提供者可能會引發失效的訊號，來通知F#的結構描述的假設可能已變更的語言服務。</span><span class="sxs-lookup"><span data-stu-id="db585-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="db585-402">失效時，如果提供者裝載在 Visual Studio 中，會重做 typecheck。</span><span class="sxs-lookup"><span data-stu-id="db585-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="db585-403">在裝載提供者時，將會忽略此訊號F#互動式或由F#編譯器 (fsc.exe)。</span><span class="sxs-lookup"><span data-stu-id="db585-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="db585-404">快取的結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="db585-404">Caching Schema Information</span></span>

<span data-ttu-id="db585-405">提供者通常必須快取結構描述資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="db585-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="db585-406">使用指定的檔案名稱，做為靜態參數，或做為使用者資料應該儲存快取的資料。</span><span class="sxs-lookup"><span data-stu-id="db585-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="db585-407">舉例來說，結構描述快取`LocalSchemaFile`參數中的型別提供者中`FSharp.Data.TypeProviders`組件。</span><span class="sxs-lookup"><span data-stu-id="db585-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="db585-408">在這些提供者實作中，此靜態的參數會指示型別提供者，用於指定的本機檔案，而不是透過網路存取的資料來源的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="db585-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="db585-409">若要使用快取的結構描述資訊，您也必須設定靜態參數`ForceUpdate`至`false`。</span><span class="sxs-lookup"><span data-stu-id="db585-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="db585-410">若要啟用線上和離線的資料存取，您可以使用類似的技巧。</span><span class="sxs-lookup"><span data-stu-id="db585-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="db585-411">備份組件</span><span class="sxs-lookup"><span data-stu-id="db585-411">Backing Assembly</span></span>

<span data-ttu-id="db585-412">當您編譯`.dll`或`.exe`檔案，支援.dll 檔案產生的型別以靜態方式連結到產生的組件。</span><span class="sxs-lookup"><span data-stu-id="db585-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="db585-413">從備份組件，到最終組件複製的中繼語言 (IL) 型別定義和任何受管理的資源會建立此連結。</span><span class="sxs-lookup"><span data-stu-id="db585-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="db585-414">當您使用F#Interactive，支援.dll 檔案不會複製，並會改為直接載入至F#互動式處理序。</span><span class="sxs-lookup"><span data-stu-id="db585-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="db585-415">例外狀況和診斷從型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="db585-416">從提供的類型的所有成員的所有使用可能會擲都回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db585-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="db585-417">在所有情況下，型別提供者會擲回的例外狀況，如果主機編譯器屬性錯誤的特定型別提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="db585-418">內部編譯器錯誤應該永遠不會產生型別提供者例外狀況。</span><span class="sxs-lookup"><span data-stu-id="db585-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="db585-419">型別提供者無法回報警告。</span><span class="sxs-lookup"><span data-stu-id="db585-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="db585-420">當型別提供者裝載在F#編譯器，F#開發環境，或F#互動式，會攔截所有例外狀況，該提供者。</span><span class="sxs-lookup"><span data-stu-id="db585-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="db585-421">訊息屬性一律會是錯誤的文字，並沒有堆疊追蹤會出現。</span><span class="sxs-lookup"><span data-stu-id="db585-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="db585-422">如果您將會擲回例外狀況，您可以擲回下列的範例： `System.NotSupportedException`， `System.IO.IOException`， `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="db585-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="db585-423">提供產生的型別</span><span class="sxs-lookup"><span data-stu-id="db585-423">Providing Generated Types</span></span>

<span data-ttu-id="db585-424">到目前為止，本文件說明如何提供它們的類型。</span><span class="sxs-lookup"><span data-stu-id="db585-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="db585-425">您也可以使用中的型別提供者機制F#若要提供產生的型別，這是加入量呈現真實的.NET 型別定義，到使用者的程式。</span><span class="sxs-lookup"><span data-stu-id="db585-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="db585-426">您必須參考產生提供使用型別定義的類型。</span><span class="sxs-lookup"><span data-stu-id="db585-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="db585-427">ProvidedTypes 0.2 協助程式程式碼屬於F#3.0 版只能進行有限的支援，提供產生的型別。</span><span class="sxs-lookup"><span data-stu-id="db585-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="db585-428">下列陳述式必須是產生的型別定義，則為 true:</span><span class="sxs-lookup"><span data-stu-id="db585-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="db585-429">`isErased` 必須設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="db585-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="db585-430">產生的型別必須新增至新建構`ProvidedAssembly()`，代表產生的程式碼片段的容器。</span><span class="sxs-lookup"><span data-stu-id="db585-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="db585-431">提供者必須具有相符的.dll 檔案，在磁碟上的實際支援.NET.dll 檔案的組件。</span><span class="sxs-lookup"><span data-stu-id="db585-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="db585-432">規則和限制</span><span class="sxs-lookup"><span data-stu-id="db585-432">Rules and Limitations</span></span>

<span data-ttu-id="db585-433">當您撰寫型別提供者時，請記住下列規則和限制。</span><span class="sxs-lookup"><span data-stu-id="db585-433">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="db585-434">提供的類型必須是可連線</span><span class="sxs-lookup"><span data-stu-id="db585-434">Provided types must be reachable</span></span>

<span data-ttu-id="db585-435">提供類型應該是可從非巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="db585-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="db585-436">呼叫中指定的非巢狀型別`TypeProviderForNamespaces`建構函式或呼叫`AddNamespace`。</span><span class="sxs-lookup"><span data-stu-id="db585-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="db585-437">例如，如果提供者提供的型別`StaticClass.P : T`，您必須確定 T 是在非巢狀型別或巢狀在下一個。</span><span class="sxs-lookup"><span data-stu-id="db585-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="db585-438">比方說，某些提供者都有靜態類別，如`DataTypes`，其中包含這些`T1, T2, T3, ...`型別。</span><span class="sxs-lookup"><span data-stu-id="db585-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="db585-439">否則，錯誤會指出，找不到組件 A 中的型別 T 的參考，但在該組件中找不到類型。</span><span class="sxs-lookup"><span data-stu-id="db585-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="db585-440">如果出現這個錯誤，請確認您所有的子類型，可從提供者類型。</span><span class="sxs-lookup"><span data-stu-id="db585-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="db585-441">注意:這些`T1, T2, T3...`類型指*上即時*型別。</span><span class="sxs-lookup"><span data-stu-id="db585-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="db585-442">請務必將它們放在可存取的命名空間或父類型。</span><span class="sxs-lookup"><span data-stu-id="db585-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="db585-443">型別提供者機制的限制</span><span class="sxs-lookup"><span data-stu-id="db585-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="db585-444">中的型別提供者機制F#具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="db585-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="db585-445">中的型別提供者的基礎結構F#不支援提供泛型類型，或提供泛型方法。</span><span class="sxs-lookup"><span data-stu-id="db585-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="db585-446">機制不支援巢狀的類型的靜態參數。</span><span class="sxs-lookup"><span data-stu-id="db585-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="db585-447">開發秘訣</span><span class="sxs-lookup"><span data-stu-id="db585-447">Development Tips</span></span>

<span data-ttu-id="db585-448">您可能會發現下列秘訣有助於在開發程序：</span><span class="sxs-lookup"><span data-stu-id="db585-448">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="db585-449">執行兩個 Visual Studio 執行個體</span><span class="sxs-lookup"><span data-stu-id="db585-449">Run two instances of Visual Studio</span></span>

<span data-ttu-id="db585-450">您可以開發一個執行個體中的型別提供者，並在其他測試提供者，因為測試的 IDE 會防止型別提供者正在重建的.dll 檔案採用鎖定。</span><span class="sxs-lookup"><span data-stu-id="db585-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="db585-451">因此，您必須先關閉 Visual Studio 的第二個執行個體，而第一個執行個體中，內建提供者，然後您就必須重新開啟第二個執行個體建立提供者後。</span><span class="sxs-lookup"><span data-stu-id="db585-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="db585-452">偵錯使用 fsc.exe 的引動過程的型別提供者</span><span class="sxs-lookup"><span data-stu-id="db585-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="db585-453">您可以使用下列工具，以叫用型別提供者：</span><span class="sxs-lookup"><span data-stu-id="db585-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="db585-454">fsc.exe (F#命令列編譯器)</span><span class="sxs-lookup"><span data-stu-id="db585-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="db585-455">fsi.exe ( F# Interactive 編譯器)</span><span class="sxs-lookup"><span data-stu-id="db585-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="db585-456">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="db585-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="db585-457">您可以經常使用偵錯型別提供者最容易 fsc.exe 的測試指令碼檔案 (例如 script.fsx)。</span><span class="sxs-lookup"><span data-stu-id="db585-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="db585-458">您可以啟動偵錯工具從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="db585-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="db585-459">您可以使用列印至 stdout 記錄。</span><span class="sxs-lookup"><span data-stu-id="db585-459">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="db585-460">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db585-460">See also</span></span>

- [<span data-ttu-id="db585-461">類型提供者</span><span class="sxs-lookup"><span data-stu-id="db585-461">Type Providers</span></span>](index.md)
- [<span data-ttu-id="db585-462">型別提供者 SDK</span><span class="sxs-lookup"><span data-stu-id="db585-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
