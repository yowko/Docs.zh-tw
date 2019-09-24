---
title: 教學課程：建立型別提供者
description: 藉由檢查數個簡單F#的類型提供F#者來說明基本概念，以瞭解如何在3.0 中建立您自己的類型提供者。
ms.date: 02/02/2019
ms.openlocfilehash: 8d1a1fedf03437ccbacd40616cc7dc3e1da435b2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214265"
---
# <a name="tutorial-create-a-type-provider"></a>教學課程：建立型別提供者

中F#的型別提供者機制，是其對資訊豐富程式設計支援的重要部分。 本教學課程說明如何建立您自己的型別提供者，方法是逐步執行數個簡單型別提供者的開發，以說明基本概念。 如需中F#型別提供者機制的詳細資訊，請參閱[型別提供者](index.md)。

F#生態系統包含常用網際網路和企業資料服務的一系列型別提供者。 例如：

- [Fsharp.core：資料](https://fsharp.github.io/FSharp.Data/)報括 JSON、XML、CSV 和 HTML 檔案格式的類型提供者。

- [SQLProvider](https://fsprojects.github.io/SQLProvider/)透過物件對應和針對這些資料來源的 LINQ 查詢， F#提供 SQL 資料庫的強型別存取。

- [SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)具有一組類型提供者，適用于編譯時期已核取的 t-sql F#。

- [Fsharp.data.typeproviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是一組較舊的類型提供者，僅供用來存取 SQL、Entity Framework、ODATA 和 WSDL 資料服務的 .NET Framework 程式設計使用。

必要時，您可以建立自訂類型提供者，或者您可以參考其他人建立的類型提供者。 例如，您的組織可能會有一個資料服務，可提供大量且不斷成長的已命名資料集數目，而每個集合都有自己的穩定資料架構。 您可以建立一個型別提供者來讀取架構，並以強型別方式將目前的資料集呈現給程式設計人員。

## <a name="before-you-start"></a>在開始之前

型別提供者機制主要是設計用來在F#程式設計經驗中插入穩定的資料和服務資訊空間。

這項機制並非設計用來插入在程式執行期間架構變更的資訊空間（以與程式邏輯相關的方式）。 此外，這種機制並不是針對語言中繼程式設計，即使該網域包含一些有效的用法。 您應該只在必要時使用此機制，而在其中開發類型提供者會產生非常高的值。

您應該避免撰寫無法使用架構的類型提供者。 同樣地，您應該避免撰寫一個一般（或甚至是現有） .NET 程式庫所能滿足的類型提供者。

開始之前，您可能會提出下列問題：

- 您有資訊來源的架構嗎？ 若是如此，與 .NET 型別系統的F#對應為何？

- 您可以使用現有的（動態型別） API 作為您的實作為起點嗎？

- 您和您的組織是否有足夠的使用型別提供者，讓他們有價值？ 一般的 .NET 程式庫是否符合您的需求？

- 您的架構變更了多少？

- 在編碼期間是否會變更？

- 它會在編碼會話之間變更嗎？

- 它會在程式執行期間變更嗎？

型別提供者最適用于架構在執行時間穩定的情況，以及在已編譯器代碼的存留期間。

## <a name="a-simple-type-provider"></a>簡單型別提供者

這個範例是 HelloWorldTypeProvider，類似于`examples` [ F#類型提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)目錄中的範例。 提供者提供的「類型空間」包含100已清除的類型，如下列程式碼所示， F#會使用簽章語法，並省略除了`Type1`以外的所有詳細資料。 如需已清除之類型的詳細資訊，請參閱本主題稍後的已[清除之提供類型的詳細資料](#details-about-erased-provided-types)。

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

請注意，所提供的類型和成員集合是靜態已知的。 這個範例不會利用提供者提供相依于架構之類型的能力。 下列程式碼概述型別提供者的執行，而詳細資料則會在本主題的後續章節中討論。

> [!WARNING]
> 此程式碼與線上範例之間可能有差異。

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

若要使用此提供者，請開啟 Visual Studio 的個別實例、 F#建立腳本，然後使用 #r，從您的腳本中新增提供者的參考，如下列程式碼所示：

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

然後尋找類型提供者所`Samples.HelloWorldTypeProvider`產生之命名空間下的類型。

重新編譯提供者之前，請確定您已關閉所有使用提供者 DLL 的F# Visual Studio 和 Interactive 實例。 否則，會發生組建錯誤，因為輸出 DLL 會被鎖定。

若要使用 print 語句來進行這項提供者的偵錯工具，請建立會向提供者公開問題的腳本，然後使用下列程式碼：

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

若要使用 Visual Studio 來調試此提供者，請使用系統管理認證開啟 Visual Studio 的開發人員命令提示字元，然後執行下列命令：

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

或者，開啟 Visual Studio，開啟 [偵錯工具] 功能表，選擇`Debug/Attach to process…`，然後附加至您`devenv`正在編輯腳本的另一個進程。 藉由使用這個方法，您可以更輕鬆地以類型提供者中的特定邏輯為目標，方法是以互動方式將運算式輸入至第二個實例（具有完整的 IntelliSense 和其他功能）。

您可以停用 Just My Code 的偵錯工具，以更清楚地識別產生的程式碼錯誤。 如需如何啟用或停用這項功能的相關資訊，請參閱[使用偵錯工具流覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。 此外，您也可以開啟`Debug`功能表，然後選擇`Exceptions` [Ctrl + Alt + `Exceptions` E 鍵] 來開啟對話方塊，以設定第一個可能發生的例外狀況捕捉。 在該對話方塊中，選取`Common Language Runtime Exceptions`[] 下`Thrown`的核取方塊。

### <a name="implementation-of-the-type-provider"></a>實作為型別提供者

本節將逐步引導您完成類型提供者實作為的主要區段。 首先，您要定義自訂類型提供者本身的類型：

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

此類型必須是公用的，而且您必須使用[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性加以標記，如此一來，當個別F#的專案參考包含該類型的元件時，編譯器才會辨識該類型提供者。 *Config*參數是選擇性的，如果存在，則會包含F#編譯器所建立之型別提供者實例的內容相關設定資訊。

接下來，您會執行[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。 在此情況下，您會`TypeProviderForNamespaces`使用`ProvidedTypes` API 中的型別做為基底型別。 此協助程式類型可以提供立即提供之命名空間的有限集合，其中每一個都直接包含有限數目的固定、立即提供的類型。 在此內容中，提供者*立即*會產生類型，即使不需要或未使用它們也一樣。

```fsharp
inherit TypeProviderForNamespaces(config)
```

接下來，定義本機私用值，以指定所提供類型的命名空間，並尋找類型提供者元件本身。 此元件稍後會用來做為所提供之已清除類型的邏輯父類型。

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

接下來，建立函式來提供每個類型 Type1 。Type100. 本主題稍後將會詳細說明此函式。

```fsharp
let makeOneProvidedType (n:int) = …
```

接下來，產生100提供的類型：

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

接下來，新增類型做為提供的命名空間：

```fsharp
do this.AddNamespace(namespaceName, types)
```

最後，新增元件屬性，以指出您正在建立類型提供者 DLL：

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>提供一種類型和其成員

`makeOneProvidedType`函式會執行提供其中一種類型的實際工作。

```fsharp
let makeOneProvidedType (n:int) =
…
```

此步驟說明此函式的執行方式。 首先，建立提供的類型（例如，Type1，當 n = 1，或 Type57，當 n = 57 時）。

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

您應該要注意下列幾點：

- 已清除此提供的類型。  因為您表示基底類型為`obj`，所以實例會在編譯的程式碼中顯示為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)類型的值。

- 當您指定非巢狀型別時，您必須指定元件和命名空間。 若為已清除的類型，元件應該是類型提供者元件本身。

接下來，將 XML 檔加入至類型。 這是延遲的檔，也就是，如果主機編譯器需要，則視需要計算。

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

接下來，您要將提供的靜態屬性新增至類型：

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

取得此屬性一律會評估為字串 "Hello！"。 屬性`GetterCode`的會使用F#引號，這代表主機編譯器為了取得屬性而產生的程式碼。 如需報價的詳細資訊，請參閱程式[代碼報價（F#）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。

將 XML 檔加入至屬性。

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

現在，將提供的屬性附加至提供的類型。 您必須將提供的成員附加至一種類型。 否則，將永遠無法存取該成員。

```fsharp
t.AddMember staticProp
```

現在，請建立不採用任何參數的提供的函式。

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

此函式F#的會傳回引號，表示呼叫此函式時，主機編譯器所產生的程式碼。 `InvokeCode` 例如，您可以使用下列的函數：

```fsharp
new Type10()
```

所提供類型的實例將會以基礎資料「物件資料」建立。 加上引號的程式碼包含對[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)的轉換，因為該類型是此提供類型的抹除（如同您在宣告提供的類型時所指定）。

將 XML 檔加入至此函式，並將提供的函式加入至提供的類型：

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

建立第二個提供的函式，以接受一個參數：

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

此函式F#的會再次傳回引號，代表主機編譯器為呼叫方法所產生的程式碼。 `InvokeCode` 例如，您可以使用下列的函數：

```fsharp
new Type10("ten")
```

所提供類型的實例是使用基礎資料 "十" 所建立。 您可能已經注意到`InvokeCode`函式會傳回引號。 此函式的輸入是運算式的清單，每個函式參數一個。 在此情況下，可以在中`args.[0]`使用代表單一參數值的運算式。 呼叫此函式的程式碼會將傳回值強制轉型為已`obj`清除的類型。 將第二個提供的函式加入至類型之後，您會建立提供的實例屬性：

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

取得此屬性會傳回字串的長度，也就是標記法物件。 屬性會傳回F#報價，指定主機編譯器所產生的程式碼，以取得屬性。 `GetterCode` `InvokeCode`如同`GetterCode` ，函式會傳回引號。 主機編譯器會使用引數清單來呼叫這個函式。 在此情況下，引數只會包含單一運算式，代表要在其上呼叫 getter 的實例，您可以使用`args.[0]`來存取它。 然後，將接合至已清除類型`obj`的結果引號，並使用 cast 來滿足編譯器用來檢查物件是否為字串之類型的機制。 `GetterCode` 的下一個部分`makeOneProvidedType`會提供具有一個參數的實例方法。

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

最後，建立包含100嵌套屬性的巢狀型別。 建立此巢狀型別及其屬性會延遲，也就是視需要計算。

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

### <a name="details-about-erased-provided-types"></a>已清除之提供類型的詳細資料

本節中的範例只提供已*清除的提供類型*，在下列情況下特別有用：

- 當您針對只包含資料和方法的資訊空間撰寫提供者時。

- 當您撰寫提供者，其中正確的執行時間型別語義對資訊空間的實際使用並不重要。

- 當您撰寫的資訊空間提供者很大且相互關聯時，在技術上並不能為資訊空間產生真正的 .NET 類型。

在此範例中，會將每個提供的`obj`型別清除成型別，而該型別的`obj`所有用法都會在已編譯的程式碼中顯示成型別。 事實上，這些範例中的基礎物件都是字串，但型別在 .net 編譯器`System.Object`代碼中會顯示為。 如同抹除類型的所有用法，您可以使用明確的裝箱、取消裝箱，以及轉換成破壞清除的類型。 在此情況下，當使用物件時，可能會導致不正確轉換例外狀況。 提供者執行時間可以定義自己的私用標記法類型，以協助防止 false 標記法。 您無法在本身定義已F#清除的類型。 只有提供的類型可以清除。 您必須瞭解使用類型提供者的已清除類型，或提供已清除類型之提供者的後果，包括實際和語義。 已清除的類型沒有真正的 .NET 類型。 因此，您無法對型別執行精確的反映，而且如果您使用執行時間轉換和其他依賴實際執行時間型別語義的技術，則可能會破壞已清除的類型。 已清除類型的 Subversion 經常會在執行時間產生類型轉換例外狀況。

### <a name="choosing-representations-for-erased-provided-types"></a>選擇已清除之提供類型的標記法

對於已清除之提供類型的某些用法，不需要任何標記法。 例如，已清除的提供類型可能只包含靜態屬性和成員，而且沒有任何方法或屬性會傳回類型的實例。 如果您可以到達已清除之提供類型的實例，則必須考慮下列問題：

**所提供類型的抹除是什麼？**

- 所提供類型的抹除是該類型在已編譯的 .NET 程式碼中的顯示方式。

- 在類型的繼承鏈中，所提供之已清除類別類型的抹除一律是第一個未清除的基底類型。

- 所提供之已清除介面類別型的抹除一律`System.Object`為。

**提供類型的標記法為何？**

- 已清除之提供類型的一組可能物件稱為其標記法。 在本檔的範例中，所有已清除之提供類型`Type1.Type100`的表示一律為 string 物件。

所提供類型的所有表示都必須與所提供類型的抹除相容。 （否則， F#編譯器會提供使用型別提供者的錯誤，否則會產生不正確無法驗證的 .net 程式碼。 如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。

您可以使用下列其中一種方法來選擇所提供物件的標記法，這兩者都很常見：

- 如果您只是在現有的 .NET 類型上提供強型別包裝函式，則您的型別會清除為該型別，請使用該型別的實例做為標記法，或兩者皆是。 當使用強型別版本時，該型別上大部分的現有方法仍有意義，這是適當的方法。

- 如果您想要建立與任何現有 .NET API 截然不同的 API，建立執行時間類型將會是所提供類型的抹除和標記法，是合理的做法。

本檔中的範例使用字串作為所提供物件的標記法。 通常，針對標記法使用其他物件可能是適當的方式。 例如，您可以使用字典做為屬性包：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

或者，您也可以在型別提供者中定義一個類型，以便在執行時間用來形成標記法，以及一或多個執行時間作業：

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

提供的成員可以接著建立此物件類型的實例：

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

在這種情況下，您可以（選擇性地）使用此類型做為型別抹除，方法`baseType`是在`ProvidedTypeDefinition`建立時將此型別指定為：

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>重要課程

上一節說明如何建立簡單的抹除類型提供者，以提供類型、屬性和方法的範圍。 本節也說明了抹除類型的概念，包括從類型提供者提供已清除類型的一些優缺點，以及已清除類型的標記法。

## <a name="a-type-provider-that-uses-static-parameters"></a>使用靜態參數的類型提供者

透過靜態資料參數化型別提供者的能力，可實現許多有趣的案例，即使提供者不需要存取任何本機或遠端資料也一樣。 在本節中，您將瞭解將這類提供者放在一起的一些基本技巧。

### <a name="type-checked-regex-provider"></a>類型已核取的 Regex 提供者

假設您想要在提供下列編譯時間保證的介面中，針對包裝<xref:System.Text.RegularExpressions.Regex> .net 程式庫的正則運算式，執行型別提供者：

- 正在驗證正則運算式是否有效。

- 根據正則運算式中的任何組名，提供相符專案的命名屬性。

本節說明如何使用型別提供者建立`RegexTyped`正則運算式模式所參數化的型別，以提供這些優點。 如果提供的模式無效，則編譯器會報告錯誤，而且型別提供者可以從模式中解壓縮群組，讓您可以使用相符專案上的命名屬性來存取它們。 當您設計型別提供者時，應該考慮其公開的 API 應如何向使用者顯示，以及此設計將如何轉譯為 .NET 程式碼。 下列範例顯示如何使用這類 API 來取得區碼的元件：

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

下列範例顯示型別提供者轉譯這些呼叫的方式：

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

請注意下列幾點:

- 標準 Regex 類型代表參數化`RegexTyped`類型。

- 此`RegexTyped`函式會產生 Regex 函式的呼叫，並傳入模式的靜態類型引數。

- `Match`方法的結果是以標準<xref:System.Text.RegularExpressions.Match>型別表示。

- 每個命名群組都會產生提供的屬性，而存取屬性會導致在相符的`Groups`集合上使用索引子。

下列程式碼是執行這類提供者之邏輯的核心，而此範例會省略將所有成員加入至提供之類型的動作。 如需每個新增成員的詳細資訊，請參閱本主題稍後的適當章節。 如需完整的程式碼，請從 CodePlex 網站上的[ F# 3.0 範例套件](https://archive.codeplex.com/?p=fsharp3sample)下載範例。

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

請注意下列幾點:

- 型別提供者接受兩個靜態參數`pattern`：，這是必要的， `options`而是選擇性的（因為提供了預設值）。

- 提供靜態引數之後，您可以建立正則運算式的實例。 如果 Regex 的格式不正確，這個實例就會擲回例外狀況，而且會向使用者回報此錯誤。

- `DefineStaticParameters`在回呼內，您會定義要在提供引數之後傳回的類型。

- 這段程式`HideObjectMethods`代碼會將設定為 true，讓 IntelliSense 體驗保持順暢。 這個屬性會使`Equals`、 `GetHashCode`、 `Finalize`和`GetType`成員從提供之物件的 IntelliSense 清單中隱藏。

- 您會`obj`使用做為方法的基底類型，但您會`Regex`使用物件做為此類型的運行時程表示法，如下一個範例所示。

- 當正則運算式`Regex`無效時，對此函式的呼叫會擲回。 <xref:System.ArgumentException> 編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者報告錯誤訊息。 這個例外狀況可讓您驗證正則運算式，而不需要執行應用程式。

上述定義的類型並不實用，因為它不包含任何有意義的方法或屬性。 首先，新增靜態`IsMatch`方法：

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

先前的程式碼會定義`IsMatch`方法，以接受字串做為輸入，並`bool`傳回。 唯一棘手的部分是在`args` `InvokeCode`定義內使用引數。 在此範例中`args` ，是代表這個方法之引數的引號清單。 如果方法是實例方法，則第一個引數代表`this`引數。 不過，對於靜態方法，引數只是方法的明確引數而已。 請注意，引號值的類型應符合指定的傳回類型（在此案例`bool`中為）。 另請注意，此程式碼`AddXmlDoc`會使用方法來確定提供的方法也有實用的檔，您可以透過 IntelliSense 提供此功能。

接下來，新增實例 Match 方法。 不過，這個方法應該會傳回所提供`Match`類型的值，以便以強型別方式來存取群組。 因此，您必須先`Match`宣告型別。 因為此型別取決於當做靜態引數提供的模式，所以這個型別必須嵌套在參數化型別定義內：

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

接著，您可以將一個屬性新增至每個群組的比對類型。 在執行時間，比對是以<xref:System.Text.RegularExpressions.Match>值表示，因此定義屬性的引號必須<xref:System.Text.RegularExpressions.Match.Groups>使用索引屬性來取得相關的群組。

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

同樣地，請注意，您要將 XML 檔新增至提供的屬性。 也請注意，如果`GetterCode`提供了函式，就可以讀取屬性，而且`SetterCode`如果提供了函數，就可以寫入屬性，因此產生的屬性是唯讀的。

現在您可以建立傳回此`Match`類型值的實例方法：

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

因為您要建立實例方法， `args.[0]`所以代表呼叫方法所在的`RegexTyped`實例，而`args.[1]`則是輸入引數。

最後，提供一個可讓您建立所提供類型之實例的函式。

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

此函式只會清除建立標準 .net Regex 實例，這會再次加入至物件，因為`obj`是所提供類型的抹除。 隨著這項變更，稍早在本主題中指定的範例 API 使用方式會如預期般運作。 下列程式碼為 complete 和 final：

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

本節說明如何建立可在其靜態參數上運作的類型提供者。 提供者會檢查靜態參數，並根據其值提供作業。

## <a name="a-type-provider-that-is-backed-by-local-data"></a>由本機資料支援的類型提供者

通常，您可能會希望型別提供者不僅以靜態參數為基礎來呈現 Api，也會顯示來自本機或遠端系統的資訊。 本節討論以本機資料為基礎的型別提供者，例如本機資料檔案。

### <a name="simple-csv-file-provider"></a>簡單的 CSV 檔案提供者

做為簡單的範例，請考慮使用以逗號分隔值（CSV）格式來存取科學資料的類型提供者。 本節假設 CSV 檔案包含標頭資料列，後面接著浮點數據，如下表所示：

|距離（計量）|時間（秒）|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

本節說明如何提供一個型別，讓您用來取得`Distance`具有型`float<meter>`別屬性和`Time`型`float<second>`別之屬性的資料列。 為了簡單起見，會進行下列假設：

- 標頭名稱不是單位或格式為 "Name （unit）"，且不包含逗號。

- 單位是[fsharp.core. UnitSystems. UnitNames moduleF#（）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義的所有系統國際（SI）單位。

- 單位全都簡單（例如，計量），而不是複合（例如，計量/秒）。

- 所有資料行都包含浮點數據。

較完整的提供者會放寬這些限制。

同樣地，第一個步驟是考慮 API 的外觀。 假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

在此情況下，編譯器應該將這些呼叫轉換成類似下列範例的內容：

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

最佳的轉譯會要求型別提供者在型別`CsvFile`提供者的元件中定義 real 型別。 型別提供者通常依賴幾個 helper 類型和方法來包裝重要的邏輯。 因為量值會在執行時間清除，所以您`float[]`可以使用做為資料列的清除類型。 編譯器會將不同的資料行視為具有不同的量數值型別。 例如，範例中的第一個資料行具有類型`float<meter>`，而`float<second>`第二個是。 不過，清除的標記法可以保持相當簡單。

下列程式碼會顯示執行的核心。

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

請注意下列有關執行的要點：

- 多載的函式允許讀取具有相同架構的原始檔案或。 當您撰寫本機或遠端資料源的型別提供者時，這個模式很常見，而此模式可讓本機檔案當做遠端資料的範本使用。

- 您可以使用傳入型別提供者函式的[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)值來解析相對檔案名。

- 您可以使用`AddDefinitionLocation`方法來定義所提供屬性的位置。 因此，如果您在`Go To Definition`提供的屬性上使用，CSV 檔案將會在 Visual Studio 中開啟。

- 您可以使用`ProvidedMeasureBuilder`類型來查閱 SI 單位，並產生相關`float<_>`的類型。

### <a name="key-lessons"></a>重要課程

本節說明如何使用資料來源本身包含的簡單架構，建立本機資料來源的類型提供者。

## <a name="going-further"></a>進一步瞭解

下列各節包含進一步研究的建議。

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>查看已清除類型的已編譯器代碼

若要讓您瞭解如何使用型別提供者來對應到發出的程式碼，請使用`HelloWorldTypeProvider`本主題稍早所使用的來查看下列函數。

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

以下是使用 ildasm 所產生之程式碼反向組譯的影像：

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

如範例所示，所有提及的型`Type1`別`InstanceProperty`和屬性都已清除，只留下涉及的執行時間類型作業。

### <a name="design-and-naming-conventions-for-type-providers"></a>型別提供者的設計和命名慣例

撰寫型別提供者時，請觀察下列慣例。

**連接通訊協定的提供者**一般來說，資料和服務連線通訊協定（例如 OData 或 SQL 連接）的大部分提供者 dll 的名稱，都應該`TypeProvider`以`TypeProviders`或結尾。 例如，使用類似下列字串的 DLL 名稱：

`Fabrikam.Management.BasicTypeProviders.dll`

請確定您提供的類型是對應命名空間的成員，並指出您所執行的連接通訊協定：

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**一般程式碼撰寫的公用程式提供者**。  對於類似于正則運算式的公用程式類型提供者，類型提供者可能是基底程式庫的一部分，如下列範例所示：

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

在此情況下，提供的類型會根據一般的 .NET 設計慣例，出現在適當的時間點：

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**單一資料來源**。 某些類型提供者會連接到單一專用資料來源，並只提供資料。 在此情況下，您應該`TypeProvider`卸載尾碼，並使用一般的 .net 命名慣例：

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

如需詳細資訊，請`GetConnection`參閱本主題稍後所述的設計慣例。

### <a name="design-patterns-for-type-providers"></a>型別提供者的設計模式

下列各節說明您可以在撰寫型別提供者時使用的設計模式。

#### <a name="the-getconnection-design-pattern"></a>GetConnection 設計模式

大部分的類型提供者都應該撰寫成`GetConnection`使用 fsharp.core. fsharp.data.typeproviders 中類型提供者所使用的模式，如下列範例所示：

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>由遠端資料和服務支援的類型提供者

在建立由遠端資料和服務支援的型別提供者之前，您必須考慮連線程式設計中固有的一系列問題。 這些問題包括下列考慮：

- 架構對應

- 發生架構變更時的活動和失效

- 架構快取

- 資料存取作業的非同步執行

- 支援查詢，包括 LINQ 查詢

- 認證和驗證

本主題不會進一步探索這些問題。

### <a name="additional-authoring-techniques"></a>其他撰寫技巧

當您撰寫自己的類型提供者時，您可能會想要使用下列其他技術。

### <a name="creating-types-and-members-on-demand"></a>視需要建立類型和成員

ProvidedType API 具有延遲的 AddMember 版本。

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

這些版本是用來建立隨選的類型空間。

### <a name="providing-array-types-and-generic-type-instantiations"></a>提供陣列類型和泛型型別具現化

您可以在任何實例上使用`MakeArrayType`一般的、 <xref:System.Type> `MakePointerType`和`MakeGenericType` ，讓提供的成員（其簽章包含陣列類型、byref 類型和泛型型別的具現化`ProvidedTypeDefinitions`），包括。

> [!NOTE]
> 在某些情況下，您可能必須在中`ProvidedTypeBuilder.MakeGenericType`使用 helper。  如需詳細資訊，請參閱[型別提供者 SDK 檔](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)。

### <a name="providing-unit-of-measure-annotations"></a>提供測量單位注釋

ProvidedTypes API 提供 helper 來提供量值注釋。 例如，若要提供類型`float<kg>`，請使用下列程式碼：

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  若要提供類型`Nullable<decimal<kg/m^2>>`，請使用下列程式碼：

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>存取專案本機或腳本-本機資源

型別提供者的每個實例都可以`TypeProviderConfig`在結構中提供一個值。 此值包含提供者的「解析資料夾」（也就是編譯的專案資料夾或包含腳本的目錄）、參考的元件清單，以及其他資訊。

### <a name="invalidation"></a>失效

提供者可以引發失效信號來通知F#語言服務，架構假設可能已變更。 當發生失效時，如果提供者是在 Visual Studio 中主控，則會重做 typecheck。 當提供者裝載于F#互動式或F#編譯器（fsc）時，將會忽略此信號。

### <a name="caching-schema-information"></a>快取架構資訊

提供者通常必須快取架構資訊的存取權。 快取的資料應該使用指定為靜態參數或使用者資料的檔案名來儲存。 架構快取的範例是`LocalSchemaFile` `FSharp.Data.TypeProviders`元件型別提供者中的參數。 在這些提供者的執行中，這個靜態參數會指示類型提供者使用指定本機檔案中的架構資訊，而不是透過網路存取資料來源。 若要使用快取的架構資訊，您也必須將`ForceUpdate`靜態`false`參數設定為。 您可以使用類似的技術來啟用線上和離線資料存取。

### <a name="backing-assembly"></a>支援元件

當您編譯`.dll`或`.exe`檔案時，產生之類型的備份 .dll 檔案會以靜態方式連結到產生的元件。 建立此連結的方法是將中繼語言（IL）類型定義和任何受管理的資源從支援元件複製到最終元件。 當您使用F# Interactive 時，不會複製支援的 .dll 檔案，而會直接載入至F#互動式進程。

### <a name="exceptions-and-diagnostics-from-type-providers"></a>來自類型提供者的例外狀況和診斷

所有來自所提供類型之成員的用法可能會擲回例外狀況。 在所有情況下，如果型別提供者擲回例外狀況，則主機編譯器會將錯誤屬性設為特定的型別提供者。

- 型別提供者例外狀況不應該導致內部編譯器錯誤。

- 型別提供者無法報告警告。

- 當型別提供者裝載于F#編譯器、 F#開發環境或F#互動式時，會攔截該提供者的所有例外狀況。 Message 屬性一律為錯誤文字，而且不會出現任何堆疊追蹤。 如果您要擲回例外狀況，您可以擲回下列範例： `System.NotSupportedException`、 `System.IO.IOException`、 `System.Exception`。

#### <a name="providing-generated-types"></a>提供產生的類型

到目前為止，本檔已說明如何提供已清除的類型。 您也可以使用中F#的類型提供者機制來提供產生的類型，這會在使用者的程式中新增為實際的 .net 類型定義。 您必須使用類型定義來參考產生的提供類型。

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

屬於F# 3.0 版的 ProvidedTypes-0.2 helper 程式碼，只有提供所產生類型的有限支援。 針對產生的型別定義，下列語句必須為 true：

- `isErased`必須設定為`false`。

- 產生的類型必須加入至新`ProvidedAssembly()`建立的，其代表產生之程式碼片段的容器。

- 提供者的元件必須具有實際支援的 .NET .dll 檔案，且該檔案在磁片上具有相符的 .dll 檔案。

## <a name="rules-and-limitations"></a>規則和限制

當您撰寫型別提供者時，請記住下列規則和限制。

### <a name="provided-types-must-be-reachable"></a>提供的類型必須是可連線的

所有提供的類型都應該可從非嵌套的類型連線。 在呼叫`TypeProviderForNamespaces`函式或`AddNamespace`呼叫時，會提供非嵌套的類型。 例如，如果提供者提供類型`StaticClass.P : T`，您必須確定 T 是非嵌套的類型，或在其底下嵌套。

例如，某些提供者具有包含這些`DataTypes` `T1, T2, T3, ...`類型的靜態類別，例如。 否則，錯誤會指出已找到元件 A 中類型 T 的參考，但在該元件中找不到類型。 如果出現此錯誤，請確認您的所有子類型都可以從提供者類型中取得。 注意：這些`T1, T2, T3...`類型稱為 *「即時」類型。* 請記得將它們放在可存取的命名空間或父類型中。

### <a name="limitations-of-the-type-provider-mechanism"></a>型別提供者機制的限制

中F#的型別提供者機制具有下列限制：

- 中F#類型提供者的基礎結構不支援提供的泛型型別或提供的泛型方法。

- 此機制不支援具有靜態參數的巢狀型別。

## <a name="development-tips"></a>開發秘訣

在開發過程中，您可能會發現下列秘訣很有説明：

### <a name="run-two-instances-of-visual-studio"></a>執行 Visual Studio 的兩個實例

您可以在一個實例中開發類型提供者，並在另一個實例中測試該提供者，因為測試 IDE 將會鎖定 .dll 檔案，以避免重建類型提供者。 因此，在第一個實例中建立提供者時，您必須關閉 Visual Studio 的第二個實例，然後您必須在建立提供者之後重新開啟第二個實例。

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>使用 fsc 調用的 Debug 型別提供者

您可以使用下列工具來叫用型別提供者：

- fsc .exe （ F#命令列編譯器）

- fsi.exe .exe （ F#互動式編譯器）

- devenv （Visual Studio）

您通常可以在測試腳本檔案（例如 run.fsx）上使用 fsc，輕鬆地對型別提供者進行最簡單的偵錯工具。 您可以從命令提示字元啟動偵錯工具。

```console
devenv /debugexe fsc.exe script.fsx
```

  您可以使用列印到 stdout 記錄。

## <a name="see-also"></a>另請參閱

- [類型提供者](index.md)
- [型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
