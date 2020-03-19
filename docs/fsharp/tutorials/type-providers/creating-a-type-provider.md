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
# <a name="tutorial-create-a-type-provider"></a>教程：創建類型提供程式

F# 中的類型提供程式機制是其支援資訊豐富程式設計的重要組成部分。 本教程介紹如何通過引導您完成幾個簡單類型提供程式的開發來說明基本概念，從而創建自己的類型提供程式。 有關 F# 中的類型提供程式機制的詳細資訊，請參閱[類型提供程式](index.md)。

F# 生態系統包含一系列用於常用 Internet 和企業資料服務的類型提供程式。 例如：

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/)包括 JSON、XML、CSV 和 HTML 文檔格式的類型提供程式。

- [SQLProvider](https://fsprojects.github.io/SQLProvider/)通過物件映射和針對這些資料來源的 F# LINQ 查詢提供對 SQL 資料庫的強型別訪問。

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)具有一組類型提供程式，用於在 F# 中編譯時檢查的 T-SQL 嵌入。

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是一組較舊的類型提供程式，僅用於 .NET 框架程式設計，用於訪問 SQL、實體框架、OData 和 WSDL 資料服務。

必要時，您可以創建自訂類型提供程式，也可以引用其他人創建的類型提供程式。 例如，您的組織可以有一個資料服務，該服務提供大量且不斷增加的命名資料集，每個資料集都有自己的穩定資料架構。 您可以創建一個類型提供程式，用於讀取架構，並以強型別方式向程式師顯示當前資料集。

## <a name="before-you-start"></a>開始之前

類型提供程式機制主要用於將穩定的資料和服務資訊空間注入 F# 程式設計體驗。

此機制不是為注入資訊空間而設計的，其架構在程式執行期間以與程式邏輯相關的方式更改。 此外，該機制不是為語言內部元程式設計而設計的，即使該域包含一些有效的用途。 僅當必要且類型提供程式的開發產生非常高的值時，才應使用此機制。

應避免編寫架構不可用的類型提供程式。 同樣，應避免編寫普通（甚至現有）.NET 庫就足夠了的類型提供程式。

在開始之前，您可能會提出以下問題：

- 您是否有資訊源的架構？ 如果是，則什麼是映射到 F# 和 .NET 類型系統？

- 能否使用現有（動態類型）API 作為實現的起點？

- 您和您的組織是否有足夠的類型提供程式的使用來使編寫它是值得的？ 普通的 .NET 庫能滿足您的需求嗎？

- 架構將更改多少？

- 在編碼過程中會發生變化嗎？

- 它會在編碼會話之間更改嗎？

- 在程式執行期間會更改嗎？

類型提供程式最適合在運行時和編譯代碼的存留期內架構穩定的情況。

## <a name="a-simple-type-provider"></a>簡單類型提供程式

此示例是示例。HelloWorldTypeProvider，類似于`examples`[F# 類型提供程式 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)目錄中的示例。 提供程式提供包含 100 種擦除類型的"類型空間"，如下代碼通過使用 F# 簽名語法和省略除 之外`Type1`的所有代碼的詳細資訊來顯示的。 有關擦除類型的詳細資訊，請參閱本主題後面的[有關已擦除提供類型的詳細資訊](#details-about-erased-provided-types)。

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

請注意，提供的類型和成員集是靜態已知的。 此示例不利用提供程式提供依賴于架構的類型的能力。 類型提供程式的實現在以下代碼中概述，本主題的後續部分將介紹詳細資訊。

> [!WARNING]
> 此代碼和連線示例之間可能存在差異。

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

要使用此提供程式，請打開 Visual Studio 的單獨實例，創建 F# 腳本，然後使用#r添加對提供程式的引用，如以下代碼所示：

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

然後查找類型提供程式生成的`Samples.HelloWorldTypeProvider`命名空間下的類型。

在重新編譯提供程式之前，請確保已關閉使用提供程式 DLL 的所有 Visual Studio 和 F# 互動式實例。 否則，將發生建置錯誤，因為輸出 DLL 將被鎖定。

要使用列印語句調試此提供程式，請製作一個顯示提供程式問題的腳本，然後使用以下代碼：

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

要使用 Visual Studio 調試此提供程式，請使用管理認證打開 Visual Studio 的開發人員命令提示符，並運行以下命令：

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

作為替代，打開 Visual Studio，打開調試功能表，選擇`Debug/Attach to process…`，並附加到編輯`devenv`腳本的其他進程。 通過使用此方法，您可以通過將運算式交互地鍵入第二個實例（具有完整的 IntelliSense 和其他功能）來更輕鬆地定位類型提供程式中的特定邏輯。

您可以禁用"僅我的代碼"調試，以便更好地識別生成的代碼中的錯誤。 有關如何啟用或禁用此功能的資訊，請參閱[使用調試器 通過代碼導航](/visualstudio/debugger/navigating-through-code-with-the-debugger)。 此外，您還可以通過打開`Debug`功能表，然後選擇或選擇`Exceptions`Ctrl_Alt_E 鍵來打開`Exceptions`對話方塊來設置第一次異常捕獲。 在該對話方塊中，在`Common Language Runtime Exceptions`下，`Thrown`選擇核取方塊。

### <a name="implementation-of-the-type-provider"></a>類型提供程式的實現

本節將介紹類型提供程式實現的主要部分。 首先，定義自訂類型提供程式本身的類型：

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

此類型必須是公共的，並且必須使用[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性標記它，以便編譯器在單獨的 F# 專案引用包含該類型的程式集時識別類型提供程式。 *配置*參數是可選的，如果存在，則包含 F# 編譯器創建的類型提供程式實例的上下文配置資訊。

接下來，實現[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。 在這種情況下，您將 API`TypeProviderForNamespaces`中的`ProvidedTypes`類型用作基本類型。 此説明器類型可以提供熱切提供的命名空間的有限集合，每個命名空間都直接包含有限數量的固定、熱切提供的類型。 在此上下文中，提供程式*熱切地*組建類型，即使它們不需要或使用。

```fsharp
inherit TypeProviderForNamespaces(config)
```

接下來，定義指定提供類型的命名空間的本地私有值，並查找類型提供程式程式集本身。 稍後，此程式集用作提供的擦除類型的邏輯父類型。

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

接下來，創建一個函數來提供 Type1...類型 100。 本主題稍後將更詳細地介紹此功能。

```fsharp
let makeOneProvidedType (n:int) = …
```

接下來，生成 100 個提供的類型：

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

接下來，將類型添加為提供的命名空間：

```fsharp
do this.AddNamespace(namespaceName, types)
```

最後，添加一個程式集屬性，指示要創建類型提供程式 DLL：

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>提供一種類型及其成員

函數`makeOneProvidedType`執行提供其中一種類型的實際工作。

```fsharp
let makeOneProvidedType (n:int) =
…
```

此步驟解釋了此函數的實現。 首先，創建提供的類型（例如，類型 1，當 n = 1 時，或 Type57，當 n = 57）。

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

您應該注意以下幾點：

- 此提供的類型將被刪除。  由於您指示基類型為`obj`，因此實例將在編譯代碼中顯示為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)類型的值。

- 指定非巢狀型別時，必須指定程式集和命名空間。 對於擦除的類型，程式集應是類型提供程式程式集本身。

接下來，將 XML 文檔添加到類型中。 本文檔延遲，即，如果主機編譯器需要，則按需計算。

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

接下來，向類型添加提供的靜態屬性：

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

獲取此屬性將始終評估到字串"你好！ 屬性`GetterCode`使用 F# 引號，它表示主機編譯器為獲取該屬性而生成的代碼。 有關報價單的詳細資訊，請參閱[代碼報價 （F#）。](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)

將 XML 文檔添加到屬性。

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

現在，將提供的屬性附加到提供的類型。 您必須將提供的成員附加到一種和僅一種類型。 否則，該成員將永遠無法訪問。

```fsharp
t.AddMember staticProp
```

現在創建一個不需要參數的提供的建構函式。

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

構造`InvokeCode`函數返回一個 F# 引號，它表示在調用建構函式時主機編譯器生成的代碼。 例如，可以使用以下建構函式：

```fsharp
new Type10()
```

使用基礎資料"物件資料"創建提供的類型的實例。 引號代碼包括轉換為[obj，](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型是此提供類型的擦除（如您聲明提供的類型時指定的）。

將 XML 文檔添加到建構函式，並將提供的建構函式添加到提供的類型：

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

創建第二個提供的建構函式，該建構函式採用一個參數：

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

構造`InvokeCode`函數的 引號再次返回一個 F# 引號，它表示主機編譯器為調用 方法生成的代碼。 例如，可以使用以下建構函式：

```fsharp
new Type10("ten")
```

使用基礎資料"10"創建提供的類型的實例。 您可能已經注意到函數`InvokeCode`返回引號。 此函數的輸入是運算式清單，每個建構函式參數一個。 在這種情況下，表示單個參數值的運算式在 中`args.[0]`可用。 調用建構函式的代碼強制傳回值到擦除的類型`obj`。 將第二個提供的建構函式添加到類型後，將創建一個提供的實例屬性：

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

獲取此屬性將返回字串的長度，該長度是表示物件。 該`GetterCode`屬性返回一個 F# 引號，該引號指定主機編譯器為獲取該屬性而生成的代碼。 與`InvokeCode`一`GetterCode`樣，函數返回引號。 主機編譯器使用參數清單調用此函數。 在這種情況下，參數僅包括表示調用 getter 的實例的單個運算式，您可以使用 訪問 該運算式`args.[0]`。 `GetterCode`然後在擦除類型`obj`中拼接到結果引號中的實現，以及強制轉換用於滿足編譯器檢查物件是字串的類型的機制。 的下`makeOneProvidedType`一部分提供了一個實例方法，其中有一個參數。

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

最後，創建包含 100 個嵌套屬性的巢狀型別。 此巢狀型別的創建及其屬性延遲，即按需計算。

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

### <a name="details-about-erased-provided-types"></a>有關已擦除提供的類型的詳細資訊

本節中的示例僅提供*擦除的提供類型*，這些類型在以下情況下特別有用：

- 為僅包含資料和方法的資訊空間編寫提供程式時。

- 編寫提供程式時，準確運行時類型的語義對於實際使用資訊空間並不重要。

- 當您為資訊空間編寫提供程式時，該提供程式非常大且相互關聯，因此在技術上為資訊空間生成真正的 .NET 類型是不可行的。

在此示例中，每個提供的類型將擦除為類型`obj`，並且該類型的所有用途都將在編譯的代碼中顯示為類型`obj`。 事實上，這些示例中的基礎物件是字串，但類型將顯示為`System.Object`.NET 編譯代碼中。 與類型擦除的所有用途一樣，您可以使用顯式裝箱、取消裝箱和強制轉換來顛覆擦除的類型。 在這種情況下，當使用物件時，可能會出現不正確強制轉換異常。 提供程式運行時可以定義其自己的私有表示類型，以説明防止虛假陳述。 不能在 F# 本身中定義已擦除的類型。 只能擦除提供的類型。 您必須瞭解為類型提供程式或提供擦除類型的提供程式使用擦除類型的後果（無論是實際的還是語義的）。 擦除的類型沒有實際的 .NET 類型。 因此，您不能對類型進行準確反射，如果使用運行時強制轉換和其他依賴于精確運行時類型語義的技術，則可能會顛覆擦除的類型。 擦除類型的顛覆經常導致運行時的類型強制異常。

### <a name="choosing-representations-for-erased-provided-types"></a>為已擦除的提供類型選擇表示形式

對於已擦除提供的類型的某些用途，不需要表示形式。 例如，擦除的提供類型可能僅包含靜態屬性和成員，並且不包含建構函式，並且任何方法或屬性都無法返回類型的實例。 如果可以到達已擦除提供的類型的實例，則必須考慮以下問題：

**提供類型的擦除是什麼？**

- 提供類型的擦除是該類型在編譯的 .NET 代碼中的顯示方式。

- 提供的擦除類類型的擦除始終是類型繼承鏈中的第一個未擦除基類型。

- 提供的擦除介面類別型的擦除始終`System.Object`為 。

**提供的類型的表示形式是什麼？**

- 擦除提供的類型的可能物件的集稱為其表示形式。 在本文檔中的示例中，所有擦除提供的類型的`Type1..Type100`表示形式始終是字串物件。

提供類型的所有表示形式必須與提供的類型的擦除相容。 （否則，F# 編譯器將給出使用類型提供程式的錯誤，或者將生成不正確不可驗證的 .NET 代碼。 如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。

可以使用以下任一方法為提供的物件選擇表示形式，這兩種方法都很常見：

- 如果只是在現有 .NET 類型上提供強型別包裝，則類型通常可以擦除到該類型，使用該類型的實例作為表示，或者兩者兼而有之。 當使用強型別版本時，該類型上的大多數現有方法仍然有意義時，此方法是合適的。

- 如果要創建與任何現有 .NET API 有顯著差異的 API，則創建運行時類型是提供的類型擦除和表示形式，這是有道理的。

本文檔中的示例使用字串作為提供物件的表示形式。 通常，使用其他物件進行表示可能很合適。 例如，您可以將字典用作屬性包：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

作為替代方法，您可以在類型提供程式中定義將在運行時用於形成表示的類型以及一個或多個運行時操作：

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

然後，如果成員可以構造此物件類型的實例：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

在這種情況下，您可以（有選擇地）在構造 時`baseType``ProvidedTypeDefinition`將此類型指定為

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>重點課程

上一節介紹了如何創建一個簡單的解排類型提供程式，該提供程式提供一系列類型、屬性和方法。 本節還解釋了類型擦除的概念，包括從類型提供程式提供擦除類型的一些優點和缺點，並討論了擦除類型的表示形式。

## <a name="a-type-provider-that-uses-static-parameters"></a>使用靜態參數的類型提供程式

通過靜態資料對類型提供程式進行參數化的能力支援許多有趣的方案，即使提供程式不需要訪問任何本地或遠端資料也是如此。 在本節中，您將學習一些組合此類提供程式的基本技術。

### <a name="type-checked-regex-provider"></a>鍵入已檢查的正則運算式提供程式

假設您要為正則運算式實現類型提供程式，該正則運算式在提供以下編譯時間<xref:System.Text.RegularExpressions.Regex>保證的介面中包裝 .NET 庫：

- 驗證正則運算式是否有效。

- 在基於正則運算式中的任何組名稱的匹配項上提供命名屬性。

本節介紹如何使用類型提供程式創建`RegexTyped`正則運算式模式參數化類別型以提供這些好處。 如果提供的模式無效，編譯器將報告錯誤，並且類型提供程式可以從模式中提取組，以便可以使用匹配上的命名屬性訪問這些組。 在設計類型提供程式時，應考慮其公開的 API 應如何查看最終使用者，以及此設計將如何轉換為 .NET 代碼。 下面的示例演示如何使用此類 API 獲取區號元件：

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

下面的示例顯示了類型提供程式如何轉換這些調用：

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

請注意下列幾點：

- 標準 Regex 類型表示參數化`RegexTyped`類型。

- 構造`RegexTyped`函數會導致對 Regex 建構函式的調用，從而傳入模式的靜態類型參數。

- `Match`該方法的結果由標準<xref:System.Text.RegularExpressions.Match>類型表示。

- 每個命名組都會導致提供的屬性，訪問該屬性會導致在匹配的集合`Groups`上使用索引子。

以下代碼是實現此類提供程式的邏輯的核心，此示例省略了向提供的類型添加所有成員。 有關每個添加成員的資訊，請參閱本主題後面的相應部分。 有關完整代碼，請從 CodePlex 網站上的[F# 3.0 示例包](https://archive.codeplex.com/?p=fsharp3sample)下載示例。

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

請注意下列幾點：

- 類型提供程式採用兩個靜態參數：`pattern`必填項和 可選的`options`。（因為提供了預設值）。

- 提供靜態參數後，將創建正則運算式的實例。 如果 Regex 格式不正確，此實例將引發異常，並且此錯誤將報告給使用者。

- 在回檔`DefineStaticParameters`中，定義提供參數後將返回的類型。

- 此代碼設置`HideObjectMethods`為 true，以便 IntelliSense 體驗將保持流線型。 此屬性會導致`Equals`從提供物件的`GetHashCode` `Finalize`IntelliSense 清單中禁止 、 和`GetType`成員。

- 使用作為`obj`方法的基礎類型，但您將使用`Regex`物件作為此類型的運行時表示形式，如下例所示。

- 當正則運算式`Regex`無效時，對<xref:System.ArgumentException>建構函式的調用將引發 。 編譯器捕獲此異常，並在編譯時或在 Visual Studio 編輯器中向使用者報告錯誤訊息。 此異常允許在不運行應用程式的情況下驗證正則運算式。

上面定義的類型還不用，因為它不包含任何有意義的方法或屬性。 首先，添加靜態`IsMatch`方法：

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

前面的代碼定義一個方法`IsMatch`，該方法以字串作為輸入並返回 。 `bool` 唯一棘手的部分是在`args``InvokeCode`定義中使用參數。 在此示例中，`args`是表示此方法的參數的報價單清單。 如果該方法是實例方法，則第一個參數表示參數`this`。 但是，對於靜態方法，參數都只是方法的顯式參數。 請注意，引號值的類型應與指定的返回類型匹配（在本例中為`bool`）。 另請注意，此代碼使用`AddXmlDoc`方法可確保提供的方法也具有有用的文檔，您可以通過 IntelliSense 提供這些文檔。

接下來，添加實例匹配方法。 但是，此方法應返回提供的`Match`類型的值，以便以強型別方式訪問組。 因此，您首先聲明類型`Match`。 由於此類型取決於作為靜態參數提供的模式，因此此類型必須嵌套在參數化型別定義中：

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

然後，向每個組的"匹配"類型添加一個屬性。 在運行時，匹配表示為<xref:System.Text.RegularExpressions.Match>值，因此定義屬性的報價單必須使用<xref:System.Text.RegularExpressions.Match.Groups>索引屬性來獲取相關組。

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

同樣，請注意，您將 XML 文檔添加到提供的屬性。 另請注意，如果提供了`GetterCode`函數，則可以讀取屬性，如果提供了`SetterCode`函數，則可以寫入該屬性，因此生成的屬性是唯讀的。

現在，您可以創建返回此`Match`類型值的實例方法：

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

因為您正在創建實例方法，表示`args.[0]`正在調用`RegexTyped`該方法的實例，並且`args.[1]`是輸入參數。

最後，提供一個建構函式，以便可以創建提供類型的實例。

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

建構函式僅擦除為創建標準 .NET Regex 實例，該實例再次盒裝到物件，因為`obj`是提供類型的擦除。 通過該更改，主題前面指定的示例 API 用法將按預期方式工作。 以下代碼已完成且最終：

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

### <a name="key-lessons"></a>重點課程

本節介紹如何創建對其靜態參數運行的類型提供程式。 提供程式檢查靜態參數，並根據其值提供操作。

## <a name="a-type-provider-that-is-backed-by-local-data"></a>由本地資料支援的類型提供程式

通常，您可能希望類型提供程式不僅基於靜態參數，還基於本地或遠端系統的資訊來顯示 API。 本節討論基於本地資料（如本地資料檔案）的類型提供程式。

### <a name="simple-csv-file-provider"></a>簡單的 CSV 檔提供程式

作為一個簡單的示例，請考慮一個類型提供程式，用於以逗號分隔值 （CSV） 格式訪問科學資料。 本節假定 CSV 檔包含標頭行，後跟浮點數據，如下表所示：

|距離（米）|時間（秒）|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

本節演示如何提供一種類型，可用於`Distance`獲取具有類型`float<meter>`屬性和類型的`Time``float<second>`屬性的行。 為簡單起見，我們做了以下假設：

- 標題名稱不是無單元的，或者有"名稱（單位）"的表單，並且不包含逗號。

- 單位均為[Microsoft.FSharp.Data.UnitSystems.SI.單元名稱模組 （F#）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義的系統國際 （SI） 單元。

- 單位都是簡單的（例如，儀錶），而不是複合的（例如，儀錶/秒）。

- 所有列都包含浮點數據。

更完整的供應商將放鬆這些限制。

同樣，第一步是考慮 API 的外觀。 假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

在這種情況下，編譯器應將這些調用轉換為類似以下示例的內容：

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

最佳轉換將要求類型提供程式在類型提供程式的程式集中定義`CsvFile`實際類型。 類型提供程式通常依賴于一些説明器類型和方法來包裝重要邏輯。 由於度量值在運行時被擦除，因此可以使用 作為`float[]`行的擦除類型。 編譯器將不同的列視為具有不同的度量數值型別。 例如，我們示例中的第一列具有類型`float<meter>`，第二列具有`float<second>`。 但是，擦除的表示形式可以保持非常簡單。

以下代碼顯示了實現的核心。

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

請注意有關實現的以下幾點：

- 重載建構函式允許讀取原始檔案或具有相同架構的檔。 當您為本地或遠端資料源編寫類型提供程式時，此模式很常見，並且此模式允許將本地檔用作遠端資料的範本。

- 您可以使用傳遞給類型提供程式建構函式的[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)值解析相對檔案名。

- 可以使用 方法`AddDefinitionLocation`定義提供的屬性的位置。 因此，如果您在提供的屬性`Go To Definition`上使用，CSV 檔將在 Visual Studio 中打開。

- 您可以使用 類型`ProvidedMeasureBuilder`查找 SI 單位並生成相關`float<_>`類型。

### <a name="key-lessons"></a>重點課程

本節介紹如何使用資料來源本身中包含的簡單架構為本地資料來源創建類型提供程式。

## <a name="going-further"></a>更進一步

以下各節包括進一步研究的建議。

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>查看已編譯的擦除類型代碼

為了讓您瞭解類型提供程式的使用如何與所發出的代碼相對應，請使用`HelloWorldTypeProvider`本主題前面使用的代碼來查看以下函數。

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

下面是使用 ildasm.exe 編譯的結果代碼的圖像：

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

如示例所示，所有提及的類型`Type1`和`InstanceProperty`屬性都已被刪除，僅保留有關運行時類型的操作。

### <a name="design-and-naming-conventions-for-type-providers"></a>類型提供程式的設計和命名約定

創作類型提供程式時，請遵守以下約定。

**連線協定的提供程式**通常，大多數提供程式 DlL 用於資料和服務連線協定（如 OData 或 SQL 連接）的名稱應以`TypeProvider``TypeProviders`或 結尾。 例如，使用類似于以下字串的 DLL 名稱：

`Fabrikam.Management.BasicTypeProviders.dll`

確保您提供的類型是相應命名空間的成員，並指示您實現的連線協定：

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**通用編碼提供程式**。  對於實用程式類型提供程式（如正則運算式提供程式），類型提供程式可能是基本庫的一部分，如下例所示：

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

在這種情況下，根據正常的 .NET 設計約定，提供的類型將顯示在適當的點：

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**單頓資料來源**. 某些類型提供程式連接到單個專用資料來源，並且僅提供資料。 在這種情況下，應刪除`TypeProvider`尾碼，並使用正常的約定進行 .NET 命名：

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

有關詳細資訊，請參閱本主題後面`GetConnection`介紹的設計約定。

### <a name="design-patterns-for-type-providers"></a>類型提供程式的設計模式

以下各節介紹在創作類型提供程式時可以使用的設計模式。

#### <a name="the-getconnection-design-pattern"></a>獲取連接設計模式

大多數類型提供程式都應編寫用於使用 FSharp.Data.TypeProvider.dll 中類型提供程式使用的`GetConnection`模式，如下例所示：

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>由遠端資料和服務支援的類型提供程式

在創建由遠端資料和服務支援的類型提供程式之前，必須考慮連接程式設計中固有的一系列問題。 這些問題包括以下注意事項：

- 架構映射

- 存在架構更改時的即時性和失效性

- 架構緩存

- 資料訪問操作的非同步實現

- 支援查詢，包括 LINQ 查詢

- 憑據和身份驗證

本主題沒有進一步探討這些問題。

### <a name="additional-authoring-techniques"></a>其他創作技術

編寫自己的類型提供程式時，可能需要使用以下附加技術。

### <a name="creating-types-and-members-on-demand"></a>按需創建類型和成員

提供類型 API 已延遲添加成員版本。

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

這些版本用於創建類型的按需空間。

### <a name="providing-array-types-and-generic-type-instantiations"></a>提供陣列類型和通用類型具現化

通過使用`MakeArrayType`法線 和`MakePointerType`的任何`MakeGenericType`實例<xref:System.Type>（包括`ProvidedTypeDefinitions`） 使提供的成員（其簽名包括陣列類型、byref 類型和泛型型別的實例）。

> [!NOTE]
> 在某些情況下，您可能需要在 中使用`ProvidedTypeBuilder.MakeGenericType`協助程式。  有關詳細資訊，請參閱[類型提供程式 SDK 文檔](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)。

### <a name="providing-unit-of-measure-annotations"></a>提供度量單位注釋

提供類型 API 提供用於提供度量值注釋的説明器。 例如，要提供類型`float<kg>`，請使用以下代碼：

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  要提供類型`Nullable<decimal<kg/m^2>>`，請使用以下代碼：

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>訪問專案-本地資源或腳本本地資源

類型提供程式的每個實例都可以在構造期間給出一`TypeProviderConfig`個值。 此值包含提供程式的"解析資料夾"（即編譯的專案資料夾或包含腳本的目錄）、引用程式集的清單和其他資訊。

### <a name="invalidation"></a>失效

提供程式可以引發失效信號，以通知 F# 語言服務架構假設可能已更改。 當發生失效時，如果提供程式在 Visual Studio 中託管，則重新檢查類型檢查。 當提供程式託管在 F# 互動式或 F# 編譯器 （fsc.exe） 中時，將忽略此信號。

### <a name="caching-schema-information"></a>緩存架構資訊

提供程式必須經常緩存對架構資訊的訪問。 緩存的資料應使用作為靜態參數或使用者資料給出的檔案名進行存儲。 架構緩存的一個示例是`LocalSchemaFile``FSharp.Data.TypeProviders`程式集類型提供程式中的參數。 在實現這些提供程式時，此靜態參數指示類型提供程式在指定的本地檔中使用架構資訊，而不是通過網路訪問資料來源。 要使用緩存的架構資訊，還必須將靜態參數`ForceUpdate`設置為`false`。 您可以使用類似的技術來啟用連線和離線資料訪問。

### <a name="backing-assembly"></a>支援程式集

編譯`.dll`或`.exe`檔時，生成的類型的備份 .DLL 檔案將靜態連結到生成的程式集中。 此連結是通過將中間語言 （IL） 類型定義和任何託管資源從備份程式集複製到最終程式集來創建的。 使用 F# 互動式時，不會複製支援 .DLL 檔案，而是直接載入到 F# 互動式進程中。

### <a name="exceptions-and-diagnostics-from-type-providers"></a>來自類型提供程式的異常和診斷

提供類型中所有成員的所有使用都可能會引發異常。 在所有情況下，如果類型提供程式引發異常，主機編譯器將錯誤屬性歸因於特定類型提供程式。

- 類型提供程式異常不應導致內部編譯器錯誤。

- 類型提供程式無法報告警告。

- 當類型提供程式託管在 F# 編譯器、F# 開發環境或 F# 互動式中時，將捕獲該提供程式的所有異常。 消息屬性始終是錯誤文本，並且不顯示堆疊追蹤。 如果要引發異常，可以引發以下示例： `System.NotSupportedException`、 `System.IO.IOException`。 `System.Exception`。

#### <a name="providing-generated-types"></a>提供生成的類型

到目前為止，本文檔已解釋如何提供擦除類型。 您還可以使用 F# 中的類型提供程式機制提供生成的類型，這些類型將作為真正的 .NET 類型定義添加到使用者的程式中。 您必須使用類型定義來引用生成的提供類型。

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

作為 F# 3.0 版本的一部分的"提供類型-0.2 説明器"代碼對提供生成的類型的支援有限。 對於生成的類型定義，以下語句必須為 true：

- `isErased` 必須設為 `false`。

- 生成的類型必須添加到新構造`ProvidedAssembly()`的 ，該類型表示生成的代碼片段的容器。

- 提供程式必須具有具有實際支援 .NET .DLL 檔案的程式集，該檔在磁片上具有匹配的 .DLL 檔案。

## <a name="rules-and-limitations"></a>規則和限制

編寫類型提供程式時，請記住以下規則和限制。

### <a name="provided-types-must-be-reachable"></a>提供的類型必須可到達

所有提供的類型都應從非巢狀型別中進行。 非巢狀型別在對`TypeProviderForNamespaces`建構函式的調用或對`AddNamespace`的調用中給出。 例如，如果提供程式提供類型`StaticClass.P : T`，則必須確保 T 是非巢狀型別或嵌套在一個類型下。

例如，某些提供程式具有包含這些`DataTypes``T1, T2, T3, ...`類型的靜態類。 否則，錯誤表示在程式集 A 中找到對類型 T 的引用，但在該程式集中找不到該類型。 如果出現此錯誤，請驗證可以從提供程式類型中到達所有子類型。 注意：這些`T1, T2, T3...`類型稱為*動態*類型。 請記住將它們放在可訪問的命名空間或父類型中。

### <a name="limitations-of-the-type-provider-mechanism"></a>類型提供程式機制的限制

F# 中的類型提供程式機制具有以下限制：

- F# 中類型提供程式的基礎基礎結構不支援提供泛型型別或提供泛型方法。

- 該機制不支援具有靜態參數的巢狀型別。

## <a name="development-tips"></a>開發秘訣

您可能會發現以下提示在開發過程中很有説明：

### <a name="run-two-instances-of-visual-studio"></a>運行視覺化工作室的兩個實例

您可以在一個實例中開發類型提供程式，並在另一個實例中測試提供程式，因為測試 IDE 將對 .DLL 檔案進行鎖定，以防止重新組建類型提供程式。 因此，在第一個實例中生成提供程式時，必須關閉 Visual Studio 的第二個實例，然後在構建提供程式後重新打開第二個實例。

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>使用 fsc.exe 調用調試類型提供程式

您可以使用以下工具調用類型提供程式：

- fsc.exe（F# 命令列編譯器）

- fsi.exe（F# 互動式編譯器）

- 德文夫.exe（視覺工作室）

通常，通過在測試指令檔（例如，腳本.fsx）上使用 fsc.exe，您通常最容易調試類型提供程式。 可以從命令提示符啟動調試器。

```console
devenv /debugexe fsc.exe script.fsx
```

  您可以使用列印到列印的日誌記錄。

## <a name="see-also"></a>另請參閱

- [類型提供者](index.md)
- [類型提供程式 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
