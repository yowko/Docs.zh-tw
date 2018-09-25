---
title: '教學課程： 建立型別提供者 （F #）'
description: '了解如何在 F # 3.0 中建立您自己 F # 型別提供者，藉由檢查幾個簡單的型別提供者，來說明基本概念。'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109127"
---
# <a name="tutorial-create-a-type-provider"></a>教學課程： 建立型別提供者

F # 中的型別提供者機制是其支援資訊豐富程式設計的重要部分。 本教學課程說明如何建立您自己的型別提供者，方法是逐步說明的基本概念的幾個簡單的型別提供者的開發。 如需有關 F # 中的型別提供者機制的詳細資訊，請參閱[型別提供者](index.md)。

F # 生態系統包含一組常用的網際網路和企業資料服務的型別提供者。 例如: 

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/)包含型別提供者，如 JSON、 XML、 CSV 和 HTML 文件格式。

- [根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)提供強型別存取 SQL 資料庫，透過對應物件和 F # LINQ 對這些資料來源的查詢。

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)編譯時期的型別提供者的一組簽入內嵌的 F # 中的 T-SQL。

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/)是較舊型別提供者只能搭配.NET Framework 程式設計中存取 SQL、 Entity Framework、 OData 及 WSDL 資料服務使用的集合。

必要時，您可以建立自訂的型別提供者，或您可以參考其他人所建立的型別提供者。 例如，您的組織可能會有提供大量且不斷增加的已命名的資料集，各有自己的穩定資料結構描述的資料服務。 您可以建立型別提供者讀取結構描述，並採用強類型的方式，呈現給程式設計人員的目前的資料集。

## <a name="before-you-start"></a>在開始之前

型別提供者機制主要設計使插入穩定的資料和服務的資訊空間 F # 程式設計經驗。

這項機制的目的不是讓您插入結構描述變更的相關程式邏輯的方式在程式執行期間的資訊空間。 此外，機制不被專為內部語言中繼程式設計，即使該網域包含一些有效的用法。 只有在必要時，您應該使用這項機制，其中的型別提供者開發會產生非常高的值。

您應該避免撰寫結構描述無法使用其中的型別提供者。 同樣地，您應該避免在一般 （或甚至有），撰寫型別提供者.NET 程式庫即已足夠。

在開始之前，您可能會詢問下列問題：

- 您有結構描述資訊來源？ 如果是這樣，什麼是 F # 和.NET 型別系統的對應？

- 可以您使用現有的 （動態型別） API 做為起點實作？

- 將您和貴組織有不足，無法使用的型別提供者，可撰寫其值得嗎？ 一般的.NET 程式庫會符合您的需求？

- 多少會變更您的結構描述？

- 它會變更期間撰寫程式碼嗎？

- 它將編碼工作階段之間變更嗎？

- 它會在程式執行期間變更嗎？

型別提供者最適合的結構描述在執行階段和編譯的程式碼的存留期內穩定的情況。

## <a name="a-simple-type-provider"></a>簡單的型別提供者

這個範例是中的範例類似 sampleproviders\providers`examples`目錄[F # 型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)。 提供者會使用 「 類型空間 」，其中包含 100 清除的型別，為下列程式碼示範使用 F # 簽章語法並省略詳細資料，如以外的所有`Type1`。 如需清除類型的詳細資訊，請參閱 <<c0> [ 詳細資料的相關清除提供類型](#details-about-erased-provided-types)本主題稍後的。

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

請注意已確知的一組型別和成員提供。 此範例不會使用提供者能夠提供取決於結構描述的類型。 型別提供者實作會概述下列程式碼，以及本主題稍後的章節涵蓋詳細資料。

>[!WARNING]
可能會有這段程式碼與線上範例之間的差異。

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

若要使用此提供者，開啟 Visual Studio 的個別執行個體，建立 F # 指令碼，，然後新增您的指令碼提供者的參考使用 #r 下列程式碼所示：

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

然後尋找下方類型`Samples.HelloWorldTypeProvider`型別提供者產生的命名空間。

重新編譯提供者之前，請確定您已關閉所有執行個體的 Visual Studio 和 F # Interactive 所使用的提供者 DLL。 因為輸出 DLL 將會遭到鎖定，否則會發生建置錯誤。

若要使用 print 陳述式，偵錯此提供者，請公開 （expose） 的提供者的問題的指令碼並接著使用下列程式碼：

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

若要使用 Visual Studio 偵錯此提供者、 系統管理認證，以開啟 Visual Studio 命令提示字元並執行下列命令：

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

或者，開啟 Visual Studio，開啟 偵錯 功能表，選擇`Debug/Attach to process…`，並將附加至另一個`devenv`您要在其中編輯指令碼的程序。 使用此方法，您可以更輕鬆地以互動方式 （使用完整的 IntelliSense 和其他功能） 的第二個執行個體中輸入運算式目標型別提供者中的特定邏輯。

您可以停用 Just My Code 偵錯，以更精確識別產生程式碼中的錯誤。 如需有關如何啟用或停用這項功能的資訊，請參閱 <<c0> [ 使用偵錯工具巡覽程式碼](/visualstudio/debugger/navigating-through-code-with-the-debugger)。 此外，您也可以設定開啟攔截 first-chance 例外狀況`Debug`功能表，然後選擇`Exceptions`或 [選擇 Ctrl + Alt + E 鍵以開啟`Exceptions`] 對話方塊。 在該對話方塊中，在`Common Language Runtime Exceptions`，選取`Thrown`核取方塊。

### <a name="implementation-of-the-type-provider"></a>型別提供者實作

本節會引導您的型別提供者實作的主要區段。 首先，您可以定義型別本身的自訂型別提供者：

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

這種類型必須是公用，而且必須加以標示[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性，讓個別的 F # 專案參考組件包含型別時，編譯器會辨識型別提供者。 *Config*參數為選擇性，而且，如果有的話，包含 F # 編譯器會建立型別提供者執行個體的內容相關的組態資訊。

接下來，您會實作[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。 在此案例中，您會使用`TypeProviderForNamespaces`從輸入`ProvidedTypes`API 的基底類型。 此協助程式類型可以立即提供有限的集合，提供命名空間，其中每一個直接包含有限數量的其修正中，立即提供型別。 在此情況下，提供者*提早*產生型別，即使它們不需要或使用。

```fsharp
inherit TypeProviderForNamespaces(config)
```

接下來，定義本機私用的值，指定的命名空間提供的類型，並尋找型別提供者組件本身。 這個組件做為項目的邏輯父類型的類型清除所提供的更新版本。

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

接下來，建立函數，以提供每個型別 Type1...Type100。 本主題稍後更詳細地說明此函式。

```fsharp
let makeOneProvidedType (n:int) = …
```

接下來，產生 100 提供的類型：

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

接下來，新增類型為提供的命名空間：

```fsharp
do this.AddNamespace(namespaceName, types)
```

最後，新增組件的屬性，指出您要建立型別提供者 DLL:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>提供一種類型和其成員

`makeOneProvidedType`函式會提供一種類型的實際工作。

```fsharp
let makeOneProvidedType (n:int) = 
…
```

此步驟說明此函式的實作。 首先，建立 提供的型別 (例如 Type1，當 n = 1 或 Type57，當 n = 57)。

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

您應該注意下列幾點：

- 這提供型別會清除。  因為您指定的基底類型是`obj`，執行個體將會顯示為類型的值[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)中編譯的程式碼。

- 當您指定的非巢狀型別時，您必須指定組件和命名空間。 對於它們的類型，應該將組件類型提供者組件本身。

接下來，加入類型的 XML 文件。 這份文件會延遲，也就是，如果主機編譯器需要計算點播。

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

接下來將提供的靜態屬性加入類型：

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

取得這個屬性一律會評估為字串"Hello ！"。 `GetterCode`屬性會使用 F # 引號，表示主編譯器產生的取得此屬性的程式碼。 如需有關引號的詳細資訊，請參閱 <<c0> [ 程式碼引號 （F #）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。

將 XML 文件加入至屬性。

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

現在提供的型別中附加所提供的屬性。 您必須將提供的成員附加至只能有一個型別。 否則，成員絕對不會存取。

```fsharp
t.AddMember staticProp
```

現在建立提供的建構函式未採用參數。

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode`的建構函式會傳回 F # 引號，代表呼叫建構函式時，主編譯器產生的程式碼。 例如，您可以使用下列建構函式：

```fsharp
new Type10()
```

提供型別的執行個體將會建立與基礎資料 「 物件資料 」。 加上引號的程式碼包含到轉換[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型的清除提供此型別 （如您指定當您宣告提供的型別）。

將 XML 文件加入建構函式，然後將提供的建構函式提供的型別：

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

建立的第二個提供建構函式會採用一個參數：

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode`的建構函式一次傳回的 F # 引號，表示主編譯器產生的方法呼叫的程式碼。 例如，您可以使用下列建構函式：

```fsharp
new Type10("ten")
```

提供型別的執行個體被建立與基礎資料 「 10 」。 您可能已經發現，`InvokeCode`函式會傳回引號。 此函式的輸入是運算式，其中每個建構函式參數清單。 在此案例中，代表單一參數值的運算式是用於`args.[0]`。 建構函式呼叫的程式碼強制清除類型的傳回值轉型`obj`。 您將第二個提供的建構函式加入至型別之後，您會建立提供的執行個體屬性：

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

取得這個屬性會傳回字串，表示物件的長度。 `GetterCode`屬性會傳回指定主機編譯器會產生要取得其屬性的程式碼 F # 引號。 像是`InvokeCode`，則`GetterCode`函式會傳回引號。 主機編譯器會呼叫此函式的引數清單。 在此情況下，引數包含只是單一運算式，表示執行個體的呼叫 getter，您可以存取使用`args.[0]`。實作`GetterCode`然後將結果的引號在清除輸入到 splices `obj`，並轉型來滿足編譯器的機制，來檢查此物件是字串類型。 下一個部分`makeOneProvidedType`提供一個參數的執行個體方法。

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

最後，建立巢狀的類型，其中包含 100 個巢狀的屬性。 這個建立巢狀類型和其屬性會延遲，也就是，計算點播。

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

### <a name="details-about-erased-provided-types"></a>它們提供類型的詳細資料

在這一節，提供僅*清除所提供的型別*，這是在下列情況中特別有用：

- 當您在撰寫只包含資料和方法的資訊空間的提供者。

- 當您在撰寫正確的執行階段型別語意不重要的資訊空間的實際用途是提供者。

- 當您在撰寫且因此大型互連，不產生真正的.NET 類型的資訊空間技術上可行的資訊空間的提供者。

在此範例中，提供的每一個型別會清除輸入`obj`，所有使用的類型會都顯示為型別及`obj`中編譯的程式碼。 事實上，在這些範例中的基礎物件是字串，但類型會顯示為`System.Object`在.NET 中編譯的程式碼。 所有使用的類型清除，您可以使用明確的 boxing 處理，unboxing，並將轉換可以破壞清除類型。 在此情況下，使用物件時，可能會造成無效轉換例外狀況。 提供者執行階段可以定義自己的私用表示型別，以協助防範 false 表示法。 您無法在 F # 本身中定義它們的類型。 提供的類型可能會被刪除。 您必須了解後果，這兩個實際會加以語意，使用 清除您的型別提供者或提供的提供者的類型清除類型。 它們的類型都有沒有真正的.NET 型別。 因此，您無法準確的反映類型，而且您可能會破壞它們的型別，如果您使用執行階段轉換和其他技術，依賴確切執行階段型別語意。 清除類型的 subversion 經常會導致在執行階段的類型轉換例外狀況。

### <a name="choosing-representations-for-erased-provided-types"></a>選擇表示法，如清除所提供的類型

如需清除的提供類型的一些用途，不表示需要。 比方說，它們提供型別可能會包含靜態屬性和成員並沒有建構函式，而沒有方法或屬性，則會傳回型別的執行個體。 如果您可以連線到它們的執行個體提供型別，您必須考慮下列問題：

**在提供型別的清除是什麼？**

- 在提供型別的清除是類型出現在已編譯的.NET 程式碼的方式。

- 提供它們的類別型別的清除永遠是第一個非清除基底類型繼承鏈結中的型別。

- 提供的清除的介面型別的清除總是`System.Object`。

**提供的型別表示有哪些？**

- 一組可能的物件，為它們提供型別會呼叫其表示法。 在本文中範例中，所有清除所提供的表示型別`Type1..Type100`永遠是字串的物件。

所有提供的型別表示法必須與提供的類型清除相容。 （否則 F # 編譯器將會發生錯誤的型別提供者中，使用或無法驗證不是有效的.NET 程式碼將會產生。 如果型別提供者傳回的程式碼提供了無效的表示方式，則該型別提供者無效。

您可以使用下列其中一個方法，這兩者都是很常見的其中一種選擇提供物件的表示法：

- 如果您只需透過現有的.NET 型別提供強型別包裝函式，它通常適合您若要清除為該型別，表示法，或兩者皆為使用該類型的執行個體的類型。 當該類型上的現有方法的大部分仍能呼應使用強類型的版本時，適合使用這種方法。

- 如果您想要從任何現有的.NET API 大幅建立不同的 API，合理來建立要提供的類型的表示法與型別清除執行階段類型。

這份文件中的範例會使用字串，以提供物件的表示法。 通常，可能適合用於表示法中的其他物件。 比方說，您可能會使用字典，為屬性包：

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

或者，您可能在您將在執行階段用來形成的表示法，以及一或多個執行階段作業的型別提供者中定義類型：

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

提供的成員可以再建構此物件類型的執行個體：

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

在此情況下，您可能 （選擇性） 使用此類型為型別清除藉由指定為此型別`baseType`建構時`ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>索引鍵的課程

上一節會說明如何建立簡單清除型別提供者提供了各式各樣的型別、 屬性和方法。 本節也說明類型清除，包括的一些優點和缺點提供它們的型別從型別提供者的概念，並討論它們的類型表示法。

## <a name="a-type-provider-that-uses-static-parameters"></a>使用靜態參數的型別提供者

將參數化的靜態資料的型別提供者的能力可讓許多有趣的情況下，即使是在提供者不需要存取任何本機或遠端資料的情況下。 在本節中，您將學習一些基本技術搭配使用這類提供者。

### <a name="type-checked-regex-provider"></a>檢查 Regex 提供者類型。

假設您想要實作規則運算式的型別提供者包裝.NET<xref:System.Text.RegularExpressions.Regex>提供以下的編譯時期保證的介面中的程式庫：

- 正在驗證規則運算式是否有效。

- 提供比對規則運算式中的任何群組名稱為基礎的具名的屬性。

本節說明如何使用型別提供者來建立`RegexTyped`輸入規則運算式模式會將參數化以提供這些優點。 如果提供的模式不是有效的而且型別提供者可以擷取群組模式中，讓您可以使用名為 比對的屬性來存取它們，編譯器會報告發生錯誤。 當您設計型別提供者時，您應該考慮其公開的 API 外觀一般使用者與此設計會轉譯成.NET 程式碼的方式。 下列範例示範如何使用這類 API 來取得區域程式碼的元件：

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

下列範例會顯示型別提供者將這些呼叫的轉譯：

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

請注意下列幾點：

- 標準的 Regex 型別代表參數化`RegexTyped`型別。

- `RegexTyped` Regex 建構函式、 靜態型別引數的模式比對中的呼叫會產生建構函式。

- 結果`Match`方法都由標準<xref:System.Text.RegularExpressions.Match>型別。

- 提供的屬性，會產生每個具名的群組，並存取屬性的相符項目上的索引子會產生`Groups`集合。

下列的程式碼來實作這類提供者，邏輯的核心，而且這個範例省略了提供的型別所有成員的加入。 如需每個新增的成員，請參閱本主題稍後的適當區段。 完整的程式碼，下載範例[F # 3.0 範例套件](https://fsharp3sample.codeplex.com)Codeplex 網站上。

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

- 型別提供者會採用兩個靜態參數： `pattern`，這是必要項目，而`options`，這是選擇性的 （因為提供的預設值）。

- 提供靜態引數之後，您會建立規則運算式的執行個體。 如果 Regex 的格式不正確，而且使用者將會報告此錯誤，這個執行個體將會擲回例外狀況。

- 內`DefineStaticParameters`回呼中，您定義之後提供的引數，將傳回的型別。

- 此程式碼會設定`HideObjectMethods`為 true，讓 IntelliSense 體驗將會保持精簡。 這個屬性會導致`Equals`， `GetHashCode`， `Finalize`，和`GetType`来隱藏的成員從 IntelliSense 清單中提供的物件。

- 您使用`obj`作為基底類型的方法，但您將使用`Regex`物件做為下一個範例會示範這種執行階段表示。

- 若要在呼叫`Regex`建構函式會擲回<xref:System.ArgumentException>當規則運算式不是有效的。 編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者回報的錯誤訊息。 這個例外狀況可讓規則運算式，而不需執行應用程式進行驗證。

上面所定義的型別尚未有用因為它並未包含任何有意義的方法或屬性。 首先，新增靜態`IsMatch`方法：

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

先前的程式碼定義的方法`IsMatch`，它會接受字串做為輸入，並傳回`bool`。 唯一比較麻煩的部分就是使用`args`內的引數`InvokeCode`定義。 在此範例中，`args`是引號，代表這個方法的引數清單。 如果方法是執行個體方法，第一個引數代表`this`引數。 不過，對於靜態方法，引數是只方法的明確引數。 請注意，加上引號的值的型別應該符合指定的傳回型別 (在此情況下， `bool`)。 另外請注意，此程式碼使用`AddXmlDoc`方法以確定提供的方法也有您可以透過 IntelliSense 提供的有用文件。

接下來，新增執行個體比對方法。 不過，此方法應傳回所提供的值`Match`型別，如此群組可以存取在強型別的方式。 因此，您首先宣告`Match`型別。 因為此類型取決於提供靜態引數作為模式，這種類型都必須在參數化型的別定義中巢狀結構：

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

然後，您會加入一個屬性為每個群組的相符項目型別。 在執行階段，以表示相符項目<xref:System.Text.RegularExpressions.Match>值，因此必須使用定義的屬性將引號<xref:System.Text.RegularExpressions.Match.Groups>編製索引的屬性，以取得相關的群組。

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

同樣地，請注意，您要將 XML 文件新增到所提供的屬性。 另外請注意，如果可讀取的屬性`GetterCode`提供函式，和可寫入屬性，如果`SetterCode`提供函式，因此產生的屬性唯讀。

現在您可以建立傳回值，這個執行個體方法`Match`類型：

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

因為您會建立執行個體方法，`args.[0]`代表`RegexTyped`執行個體呼叫方法，和`args.[1]`是輸入引數。

最後，提供一個建構函式，以便可以建立的提供類型執行個體。

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

建構函式只會清除建立標準的.NET Regex 執行個體，這會再次進行 boxed 處理物件因為`obj`是提供的類型清除。 這項變更，與本主題稍早所述的範例 API 使用量會如預期般運作。 下列程式碼是完整且最終：

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

### <a name="key-lessons"></a>索引鍵的課程

本節說明如何建立能在其靜態參數的運作方式的型別提供者。 提供者會檢查靜態參數，並提供其值為基礎的作業。

## <a name="a-type-provider-that-is-backed-by-local-data"></a>型別提供者，並受到本機資料

通常，您可以呈現 Api 的靜態參數不僅從本機或遠端系統的資訊為基礎的型別提供者。 本章節將討論本機資料，例如本機資料檔案為基礎的型別提供者。

### <a name="simple-csv-file-provider"></a>簡易的 CSV 檔案提供者

簡單的範例，請考慮用於存取以逗號分隔值 (CSV) 格式的科學資料的型別提供者。 本節假設，CSV 檔案包含標頭資料列，再浮動點資料，如下表所示：

|距離 （計量）|時間 （秒）|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

本節說明如何提供您可用來取得資料列型別`Distance`型別的屬性`float<meter>`並`Time`型別的屬性`float<second>`。 為了簡單起見，會進行下列假設：

- 標頭名稱都是無單位或 「 名稱 （單位） 」 的格式，並不包含逗號。

- 單位是為所有 Systeme International (SI) 單位[Microsoft.FSharp.Data.UnitSystems.SI.UnitNames 模組 （F #）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義。

- 單位是所有簡單 （例如，計量） 而不是複合 （比方說，計量表/秒）。

- 所有的資料行包含浮點數資料。

更完整的提供者會放寬這些限制。

同樣地，首先是 API 的外觀，請考慮。 假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

在此情況下，編譯器應該將這些呼叫轉換成類似下列的範例：

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

最佳的轉譯會需要型別提供者，來定義真實`CsvFile`型別提供者的組件中的型別。 型別提供者通常需仰賴幾個協助程式類型和方法，來包裝重要邏輯而定。 由於量值就會清除在執行階段，您可以使用`float[]`做為清除類型的資料列。 編譯器會將不同的資料行視為具有不同的量值類型。 例如，在本例中的第一個資料行具有類型`float<meter>`，第二個`float<second>`。 不過，它們的表示可以保持相當簡單。

下列程式碼會顯示實作的核心。

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

請注意下列有關實作的重點：

- 原始檔或可讀取相同的結構描述，可讓多載的建構函式。 當您撰寫本機或遠端資料來源的型別提供者並將此模式可讓本機檔案做為遠端資料範本，此模式相當常見。

- 您可以使用[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)會傳遞至型別提供者建構函式，來解析相對檔案名稱中的值。

- 您可以使用`AddDefinitionLocation`方法來定義所提供的屬性位置。 因此，如果您使用`Go To Definition`上提供的屬性，CSV 檔案會在 Visual Studio 中開啟。

- 您可以使用`ProvidedMeasureBuilder`若要查詢的 SI 單位，並產生相關的型別`float<_>`型別。

### <a name="key-lessons"></a>索引鍵的課程

本節說明如何使用簡單的結構描述包含在資料來源本身中建立本機資料來源的型別提供者。

## <a name="going-further"></a>繼續進行

下列各節包含需進一步的研究的建議。

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>看看清除類型的已編譯程式碼

為了讓您了解如何使用型別提供者對應，就會發出的程式碼，看看下列函式使用`HelloWorldTypeProvider`用稍早在本主題中。

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

以下是產生的程式碼使用 ildasm.exe 反向組譯的映像：

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

如範例所示，型別的所有提及`Type1`而`InstanceProperty`屬性已清除，保留所涉及的只有在執行階段型別上的作業。

### <a name="design-and-naming-conventions-for-type-providers"></a>設計和型別提供者的命名慣例

撰寫型別提供者時，請觀察下列慣例。

**提供者的連接通訊協定**一般而言，大部分的提供者 Dll 的資料和服務的連線通訊協定，例如 OData 或 SQL 連接時，名稱應該結束於`TypeProvider`或`TypeProviders`。 例如，使用類似如下的 DLL 名稱：

```
  Fabrikam.Management.BasicTypeProviders.dll
```

請確定您提供的型別是對應的命名空間的成員，並指出您所實作的連線通訊協定：

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**撰寫一般程式碼的公用程式提供者**。  公用程式類型提供者，例如規則運算式，型別提供者可能屬於基底的程式庫，如下列範例所示：

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

在此情況下，提供的型別會出現在適當的時間點，根據一般的.NET 設計慣例：

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

**單一資料來源**。 某些型別提供者連接到單一的專用的資料來源，並只提供資料。 在此情況下，您應該卸除`TypeProvider`後置詞，並使用一般的慣例，.NET 命名：

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

如需詳細資訊，請參閱`GetConnection`設計會在本主題稍後描述的慣例。

### <a name="design-patterns-for-type-providers"></a>型別提供者設計模式

下列各節說明您可以撰寫型別提供者時使用的設計模式。

#### <a name="the-getconnection-design-pattern"></a>GetConnection 設計模式

大部分的型別提供者應撰寫成使用`GetConnection`模式，可由型別中的提供者 FSharp.Data.TypeProviders.dll，如下列範例所示：

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>遠端資料和服務所支援的型別提供者

建立遠端資料和服務所支援的類型提供者之前，您必須考慮各種連線程式設計中固有的問題。 這些問題包括下列考量：

- 結構描述對應

- 作用與結構描述變更時失效

- 結構描述快取

- 非同步處理實作的資料存取作業

- 支援的查詢，包括 LINQ 查詢

- 認證和驗證

本主題不會探索這些在進一步的問題。

### <a name="additional-authoring-techniques"></a>其他的撰寫技術

當您撰寫您自己的型別提供者時，您可以使用下列其他技巧。

### <a name="creating-types-and-members-on-demand"></a>建立型別和成員依需求

ProvidedType API 已延遲 AddMember 的版本。

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

這些版本用來建立隨空間的型別。

### <a name="providing-array-types-and-generic-type-instantiations"></a>提供陣列型別和泛型類型具現化

要提供的成員 （其簽章包含陣列類型、 byref 類型和具現化的泛型型別） 使用一般`MakeArrayType`， `MakePointerType`，並`MakeGenericType`任何執行個體上<xref:System.Type>，其中包括`ProvidedTypeDefinitions`。

> [!NOTE]
> 在某些情況下，您可能必須使用這個 helper `ProvidedTypeBuilder.MakeGenericType`。  請參閱[型別提供者 SDK 文件](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations)如需詳細資訊。

### <a name="providing-unit-of-measure-annotations"></a>提供的量值註釋的單位

ProvidedTypes API 會提供協助程式，提供量值註釋。 例如，若要提供型別`float<kg>`，使用下列程式碼：

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  若要提供型別`Nullable<decimal<kg/m^2>>`，使用下列程式碼：

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>存取專案-本機位址或指令碼-本機資源

您可以指定每個型別提供者執行個體`TypeProviderConfig`在建構期間的值。 此值包含 「 解析資料夾 」 提供者 （也就是編譯或包含的指令碼的目錄的專案資料夾）、 參考組件、 清單和其他資訊。

### <a name="invalidation"></a>失效

提供者可以引發失效的訊號，來通知的結構描述的假設可能已變更的 F # 語言服務。 失效時，如果提供者裝載在 Visual Studio 中，會重做 typecheck。 F # Interactive 中或 F # 編譯器 (fsc.exe) 所裝載的提供者時，將會忽略此訊號。

### <a name="caching-schema-information"></a>快取的結構描述資訊

提供者通常必須快取結構描述資訊的存取權。 使用指定的檔案名稱，做為靜態參數，或做為使用者資料應該儲存快取的資料。 舉例來說，結構描述快取`LocalSchemaFile`參數中的型別提供者中`FSharp.Data.TypeProviders`組件。 在這些提供者實作中，此靜態的參數會指示型別提供者，用於指定的本機檔案，而不是透過網路存取的資料來源的結構描述資訊。 若要使用快取的結構描述資訊，您也必須設定靜態參數`ForceUpdate`至`false`。 若要啟用線上和離線的資料存取，您可以使用類似的技巧。

### <a name="backing-assembly"></a>備份組件

當您編譯`.dll`或`.exe`檔案，支援.dll 檔案產生的型別以靜態方式連結到產生的組件。 從備份組件，到最終組件複製的中繼語言 (IL) 型別定義和任何受管理的資源會建立此連結。 當您使用 F # Interactive 時，支援.dll 檔案不會複製，並會改為直接載入至 F # 互動式程序。

### <a name="exceptions-and-diagnostics-from-type-providers"></a>例外狀況和診斷從型別提供者

從提供的類型的所有成員的所有使用可能會擲都回例外狀況。 在所有情況下，型別提供者會擲回的例外狀況，如果主機編譯器屬性錯誤的特定型別提供者。

- 內部編譯器錯誤應該永遠不會產生型別提供者例外狀況。

- 型別提供者無法回報警告。

- 當型別提供者裝載中的 F # 編譯器、 F # 開發環境，或 F # Interactive 時，會攔截所有例外狀況，該提供者。 訊息屬性一律會是錯誤的文字，並沒有堆疊追蹤會出現。 如果您將會擲回例外狀況，您可以擲回下列的範例： `System.NotSupportedException`， `System.IO.IOException`， `System.Exception`。

#### <a name="providing-generated-types"></a>提供產生的型別

到目前為止，本文件說明如何提供它們的類型。 您也可以使用 F # 中的型別提供者機制，提供產生的型別，這會新增為真正的.NET 型別定義，到使用者的程式。 您必須參考產生提供使用型別定義的類型。

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

是 F # 3.0 版本的一部分 ProvidedTypes 0.2 協助程式程式碼只能進行有限的支援，提供產生的型別。 下列陳述式必須是產生的型別定義，則為 true:

- `isErased` 必須設定為`false`。

- 產生的型別必須新增至新建構`ProvidedAssembly()`，代表產生的程式碼片段的容器。

- 提供者必須具有相符的.dll 檔案，在磁碟上的實際支援.NET.dll 檔案的組件。

## <a name="rules-and-limitations"></a>規則和限制

當您撰寫型別提供者時，請記住下列規則和限制。

### <a name="provided-types-must-be-reachable"></a>提供的類型必須是可連線

提供類型應該是可從非巢狀型別。 呼叫中指定的非巢狀型別`TypeProviderForNamespaces`建構函式或呼叫`AddNamespace`。 例如，如果提供者提供的型別`StaticClass.P : T`，您必須確定 T 是在非巢狀型別或巢狀在下一個。

比方說，某些提供者都有靜態類別，如`DataTypes`，其中包含這些`T1, T2, T3, ...`型別。 否則，錯誤會指出，找不到組件 A 中的型別 T 的參考，但在該組件中找不到類型。 如果出現這個錯誤，請確認您所有的子類型，可從提供者類型。 注意： 這些`T1, T2, T3...`類型指*上即時*型別。 請務必將它們放在可存取的命名空間或父類型。

### <a name="limitations-of-the-type-provider-mechanism"></a>型別提供者機制的限制

F # 中的型別提供者機制具有下列限制：

- 提供泛型類型，或提供泛型方法，不支援 F # 中的型別提供者的基礎結構。

- 機制不支援巢狀的類型的靜態參數。

## <a name="development-tips"></a>開發秘訣

您可能會發現下列秘訣有助於在開發程序。

### <a name="run-two-instances-of-visual-studio"></a>執行 Visual studio 的兩個執行個體

您可以開發一個執行個體中的型別提供者，並在其他測試提供者，因為測試的 IDE 會防止型別提供者正在重建的.dll 檔案採用鎖定。 因此，您必須先關閉 Visual Studio 的第二個執行個體，而第一個執行個體中，內建提供者，然後您就必須重新開啟第二個執行個體建立提供者後。

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>偵錯使用 fsc.exe 的引動過程的型別提供者

您可以使用下列工具，以叫用型別提供者：

- fsc.exe （F # 命令列編譯器）

- fsi.exe （F # Interactive 編譯器）

- devenv.exe (Visual Studio)

您可以經常使用偵錯型別提供者最容易 fsc.exe 的測試指令碼檔案 (例如 script.fsx)。 您可以啟動偵錯工具從命令提示字元。

```
  devenv /debugexe fsc.exe script.fsx
```

  您可以使用列印至 stdout 記錄。

## <a name="see-also"></a>另請參閱

- [類型提供者](index.md)
- [型別提供者 SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
