---
title: 教學課程：建立型別提供者
description: '瞭解如何在 F # 3.0 中建立您自己的 F # 型別提供者，方法是檢查數個簡單的型別提供者來說明基本概念。'
ms.date: 11/04/2019
ms.openlocfilehash: 65cb9616f66b5850135dbfcdd9b9a9dad30421de
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739694"
---
# <a name="tutorial-create-a-type-provider"></a>教學課程：建立型別提供者

F # 中的型別提供者機制是其對資訊豐富程式設計支援的重要部分。 本教學課程說明如何建立您自己的型別提供者，方法是逐步解說幾個簡單的型別提供者，以說明基本概念。 如需 F # 中型別提供者機制的詳細資訊，請參閱 [類型提供者](index.md)。

F # 生態系統包含一系列常用的網際網路和企業資料服務的類型提供者。 例如：

- [Fsharp.core](https://fsharp.github.io/FSharp.Data/) 包括 JSON、XML、CSV 和 HTML 檔案格式的類型提供者。

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) 可透過物件對應以及對這些資料來源的 F # LINQ 查詢，提供 SQL 資料庫的強型別存取。

- [Fsharp.core](https://fsprojects.github.io/FSharp.Data.SqlClient/) 有一組型別提供者，可用於在 F # 中，以編譯時間檢查的 t-sql。

- [Fsharp.core](https://fsprojects.github.io/FSharp.Data.TypeProviders/) 是一組較舊的型別提供者，僅供用來存取 SQL、Entity Framework、ODATA 和 WSDL Data services .NET Framework 程式設計。

您可以在必要時建立自訂型別提供者，也可以參考其他人所建立的型別提供者。 例如，您的組織可能會有一個資料服務，可提供大量且不斷增加的命名資料集，每個資料集都有自己的穩定資料架構。 您可以建立可讀取架構的型別提供者，並以強型別方式向程式設計師呈現目前的資料集。

## <a name="before-you-start"></a>開始之前

型別提供者機制主要是設計用來將穩定的資料和服務資訊空間插入 F # 程式設計體驗中。

這項機制並非設計用來插入資訊空間，其架構在程式執行期間會以與程式邏輯相關的方式進行變更。 此外，此機制不是針對語言中繼程式設計所設計，即使該網域包含一些有效的用途也一樣。 您應該只在必要時才使用此機制，而在開發型別提供者時會產生非常高的價值。

您應該避免撰寫無法使用架構的類型提供者。 同樣地，您應該避免撰寫一般 (或甚至是現有) .NET 程式庫都已足夠的類型提供者。

開始之前，您可能會詢問下列問題：

- 您有資訊來源的架構嗎？ 如果是，F # 和 .NET 類型系統的對應是什麼？

- 您可以使用現有的 (動態型別) API 做為您的實作為起點嗎？

- 您和您的組織是否有足夠的型別提供者使用，讓您有價值的撰寫？ 一般的 .NET 程式庫是否符合您的需求？

- 您的架構會變更多少？

- 在編碼期間是否會變更？

- 程式碼撰寫會話之間會變更嗎？

- 它會在程式執行期間變更嗎？

型別提供者最適合的情況是，架構在執行時間和編譯器代碼存留期間都是穩定的情況。

## <a name="a-simple-type-provider"></a>簡單類型提供者

此範例為 HelloWorldTypeProvider，類似于 `examples` [F # 型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)目錄中的範例。 提供者可以使用包含100清除類型的「類型空間」，如下列程式碼所示，使用 F # 簽章語法，並省略所有的詳細資料 `Type1` 。 如需已清除之類型的詳細資訊，請參閱本主題稍後的已 [清除提供類型的詳細資料](#details-about-erased-provided-types) 。

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

請注意，所提供的類型和成員集合是靜態已知的。 此範例不會利用提供者的能力來提供相依于架構的類型。 下列程式碼概述型別提供者的實作為，詳細資料將在本主題的後續章節中討論。

> [!WARNING]
> 這段程式碼和線上範例之間可能會有差異。

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

若要使用此提供者，請開啟 Visual Studio 的個別實例，建立 F # 腳本，然後使用 #r，從您的腳本加入提供者的參考，如下列程式碼所示：

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

然後，在 `Samples.HelloWorldTypeProvider` 型別提供者產生的命名空間底下尋找類型。

在重新編譯提供者之前，請確定您已關閉所有使用 provider DLL 之 Visual Studio 和 F# 互動的實例。 否則，將會發生組建錯誤，因為輸出 DLL 將會被鎖定。

若要使用 print 語句來偵測這個提供者，請建立一個腳本來公開提供者的問題，然後使用下列程式碼：

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

若要使用 Visual Studio 來偵測此提供者，請以系統管理認證開啟 Visual Studio 的開發人員命令提示字元，然後執行下列命令：

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

另一種方式是開啟 Visual Studio，開啟 [偵錯工具] 功能表，選擇 `Debug/Attach to process…` ，然後附加到 `devenv` 您正在編輯腳本的另一個進程。 藉由使用這個方法，您可以使用完整的 IntelliSense 和其他功能) ，以互動方式將運算式輸入至第二個 (實例，以便更輕鬆地以型別提供者的特定邏輯為目標。

您可以停用 Just My Code 的偵錯工具，以更妥善識別產生的程式碼中的錯誤。 如需如何啟用或停用這項功能的詳細資訊，請參閱 [使用偵錯工具流覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。 此外，您也可以開啟 `Debug` 功能表，然後選擇 `Exceptions` 或選擇 Ctrl + Alt + E 鍵開啟對話方塊，來設定第一個可能發生的例外狀況攔截 `Exceptions` 。 在該對話方塊中， `Common Language Runtime Exceptions` 選取下的 `Thrown` 核取方塊。

### <a name="implementation-of-the-type-provider"></a>實作為型別提供者

本節將逐步引導您完成型別提供者執行的主要區段。 首先，您要定義自訂型別提供者本身的型別：

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

這個型別必須是公用的，而且您必須使用 [TypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) 屬性來標記它，如此一來，當另一個 F # 專案參考包含型別的元件時，編譯器就會辨識型別提供者。 *Config* 參數是選擇性的，如果有的話，則會包含 F # 編譯器所建立之型別提供者實例的內容設定資訊。

接下來，您會執行 [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) 介面。 在此情況下，您會使用 `TypeProviderForNamespaces` API 中的型別 `ProvidedTypes` 做為基底類型。 此協助程式類型可以提供有限的立即提供命名空間集合，其中每個命名空間都會直接包含有限數目的固定、立即提供類型。 在此內容中，提供者 *立即* 會產生型別，即使它們不需要或使用也一樣。

```fsharp
inherit TypeProviderForNamespaces(config)
```

接下來，定義指定所提供類型之命名空間的本機私用值，並尋找型別提供者元件本身。 此元件稍後會用來做為所提供之已清除類型的邏輯父系型別。

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

接著，建立一個函式來提供每個類型的 Type1 .。。Type100. 本主題稍後將更詳細地說明此函式。

```fsharp
let makeOneProvidedType (n:int) = …
```

接下來，產生100提供的類型：

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

接下來，將類型新增為所提供的命名空間：

```fsharp
do this.AddNamespace(namespaceName, types)
```

最後，加入元件屬性，表示您正在建立型別提供者 DLL：

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>提供一種類型和其成員

`makeOneProvidedType`函數會執行提供其中一種類型的實際工作。

```fsharp
let makeOneProvidedType (n:int) =
…
```

此步驟說明此函數的執行。 首先，建立提供的型別 (例如 Type1、when n = 1 或 Type57 （當 n = 57) 時）。

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

您應該注意下列幾點：

- 這會清除提供的類型。  因為您指出基底類型為 `obj` ，所以實例會在已編譯的程式碼中顯示為 [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) 類型的值。

- 當您指定非巢狀型別時，必須指定元件和命名空間。 針對已清除的類型，元件應該是型別提供者元件本身。

接下來，將 XML 檔加入至類型。 這是延遲的檔，也就是當主機編譯器需要時，視需要計算。

```fsharp
t.AddXmlDocDelayed (fun () -> $"""This provided type {"Type" + string n}""")
```

接下來，您要將提供的靜態屬性加入至類型：

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

取得此屬性一律會評估為字串 "Hello！"。 `GetterCode`屬性（property）使用 F # 引號，代表主機編譯器為了取得屬性而產生的程式碼。 如需有關引號的詳細資訊，請參閱 [Code 引號 (F # ) ](../../language-reference/code-quotations.md)。

將 XML 檔集加入至屬性。

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

現在將提供的屬性附加至提供的型別。 您必須將提供的成員附加至一種類型。 否則，成員將永遠無法存取。

```fsharp
t.AddMember staticProp
```

現在，建立未採用任何參數的提供的函式。

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

函式的會傳回 `InvokeCode` F # 引號，代表呼叫函式時，主機編譯器所產生的程式碼。 例如，您可以使用下列的函式：

```fsharp
new Type10()
```

將會使用基礎資料「物件資料」來建立所提供類型的實例。 加上引號的程式碼包含轉換成 [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) ，因為該型別會將這個提供的型別抹除 (當您宣告提供的型別) 時所指定的型別。

將 XML 檔新增至函式，並將提供的函式新增至提供的類型：

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

建立第二個提供的函式，採用一個參數：

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

函 `InvokeCode` 式的會再次傳回 F # 引號，代表主機編譯器針對方法呼叫所產生的程式碼。 例如，您可以使用下列的函式：

```fsharp
new Type10("ten")
```

所提供型別的實例會以基礎資料 "十" 建立。 您可能已經注意到函數會傳回 `InvokeCode` 一個引號。 此函數的輸入是運算式的清單，每個函式參數都有一個。 在此情況下，會在中提供代表單一參數值的運算式 `args.[0]` 。 呼叫函式的程式碼會將傳回值強制轉型為已清除的型別 `obj` 。 當您將第二個提供的函式加入至類型之後，您可以建立提供的實例屬性：

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

取得此屬性會傳回字串的長度，也就是代表物件。 `GetterCode`屬性會傳回 F # 引號，以指定主機編譯器產生的程式碼以取得屬性。 如同 `InvokeCode` ，函數會傳回 `GetterCode` 引號。 主機編譯器會使用引數清單來呼叫這個函數。 在此情況下，引數只會包含代表要呼叫 getter 之實例的單一運算式，您可以使用來存取此實例 `args.[0]` 。 接著會將的實 `GetterCode` 接合至已清除之類型的結果引號 `obj` 中，並使用 cast 來滿足編譯器用來檢查物件是否為字串之類型的機制。 下一個部分會 `makeOneProvidedType` 提供具有一個參數的實例方法。

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

最後，建立包含100嵌套屬性的巢狀型別。 建立此巢狀型別和其屬性會延遲，也就是依需求計算。

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
                  $"This is StaticProperty{i} on NestedType")

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a>已清除提供類型的詳細資料

本節中的範例只會提供已 *清除的提供類型*，在下列情況下特別有用：

- 當您針對只包含資料和方法的資訊空間寫入提供者時。

- 當您撰寫的提供者，正確的執行時間型別語義對資訊空間的實際使用並不重要。

- 當您撰寫的提供者的資訊空間太大且互相連接時，為資訊空間產生真正的 .NET 型別，並不是技術上可行的。

在此範例中，會將每個提供的型別清除為類型 `obj` ，而類型的所有用法在編譯的程式碼中會顯示為類型 `obj` 。 事實上，這些範例中的基礎物件是字串，但類型會顯示為 `System.Object` .net 編譯器代碼中的。 如同抹除型別的所有使用方式，您可以使用明確的裝箱、取消清除和轉換來破壞清除的類型。 在此情況下，使用物件時，可能會產生不正確 cast 例外狀況。 提供者執行時間可以定義自己的私用表示型別，以協助防範 false 標記法。 您無法在 F # 中定義清除的類型。 可能只會清除提供的類型。 您必須瞭解使用您的類型提供者的已清除型別，或提供已清除之類型的提供者，才能瞭解其實際和語義的後果。 清除的類型沒有真正的 .NET 類型。 因此，您無法對型別進行精確的反映，而且如果您使用執行時間轉換和依賴確切執行時間型別語義的其他技術，您可能會破壞清除的型別。 清除的型別 Subversion 通常會在執行時間產生類型轉換例外狀況。

### <a name="choosing-representations-for-erased-provided-types"></a>選擇已清除提供類型的標記法

針對已清除之提供類型的某些用途，不需要標記法。 例如，已清除的提供類型可能只包含靜態屬性和成員，而不包含任何函式，而且沒有方法或屬性會傳回類型的實例。 如果您可以觸達已清除之提供類型的實例，您必須考慮下列問題：

**所提供類型的抹除為何？**

- 抹除所提供的類型是類型在已編譯的 .NET 程式碼中的顯示方式。

- 在類型的繼承鏈中，抹除所提供的已清除類別類型一律是第一個未清除的基底類型。

- 所提供已清除介面類別型的抹除一律為 `System.Object` 。

**所提供類型的標記法為何？**

- 已清除之提供類型的可能物件集合稱為其標記法。 在本檔的範例中，所有已清除的所提供類型的表示 `Type1..Type100` 一律為字串物件。

提供之類型的所有表示都必須與所提供類型的抹除相容。  (否則，F # 編譯器會在使用型別提供者時提供錯誤，否則會產生不正確無法驗證 .NET 程式碼。 如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。

您可以使用下列其中一種方法來選擇所提供物件的標記法，兩者都很常見：

- 如果您只是在現有的 .NET 型別上提供強型別包裝函式，則您的型別通常很適合用來清除該型別、使用該型別的實例做為標記法，或兩者都使用。 當使用強型別版本時，該類型上的大部分現有方法仍有意義時，這個方法就很適合。

- 如果您想要建立與任何現有 .NET API 截然不同的 API，請建立執行時間類型，以做為所提供類型的抹除和標記法。

本檔中的範例會使用字串作為所提供物件的表示。 通常可能適合使用其他物件作為標記法。 例如，您可以使用字典作為屬性包：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

或者，您可以在型別提供者中定義要在執行時間用來形成標記法的型別，以及一或多個執行時間作業：

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

接著，提供的成員可以建立此物件類型的實例：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

在這種情況下，您可以在建立時將此類型指定為，以 (選擇性地) 使用此類型做為類型抹除 `baseType` `ProvidedTypeDefinition` ：

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>重要課程

上一節說明如何建立簡單的清除型別提供者，以提供一系列的類型、屬性和方法。 本節也說明了抹除型別的概念，包括從型別提供者提供已清除類型的一些優點和缺點，以及已清除之類型的標記法。

## <a name="a-type-provider-that-uses-static-parameters"></a>使用靜態參數的型別提供者

即使提供者不需要存取任何本機或遠端資料，透過靜態資料將型別提供者參數化的功能也可提供許多有趣的案例。 在本節中，您將瞭解一些將這類提供者結合在一起的基本技巧。

### <a name="type-checked-regex-provider"></a>輸入已核取的 Regex 提供者

假設您想要在 <xref:System.Text.RegularExpressions.Regex> 提供下列編譯時期保證的介面中，針對包裝 .net 程式庫的正則運算式，執行型別提供者：

- 確認正則運算式是否有效。

- 根據正則運算式中的任何組名，提供相符專案的命名屬性。

本節說明如何使用型別提供者來建立 `RegexTyped` 正則運算式模式所參數化的型別，以提供這些優點。 如果提供的模式無效，則編譯器會回報錯誤，而且型別提供者可以從模式中解壓縮群組，以便您可以使用相符的命名屬性來存取它們。 當您設計型別提供者時，您應該考慮其公開的 API 對終端使用者的外觀，以及這種設計如何轉譯為 .NET 程式碼。 下列範例顯示如何使用這類 API 來取得區碼的元件：

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

下列範例顯示型別提供者如何轉譯這些呼叫：

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

請注意下列幾點：

- 標準 Regex 類型代表參數化 `RegexTyped` 型別。

- 此函式會 `RegexTyped` 導致呼叫 Regex 的函式，並傳入模式的靜態型別引數。

- 方法的結果 `Match` 會以標準 <xref:System.Text.RegularExpressions.Match> 類型表示。

- 每個命名群組都會產生提供的屬性，而且存取屬性會導致在相符的集合上使用索引子 `Groups` 。

下列程式碼是執行這類提供者的邏輯核心，此範例會省略將所有成員新增至提供的類型。 如需每個已加入成員的詳細資訊，請參閱本主題稍後的適當章節。 如需完整的程式碼，請從 CodePlex 網站上的 [F # 3.0 範例套件](https://archive.codeplex.com/?p=fsharp3sample) 下載範例。

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

- 型別提供者採用兩個靜態參數： `pattern` ，這是必要的， `options` 而且是選擇性的 (因為) 會提供預設值。

- 提供靜態引數之後，您可以建立正則運算式的實例。 如果 Regex 的格式不正確，這個實例將會擲回例外狀況，並將此錯誤回報給使用者。

- 在 `DefineStaticParameters` 回呼中，您要定義在提供引數之後將傳回的型別。

- 這段程式碼會將設定 `HideObjectMethods` 為 true，讓 IntelliSense 體驗維持簡化。 這個屬性會讓 `Equals` 、 `GetHashCode` 、 `Finalize` 和 `GetType` 成員從提供的物件的 IntelliSense 清單中隱藏。

- 您可以使用 `obj` 做為方法的基底類型，但您會使用 `Regex` 物件做為此類型的運行時程表示法，如以下範例所示。

- `Regex` <xref:System.ArgumentException> 當正則運算式無效時，對此函數的呼叫會擲回。 編譯器會攔截這個例外狀況，並在編譯時期或 Visual Studio 編輯器中，將錯誤訊息報告給使用者。 這個例外狀況可讓您驗證正則運算式，而不需要執行應用程式。

以上定義的類型並不實用，因為它不包含任何有意義的方法或屬性。 首先，新增靜態 `IsMatch` 方法：

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

先前的程式碼會定義方法 `IsMatch` ，此方法會接受字串做為輸入並傳回 `bool` 。 唯一棘手的部分是在 `args` 定義內使用引數 `InvokeCode` 。 在此範例中， `args` 是代表這個方法之引數的引號清單。 如果方法是實例方法，則第一個引數代表 `this` 引數。 不過，針對靜態方法，引數全都只是方法的明確引數。 請注意，引號值的類型應該符合指定的傳回類型 (在此案例中為 `bool`) 。 另請注意，此程式碼 `AddXmlDoc` 會使用方法來確保提供的方法也有實用的檔，您可以透過 IntelliSense 提供這些檔。

接下來，加入實例 Match 方法。 不過，這個方法應該會傳回所提供類型的值，以便以強型別 `Match` 方式來存取群組。 因此，您會先宣告 `Match` 類型。 因為這個型別取決於提供為靜態引數的模式，所以這個型別必須嵌套在參數化型別定義中：

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

然後，您可以將一個屬性新增至每個群組的比對類型。 在執行時間，會以值表示比對 <xref:System.Text.RegularExpressions.Match> ，因此定義屬性的引號必須使用 <xref:System.Text.RegularExpressions.Match.Groups> 索引屬性來取得相關的群組。

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc($"""Gets the ""{group}"" group from this match""")
    matchTy.AddMember prop
```

同樣地，請注意，您要將 XML 檔新增至提供的屬性。 另請注意，如果有提供函式，就可以讀取屬性 `GetterCode` ，而且如果有提供函式，就可以撰寫屬性 `SetterCode` ，因此產生的屬性是唯讀的。

現在您可以建立傳回此類型值的實例方法 `Match` ：

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

因為您要建立實例方法，所以 `args.[0]` 代表 `RegexTyped` 呼叫方法的實例，而 `args.[1]` 是輸入引數。

最後，提供一個函式，以便能夠建立所提供型別的實例。

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

此函式只會清除建立標準的 .NET Regex 實例，這會再次封裝至物件，因為 `obj` 是所提供類型的抹除。 有了這項變更，本主題稍早指定的範例 API 使用方式就會如預期般運作。 以下是完整的程式碼和最後的程式碼：

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

### <a name="key-lessons"></a>重要課程

本節說明如何建立可在其靜態參數上運作的型別提供者。 提供者會檢查靜態參數，並根據其值提供作業。

## <a name="a-type-provider-that-is-backed-by-local-data"></a>由本機資料支援的型別提供者

通常，您可能會想要型別提供者根據靜態參數，以及本機或遠端系統的資訊來呈現 Api。 本節將討論以本機資料（例如本機資料檔案）為基礎的型別提供者。

### <a name="simple-csv-file-provider"></a>Simple CSV File Provider

簡單的範例，請考慮使用以逗號分隔值 (CSV) 格式來存取科學資料的型別提供者。 本節假設 CSV 檔案包含標頭資料列，後面接著浮點數資料，如下表所示：

|距離 (計量) |時間 (秒) |
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

本節說明如何提供型別，讓您用來取得具有 `Distance` 型別屬性 `float<meter>` 和型別屬性的資料列 `Time` `float<second>` 。 為了簡單起見，會進行下列假設：

- 標頭名稱不是單位，或格式為 "Name (unit) " 且不包含逗號。

- 單位是所有系統國際 (SI) 單位，與 [fsharp.core. UnitNames 模組 (F # ) ](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) 模組定義。

- 單位都是簡單的 (例如，計量) ，而不是複合 (例如，計量/秒) 。

- 所有資料行都包含浮點數據。

更完整的提供者會放寬這些限制。

同樣地，第一步是考慮 API 的外觀。 假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn $"{float time}"
```

在此情況下，編譯器應該將這些呼叫轉換成如下列範例所示的內容：

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn $"%f{float time}"
```

最佳轉譯需要型別提供者 `CsvFile` 在型別提供者的元件中定義實數型別。 型別提供者通常依賴一些協助程式類型和方法來包裝重要的邏輯。 因為量值會在執行時間清除，所以您可以使用做為資料 `float[]` 列的清除型別。 編譯器會將不同的資料行視為具有不同的量數值型別。 例如，在我們的範例中，第一個資料行的類型為 `float<meter>` ，而第二個數據行有 `float<second>` 。 不過，已清除的表示可以維持相當簡單。

下列程式碼顯示執行的核心。

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

請注意下列有關執行的重點：

- 多載的函式允許讀取具有相同架構的原始檔案或。 當您針對本機或遠端資料源撰寫型別提供者時，此模式很常見，而此模式允許使用本機檔案做為遠端資料的範本。

- 您可以使用傳遞至型別提供者函式的 [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) 值來解析相對檔案名。

- 您可以使用 `AddDefinitionLocation` 方法來定義所提供屬性的位置。 因此，如果您在 `Go To Definition` 提供的屬性上使用，則會在 Visual Studio 中開啟 CSV 檔案。

- 您可以使用 `ProvidedMeasureBuilder` 類型來查閱 SI 單位，並產生相關的 `float<_>` 類型。

### <a name="key-lessons"></a>重要課程

本節說明如何使用包含在資料來源本身的簡單架構來建立本機資料來源的類型提供者。

## <a name="going-further"></a>更進一步

下列各節包含進一步研究的建議。

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>查看已清除類型的已編譯器代碼

為了讓您瞭解如何使用型別提供者對應至發出的程式碼，請使用本主題稍早所使用的來查看下列函式 `HelloWorldTypeProvider` 。

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

以下是使用 ildasm.exe 所反向組譯的產生程式碼的影像：

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

如範例所示，所有提及的型別 `Type1` 和 `InstanceProperty` 屬性都已清除，只留下相關執行時間類型的作業。

### <a name="design-and-naming-conventions-for-type-providers"></a>型別提供者的設計和命名慣例

撰寫型別提供者時，請觀察下列慣例。

**連接通訊協定的提供者** 一般而言，資料和服務連接通訊協定（例如 OData 或 SQL 連接）的最大提供者 Dll 名稱應該以 `TypeProvider` 或結尾 `TypeProviders` 。 例如，使用類似下列字串的 DLL 名稱：

`Fabrikam.Management.BasicTypeProviders.dll`

確定您提供的類型是對應命名空間的成員，並指出您所執行的連接通訊協定：

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**一般程式碼撰寫的公用程式提供者**。  針對正則運算式之類的公用程式類型提供者，型別提供者可能是基底程式庫的一部分，如下列範例所示：

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

在此情況下，所提供的類型會根據一般的 .NET 設計慣例出現在適當的時間點：

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**單一資料來源**。 某些型別提供者會連接到單一專用資料來源，並只提供資料。 在此情況下，您應該卸載 `TypeProvider` 尾碼並使用一般的 .net 命名慣例：

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

如需詳細資訊，請參閱 `GetConnection` 本主題稍後所述的設計慣例。

### <a name="design-patterns-for-type-providers"></a>型別提供者的設計模式

下列各節描述撰寫型別提供者時，您可以使用的設計模式。

#### <a name="the-getconnection-design-pattern"></a>GetConnection 設計模式

大部分的型別提供者都應該撰寫成使用 `GetConnection` FSharp.Data.TypeProviders.dll 中的型別提供者所使用的模式，如下列範例所示：

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>遠端資料和服務支援的型別提供者

在您建立由遠端資料和服務支援的型別提供者之前，您必須考慮連線程式設計中固有的一系列問題。 這些問題包括下列考慮：

- 架構對應

- 架構變更存在時的活動和失效

- 架構快取

- 資料存取作業的非同步執行

- 支援查詢，包括 LINQ 查詢

- 認證和驗證

本主題不會進一步探索這些問題。

### <a name="additional-authoring-techniques"></a>其他撰寫技巧

當您撰寫自己的型別提供者時，您可能會想要使用下列其他技巧。

### <a name="creating-types-and-members-on-demand"></a>視需要建立類型和成員

ProvidedType API 有延遲的 AddMember 版本。

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

這些版本是用來建立隨選的類型空間。

### <a name="providing-array-types-and-generic-type-instantiations"></a>提供陣列類型和泛型型別具現化

您會將提供的成員 (其簽章包含陣列類型、byref 型別和泛型型別的具現化) 使用 normal `MakeArrayType` 、 `MakePointerType` 和的 `MakeGenericType` 任何實例 <xref:System.Type> （包括） `ProvidedTypeDefinitions` 。

> [!NOTE]
> 在某些情況下，您可能必須在中使用 helper `ProvidedTypeBuilder.MakeGenericType` 。  如需詳細資訊，請參閱 [類型提供者 SDK 檔](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) 。

### <a name="providing-unit-of-measure-annotations"></a>提供量值注釋的單位

ProvidedTypes API 提供提供量值附注的協助程式。 例如，若要提供型別 `float<kg>` ，請使用下列程式碼：

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  若要提供類型 `Nullable<decimal<kg/m^2>>` ，請使用下列程式碼：

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>存取 Project-Local 或 Script-Local 資源

型別提供者的每個實例都可以在 `TypeProviderConfig` 結構中指定一個值。 此值包含提供者的「解析資料夾」 (也就是編譯的專案資料夾或包含腳本) 的目錄、參考元件的清單，以及其他資訊。

### <a name="invalidation"></a>失效

提供者可以引發失效信號，通知 F # 語言服務架構假設可能已變更。 當發生失效時，如果 Visual Studio 中裝載提供者，則會重做 typecheck。 當提供者裝載于 F# 互動或由 F # 編譯器 ( # A0) 時，將會忽略此信號。

### <a name="caching-schema-information"></a>快取架構資訊

提供者通常必須快取架構資訊的存取權。 快取的資料應該使用以靜態參數形式提供的檔案名或使用者資料來儲存。 架構快取的範例是 `LocalSchemaFile` 元件中型別提供者的參數 `FSharp.Data.TypeProviders` 。 在這些提供者的執行中，這個靜態參數會指示型別提供者使用指定的本機檔案中的架構資訊，而不是透過網路來存取資料來源。 若要使用快取的架構資訊，您也必須將靜態參數設定 `ForceUpdate` 為 `false` 。 您可以使用類似的技術來啟用線上和離線資料存取。

### <a name="backing-assembly"></a>支援元件

當您編譯或檔案時 `.dll` `.exe` ，產生之類型的支援 .dll 檔會以靜態方式連結到產生的元件中。 建立此連結的方法是將中繼語言 (IL) 型別定義，以及從支援元件到最終元件的任何 managed 資源複製。 當您使用 F# 互動時，不會複製支援 .dll 檔案，而會改為直接載入 F# 互動的進程。

### <a name="exceptions-and-diagnostics-from-type-providers"></a>來自型別提供者的例外狀況和診斷

來自所提供類型之所有成員的所有使用，可能會擲回例外狀況。 在所有情況下，如果型別提供者擲回例外狀況，則主機編譯器會將錯誤屬性指定給特定的類型提供者。

- 型別提供者例外狀況絕不會導致編譯器內部錯誤。

- 類型提供者無法報告警告。

- 當型別提供者裝載于 F # 編譯器、F # 開發環境或 F# 互動時，會攔截到該提供者的所有例外狀況。 Message 屬性一律是錯誤文字，且不會顯示任何堆疊追蹤。 如果您即將擲回例外狀況，您可以擲回下列範例： `System.NotSupportedException` 、 `System.IO.IOException` 、 `System.Exception` 。

#### <a name="providing-generated-types"></a>提供產生的類型

到目前為止，本檔已說明如何提供清除的類型。 您也可以使用 F # 中的型別提供者機制來提供產生的型別，這些型別會以真實的 .NET 型別定義新增至使用者的程式。 您必須使用類型定義來參考所產生的所提供類型。

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

屬於 F # 3.0 版本的 ProvidedTypes-0.2 協助程式程式碼，只有有限的支援提供產生的類型。 下列語句對於產生的型別定義而言必須是 true：

- `isErased` 必須設為 `false`。

- 產生的類型必須加入至新建立的 `ProvidedAssembly()` ，這表示產生的程式碼片段的容器。

- 提供者的元件必須具有在磁片上具有相符 .dll 檔案的實際支援 .NET .dll 檔案。

## <a name="rules-and-limitations"></a>規則和限制

當您撰寫型別提供者時，請記住下列規則和限制。

### <a name="provided-types-must-be-reachable"></a>提供的類型必須可以連線

所有提供的類型都應該可從非巢狀型別連接。 呼叫函式或的呼叫時，會提供非巢狀型別 `TypeProviderForNamespaces` `AddNamespace` 。 例如，如果提供者提供型 `StaticClass.P : T` 別，您必須確定 T 是非嵌套型別或在其中嵌套。

例如，某些提供者有一個靜態類別，例如 `DataTypes` 包含這些 `T1, T2, T3, ...` 類型。 否則，此錯誤表示找到元件 A 中的類型 T 的參考，但在該元件中找不到該類型。 如果出現此錯誤，請確認您的所有子類型都可以從提供者類型中取得。 注意：這些型別 `T1, T2, T3...` 稱為「 *動態* 」類型。 請記得將它們放在可存取的命名空間或父系型別中。

### <a name="limitations-of-the-type-provider-mechanism"></a>型別提供者機制的限制

F # 中的型別提供者機制有下列限制：

- F # 中型別提供者的基礎結構不支援提供的泛型型別或提供的泛型方法。

- 機制不支援具有靜態參數的巢狀型別。

## <a name="development-tips"></a>開發秘訣

在開發過程中，您可能會發現下列秘訣很有説明：

### <a name="run-two-instances-of-visual-studio"></a>執行 Visual Studio 的兩個實例

您可以在一個實例中開發型別提供者，並在另一個實例中測試該提供者，因為測試 IDE 會對 .dll 檔案進行鎖定，防止重建型別提供者。 因此，您必須在第一個實例內建提供者時，關閉 Visual Studio 的第二個實例，然後您必須在建立提供者之後重新開啟第二個實例。

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>使用 fsc.exe 調用的偵錯工具型別提供者

您可以使用下列工具來叫用型別提供者：

- fsc.exe (F # 命令列編譯器) 

- fsi.exe (F# 互動編譯器) 

- devenv.exe (Visual Studio) 

您通常可以在測試腳本檔案上使用 fsc.exe，以最輕鬆的方式來偵測型別提供者 (例如 .fsx) 。 您可以從命令提示字元啟動偵錯工具。

```console
devenv /debugexe fsc.exe script.fsx
```

  您可以使用列印到 stdout 記錄。

## <a name="see-also"></a>另請參閱

- [型別提供者](index.md)
- [型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
