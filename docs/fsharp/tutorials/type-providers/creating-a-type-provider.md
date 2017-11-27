---
title: "教學課程：建立型別提供者 (F#)"
description: "了解如何在 F # 3.0 中建立您自己 F # 類型提供者，藉由檢查幾個簡單的型別提供者，來說明基本的概念。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: a1d6315c2546de12e85efdd06cf2520605cb6e91
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2017
---
# <a name="tutorial-creating-a-type-provider"></a>教學課程： 建立型別提供者

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。

在 F # 3.0 的型別提供者機制是其支援資訊豐富程式設計的重要部分。 本教學課程說明如何建立您自己的型別提供者帶您逐步說明的基本概念的幾個簡單的型別提供者的開發。 如需在 F # 類型提供者機制的詳細資訊，請參閱[型別提供者](index.md)。

F # 3.0 包含數個內建型別提供者，供常用的網際網路和企業資料服務。 這些型別提供者會提供簡單和規則的存取權 SQL 關聯式資料庫及網路 OData 和 WSDL 服務。 這些提供者也支援使用 F # LINQ 查詢，對這些資料來源。

在需要時，您可以建立自訂型別提供者，或您可以參考其他人所建立的型別提供者。 例如，您的組織可能會有提供大量且不斷增加的具名資料集，每個都有自己的穩定資料結構描述的資料服務。 您可以建立型別提供者，讀取結構描述，並對程式設計人員呈現目前資料集，強類型方式。


## <a name="before-you-start"></a>在開始之前
型別提供者機制主要設計使注入穩定資料和服務的資訊空間 F # 程式設計經驗。

這項機制不被設計用於將資訊與程式邏輯的方式在程式執行期間變更其結構描述的空間。 此外，機制不被設計為內部語言中繼程式設計，即使該網域包含一些有效的用法。 只有在需要時，您應該使用這項機制，其中的型別提供者開發會產生非常高的值。

您應該避免撰寫結構描述不可以是型別提供者。 同樣地，您應該避免使用一般 （或甚至現有） 撰寫型別提供者.NET 程式庫即已足夠。

開始之前，您可能會詢問下列問題：


- 您是否有結構描述資訊來源？ 如果是這樣，F # 和.NET 類型系統對應為何？

- 可以使用現有的 （動態具型別） API 作為的起始點實作？

- 將您和貴組織有不足，無法使用型別提供者進行寫入的含意有其價值？ 一般的.NET 程式庫會符合您的需求？

- 多少會變更您的結構描述？

- 它會在撰寫程式碼變更嗎？

- 它會變更程式碼撰寫工作階段之間嗎？

- 它會在程式執行期間變更嗎？

型別提供者最適合的情況下的結構描述在執行階段和編譯的程式碼的存留期間穩定。


## <a name="a-simple-type-provider"></a>簡單的型別提供者
這個範例是在 Samples.HelloWorldTypeProvider`SampleProviders\Providers`目錄[F # 3.0 的範例組件](http://fsharp3sample.codeplex.com)Codeplex 網站上。 提供者可提供 「 型別空間 」 含有 100 刪除的類型為下列程式碼顯示使用 F # 簽章語法並省略以外的所有詳細資料的`Type1`。 如需清除類型的詳細資訊，請參閱[詳細資料的相關清除提供型別](#details-about-erased-provided-types)本主題稍後。

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

請注意，型別和成員提供一組以靜態方式知道。 此範例不會利用提供者能夠提供取決於結構描述的類型。 下列程式碼，所述的型別提供者實作和詳細資料會包含在本主題稍後的章節。


>[!WARNING] 
可能有一些小的命名差異，這段程式碼與線上範例之間。

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

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

若要使用此提供者，開啟 Visual Studio 2012 的獨立執行個體、 建立 F # 指令碼，然後再將從指令碼提供者的參考 #r 使用下列程式碼所示：

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

然後尋找下類型`Samples.HelloWorldTypeProvider`型別提供者產生的命名空間。

您重新編譯提供者之前，請確定您已關閉所有執行個體的 Visual Studio 和 F # Interactive 會使用提供者 DLL。 否則，因為輸出 DLL 將會遭到鎖定，會發生建置錯誤。

若要使用 print 陳述式，偵錯此提供者，讓指令碼會公開提供者，有問題，然後使用下列程式碼：

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

若要使用 Visual Studio 偵錯此提供者、 系統管理認證，以開啟 Visual Studio 命令提示字元並執行下列命令：

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

或者，開啟 Visual Studio，開啟 偵錯 功能表，選擇`Debug/Attach to process…`，並附加至另一個`devenv`就可以在其中編輯指令碼的程序。 使用此方法，您可以更輕鬆地以互動方式 （具有完整的 IntelliSense 和其他功能） 的第二個執行個體中輸入運算式目標型別提供者中的特定邏輯。

您可以停用 Just My Code 偵錯更容易辨識產生的程式碼中的錯誤。 如需如何啟用或停用此功能的資訊，請參閱[使用偵錯工具巡覽程式碼](https://msdn.microsoft.com/library/y740d9d3.aspx)。 此外，您也可以設定 first-chance 例外狀況來攔截開啟`Debug`功能表，然後選擇`Exceptions`或選擇 Ctrl + Alt + E 鍵以開啟`Exceptions` 對話方塊。 在對話方塊中，在`Common Language Runtime Exceptions`，選取`Thrown`核取方塊。


### <a name="implementation-of-the-type-provider"></a>型別提供者實作
本節將引導您透過型別提供者實作的主要區段。 首先，您可以定義類型的自訂型別提供者本身：

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

此類型必須是公用的以及您必須將它與[TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947)屬性，讓個別的 F # 專案參考組件包含的型別時，編譯器會辨識型別提供者。 *Config*參數為選擇性，而且，如果有的話，包含 F # 編譯器會建立型別提供者執行個體的內容相關的組態資訊。

接下來，您實作[ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)介面。 在此情況下，您使用`TypeProviderForNamespaces`從`ProvidedTypes`應用程式開發介面的基底類型。 此協助程式類型可以立即提供有限的集合，提供命名空間，其中每個直接包含有限的固定，立即提供型別。 在此內容中，提供者*熱切*產生型別，即使它們不需要或使用。

```fsharp
inherit TypeProviderForNamespaces()
```

接下來，定義本機私用的值，指定的命名空間提供的類型，並尋找型別提供者組件本身。 這個組件稍後會使用所提供的清除類型的邏輯父型別。

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

接下來，建立函數，以提供每種類型的類型 1...Type100。 在本主題稍後的更詳細地說明此函式。

```fsharp
let makeOneProvidedType (n:int) = …
```

接下來，產生 100 提供的類型：

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

接下來，加入類型為提供的命名空間：

```fsharp
do this.AddNamespace(namespaceName, types)
```

最後，加入組件的屬性，指出您要建立型別提供者 DLL:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>提供一個型別和成員
`makeOneProvidedType`函式會提供一種類型的實際工作。

```fsharp
let makeOneProvidedType (n:int) = 
…
```

此步驟說明此函式的實作。 首先，建立將提供的類型 (類型 1，例如當 n = 1 或 Type57，當 n = 57)。

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

您應該注意下列幾點：


- 這提供型別會被清除。  因為您指出基底型別為`obj`，執行個體將會顯示類型的值為[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)中編譯的程式碼。
<br />

- 當您指定的非巢狀類型時，您必須指定組件和命名空間。 對於清除類型，應該將組件類型提供者組件本身。
<br />

接下來，將 XML 文件集加入至類型。 這份文件會延遲，也就是，計算指定，如果主機編譯器需要它。

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

接下來將提供的靜態屬性加入至類型中：

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

取得這個屬性永遠會評估為字串"Hello ！"。 `GetterCode`屬性使用 F # 引號，代表主機編譯器產生的取得此屬性的程式碼。 如需有關引號的詳細資訊，請參閱[程式碼引號 （F #）](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)。

將 XML 文件集加入至屬性。

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

現在將所提供的屬性附加至提供的類型。 您必須將提供的成員連接只能有一個型別。 否則，成員將永遠不會成為可存取。

```fsharp
t.AddMember staticProp
```

現在建立提供的建構函式不接受參數。

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode`的建構函式會傳回 F # 引號，代表呼叫建構函式時，主機編譯器產生的程式碼。 例如，您可以使用下列建構函式：

```fsharp
new Type10()
```

提供類型的執行個體將會建立與基礎資料 「 物件資料 」。 加上引號的程式碼包含的轉換[obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7)因為該類型的清除提供此型別 （如您宣告時，指定您提供的型別）。

將 XML 文件集加入至建構函式，並提供建構函式加入至提供的類型：

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

建立的第二個提供建構函式會接受一個參數：

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode`的建構函式會再次傳回 F # 引號，代表主機編譯器產生的方法呼叫的程式碼。 例如，您可以使用下列建構函式：

```fsharp
new Type10("ten")
```

與基礎資料 「 10 」 建立所提供的型別執行個體。 您可能已經注意到，`InvokeCode`函式會傳回引號。 此函式的輸入是運算式，其中每個建構函式參數的清單。 在此案例中，代表單一參數值的運算式是用於`args.[0]`。 建構函式呼叫的程式碼強制清除類型傳回值`obj`。 新增第二個提供的建構函式類型之後，您會建立提供的執行個體屬性：

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

取得這個屬性會傳回字串，即表示物件的長度。 `GetterCode`屬性會傳回 F # 引號，指定要取得屬性的主機編譯器產生的程式碼。 像`InvokeCode`、`GetterCode`函式會傳回引號。 主機編譯器會呼叫此函式的引數清單。 在此案例中的引數包括只單一運算式表示之執行個體的 getter 被呼叫時，您可以使用存取`args.[0]`。實作`GetterCode`然後 splices 結果引號，在清除類型到`obj`，以及用來滿足編譯器的機制，檢查此物件是字串類型轉換。 下一個部分`makeOneProvidedType`提供一個參數的執行個體方法。

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

最後，建立巢狀的類型，其中包含 100 個巢狀的屬性。 這個建立巢狀類型和其屬性將會延遲，也就是，計算隨。

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a>清除之提供類型有關的詳細資料
本節中的範例僅提供*清除提供的類型*，這是在下列情況中特別有用：


- 當您要撰寫的提供者只包含資料和方法的資訊空間。
<br />

- 當您要撰寫精確的執行階段型別語意不重要的資訊空間的實際用途是提供者。
<br />

- 當您要撰寫的提供者的資訊空間，所以大型且相互連結，它不會產生實際的.NET 型別資訊空間就技術上而言可行。
<br />

在此範例中，提供的每一個型別會清除輸入`obj`，所有使用型別將會都顯示為型別和`obj`中編譯的程式碼。 事實上，在這些範例中的基礎物件是字串，但類型將會顯示為`System.Object`.net 編譯的程式碼。 所有使用的類型清除，您可以使用明確的 boxing，unboxing，以及轉型至破壞清除類型。 在此情況下，使用物件時，可能會造成不是有效的轉換例外狀況。 提供者執行階段可以定義自己的私用的表示法型別，以協助防範 false 表示相互轉換。 您無法在 F # 本身中定義它們的型別。 提供的類型可能會被清除。 您必須了解後果，這兩個實際會加以語意，請使用清除您的型別提供者或提供的提供者的類型清除類型。 清除的型別並沒有實際的.NET 類型。 因此，精準反映無法掌控型別，而且如果您使用執行階段轉換和其他技術，依賴確實執行階段的類型語意，您可能會破壞清除的類型。 清除型別的 subversion 經常會導致在執行階段類型轉型例外狀況。


### <a name="choosing-representations-for-erased-provided-types"></a>選擇表示法的清除提供型別
至於清除之提供類型的一些用法，不表示法。 例如，清除提供型別可能會包含靜態屬性及成員及任何建構函式，而沒有方法或屬性會傳回類型的執行個體。 如果您可以連線的清除執行個體提供之類型，您必須考慮下列問題：


- 清除所提供的型別是什麼？
<br />
  - 清除所提供的型別是型別如何出現在已編譯的.NET 程式碼。
<br />

  - 提供的清除的類別類型的清除永遠是第一個非清除基底類型繼承鏈結中的型別。
<br />

  - 提供的清除的介面型別的清除永遠是`System.Object`。
<br />

- 所提供之類型的表示是什麼？
<br />
  - 一組可能的清除提供之類型的物件會呼叫其表示法。 在本文範例中，類型的所有清除提供表示`Type1..Type100`一定是字串的物件。
<br />

提供之類型的所有表示都必須與所提供的型別清除相容。 （否則 F # 編譯器會產生錯誤的型別提供者，使用或將會產生無法驗證.NET 程式碼並不是有效的。 如果類型提供者傳回的程式碼提供了無效的表示方式，則該類型提供者無效。

您可以使用下列方法，兩者都是很常見的選擇提供物件的表示法：


- 如果您只透過現有的.NET 型別提供強類型包裝函式，很合理的清除為該類型，為表示法，或兩者都使用該類型的執行個體類型。 當現有的方法，該型別上的大部分仍能呼應使用強類型的版本時，這個方法是適當。
<br />

- 如果您想要從任何現有的.NET API 大幅建立不同的 API，因此才會建立執行階段類型將會針對提供的類型與類型清除。
<br />

這份文件中的範例會使用所提供之物件的表示為字串。 通常，它可能適合使用其他物件，用於表示法。 例如，您可能會使用字典當做屬性包：

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

或者，您可能會在您將在執行階段用來形成的表示法，以及一或多個執行階段作業的型別提供者定義類型：

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

提供的成員然後可以建構此物件類型的執行個體：

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

在此情況下，您可能會 （選擇性） 使用此類型的類型清除為藉由指定此類型為`baseType`建構時`ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

上一節將說明如何建立簡單清除型別提供者提供了各式各樣的型別、 屬性和方法。 本章節也說明的概念的類型清除，包括一些優點和缺點從型別提供者，提供它們的型別，並討論清除類型表示法。


## <a name="a-type-provider-that-uses-static-parameters"></a>使用靜態參數的型別提供者
參數化的靜態資料的型別提供者的能力可讓許多有趣的情況下，即使在提供者不需要存取的任何本機或遠端資料時的情況下。 在本節中，您將學習一些基本技術搭配使用這類提供者。


### <a name="type-checked-regex-provider"></a>檢查 Regex 提供者類型。
假設您想要實作規則運算式的型別提供者所包裝之.NET`System.Text.RegularExpressions.Regex`文件庫中的介面會提供下列編譯時間保證：


- 正在驗證是否為有效的規則運算式。
<br />

- 提供具名的屬性比對規則運算式中的任何群組名稱為基礎。
<br />

本節示範如何使用型別提供者來建立`RegExProviderType`輸入規則運算式模式化為提供這些優點。 如果提供的模式不是有效的而且型別提供者可以擷取的群組模式中，讓您可以使用名為相符項目上的屬性來存取它們，則編譯器會回報錯誤。 當您設計的類型提供者時，您應該考慮其公開的 API 的外觀以一般使用者與此設計會轉譯成.NET 程式碼的方式。 下列範例會示範如何使用這類 API 來取得區域程式碼的元件：

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

下列範例會示範型別提供者將這些呼叫的轉譯：

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

請注意下列重點：


- 標準的 Regex 型別代表參數化`RegexTyped`型別。
<br />

- `RegexTyped`建構函式會導致 Regex 建構函式呼叫，在模式比對的靜態型別引數中傳遞。
<br />

- 結果`Match`方法都由標準`System.Text.RegularExpressions.Match`型別。
<br />

- 每個具名的群組導致所提供的屬性，並存取屬性導致系統使用的相符項目上的索引子的`Groups`集合。
<br />

下列程式碼是核心的邏輯來實作這類提供者，以及這個範例省略了加入所有成員，以提供的類型。 每個加入的成員相關的資訊，請參閱本主題稍後的適當的區段。 完整程式碼中，下載範例的[F # 3.0 的範例組件](http://fsharp3sample.codeplex.com)Codeplex 網站上。

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
let ty = ProvidedTypeDefinition(
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

請注意下列重點：


- 型別提供者會採用兩個靜態參數： `pattern`，這是強制性，而`options`，這是選擇性的 （因為提供的預設值）。
<br />

- 提供靜態引數之後，您會建立規則運算式的執行個體。 如果 Regex 格式不正確，而且使用者會報告此錯誤，這個執行個體將會擲回例外狀況。
<br />

- 內`DefineStaticParameters`回呼，定義將會傳回之後提供的引數的型別。
<br />

- 這個程式碼設定`HideObjectMethods`為 true，讓 IntelliSense 經驗會保持流暢。 這個屬性會造成`Equals`， `GetHashCode`， `Finalize`，和`GetType`来隱藏的成員從提供的物件的 IntelliSense 清單。
<br />

- 您使用`obj`為基底類型的方法，但您將使用`Regex`物件做為此類型的執行階段表示下一個範例所示。
<br />

- 若要呼叫`Regex`建構函式會擲回`System.ArgumentException`當規則運算式不是有效的。 編譯器會攔截此例外狀況，並在編譯時期或 Visual Studio 編輯器中，向使用者回報的錯誤訊息。 這個例外狀況可讓規則運算式，而不需執行應用程式進行驗證。
<br />

因為它並未包含任何有意義的方法或屬性，沒有尚未作用上述定義的類型。 首先，新增靜態`IsMatch`方法：

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

先前的程式碼定義的方法`IsMatch`，會接受字串做為輸入，並傳回`bool`。 只有麻煩的部分就是使用`args`引數內`InvokeCode`定義。 在此範例中，`args`是引號內的清單，代表這個方法的引數。 如果該方法是執行個體方法，第一個引數代表`this`引數。 不過，對於靜態方法，引數都只方法的明確引數。 請注意，加上引號的值的型別應該符合指定的傳回型別 (在此情況下， `bool`)。 另外請注意，此程式碼使用`AddXmlDoc`來確定所提供的方法也有實用文件，您可以透過 IntelliSense 提供的方法。

接下來，加入比對方法執行個體。 不過，此方法應傳回值提供的`Match`型別，如此群組可以存取在強型別的方式。 因此，您先宣告`Match`型別。 由於此類型取決於做為靜態引數提供的模式，這種類型都必須在參數化的類型定義中巢狀結構：

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

然後，您會加入一個屬性為每個群組的相符項目型別。 在執行階段，以表示相符項目`System.Text.RegularExpressions.Match`值，因此必須使用定義的屬性引號`System.Text.RegularExpressions.Match.Groups`編製索引的屬性，以取得相關的群組。

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

同樣地，請注意，您要將 XML 文件新增到所提供的屬性。 另外請注意，如果可讀取屬性`GetterCode`提供函式，且可以寫入屬性，如果`SetterCode`提供函式，所以產生的屬性唯讀。

現在您可以建立傳回值，這個執行個體方法`Match`類型：

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

因為您正在建立執行個體方法，`args.[0]`代表`RegexTyped`執行個體呼叫方法，和`args.[1]`是輸入引數。

最後，建構函式提供，以便可以建立執行個體所提供的型別。

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

建構函式只會清除建立的標準的.NET Regex 執行個體，這會再次進行 boxed 處理的物件由於`obj`是清除所提供的型別。 這項變更，指定稍早在本主題中的範例應用程式開發介面使用量會如預期般運作。 下列程式碼是完整和最終：

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



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

本節說明如何建立作業的類型提供者在其靜態參數。 提供者會檢查靜態參數，並提供其值為基礎的作業。


## <a name="a-type-provider-that-is-backed-by-local-data"></a>型別提供者，並受到本機資料
通常，您可能想顯示而不只是靜態參數從本機或遠端系統的資訊為基礎的應用程式開發介面的型別提供者。 本章節討論本機資料，例如本機資料檔為基礎的型別提供者。


### <a name="simple-csv-file-provider"></a>簡單的 CSV 檔案提供者
為簡單的範例，請考慮存取以逗號分隔值 (CSV) 格式的科學資料型別提供者。 本節假設，CSV 檔案包含標頭資料列，再浮動點資料，如下列表格所示：



|距離 （公尺）|時間 （秒）|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
本節說明如何提供可用來取得資料列的型別`Distance`型別的屬性`float<meter>`和`Time`型別的屬性`float<second>`。 為了簡單起見，請進行下列假設：


- 標頭名稱都是無單位的或具有 「 名稱 （單位） 」 的格式，且不能包含逗號。
<br />

- 單位是做為所有 Systeme 國際 (SI) 單位[Microsoft.FSharp.Data.UnitSystems.SI.UnitNames 模組 （F #）](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b)模組定義。
<br />

- 單位為所有簡單 （比方說，測量） 而非複合 （例如，計量表/秒）。
<br />

- 所有資料行包含浮動點資料。
<br />

更完整的提供者會放寬這些限制。

一次的第一個步驟是考慮應用程式開發介面的外觀。 假設有一個包含先前資料表內容的 `info.csv` 檔案 (採用逗號分隔的格式)，則提供者的使用者應該可以編寫類似下列範例的程式碼：

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

在此情況下，編譯器應該將這些呼叫轉換成結果類似下列的範例：

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

最佳的轉譯會需要的型別提供者來定義真實`CsvFile`型別提供者的組件中的型別。 型別提供者通常依賴一些協助程式類型和方法，以重要的邏輯包裝。 因為在執行階段刪除量值時，您可以使用`float[]`做為一個資料列的刪除類型。 編譯器會將不同的資料行視為具有不同的量值類型。 例如，在本例中的第一個資料行具有類型`float<meter>`，和第二個`float<second>`。 不過，它們的表示可以保持相當簡單。

下列程式碼顯示實作的核心。

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
inherit TypeProviderForNamespaces()

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

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

請注意下列有關實作的重點：


- 多載建構函式可讓原始的檔案或已讀取相同的結構描述的其中一個。 當您撰寫本機或遠端資料來源的型別提供者及此模式可讓本機檔案要作為範本用於遠端資料，此模式相當常見。
<br />  您可以使用[TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44)會傳遞至型別提供者建構函式，來解析相對檔案名稱中的值。
<br />

- 您可以使用`AddDefinitionLocation`方法來定義提供內容的位置。 因此，如果您使用`Go To Definition`上提供的屬性，CSV 檔案會在 Visual Studio 中開啟。
<br />

- 您可以使用`ProvidedMeasureBuilder`查閱 SI 單位，並產生相關的型別`float<_>`型別。
<br />

`Key Lessons`

本節說明如何使用簡單的結構描述包含在資料來源本身建立的本機資料來源的型別提供者。


## <a name="going-further"></a>繼續進行
下列各節包含進一步研究的建議。


### <a name="a-look-at-the-compiled-code-for-erased-types"></a>查看清除類型的已編譯的程式碼
若要讓型別提供者的使用方式對應至，就會發出程式碼的一些概念，看看下列的函式使用`HelloWorldTypeProvider`稍早在本主題中使用。

```fsharp
let function1 () = 
let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
obj1.InstanceProperty
```

以下是產生的程式碼解編使用 ildasm.exe 的映像：

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

如範例所示，所有提及的型別`Type1`和`InstanceProperty`屬性已被清除，離開只有在執行階段型別上的作業相關。


### <a name="design-and-naming-conventions-for-type-providers"></a>設計和型別提供者的命名慣例
撰寫型別提供者時，請觀察下列慣例。


- `Providers for Connectivity Protocols`
<br />  一般情況下，資料和服務的連線通訊協定，例如 OData 或 SQL 連接時，大部分提供者 Dll 的名稱應該結束`TypeProvider`或`TypeProviders`。 例如，使用類似如下的 DLL 名稱：
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  請確定您提供的型別是對應的命名空間的成員，並指出您實作的連線通訊協定：
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  公用程式類型提供者的規則運算式，型別提供者可能是基底文件庫的一部分，如下列範例所示：
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  在此情況下，提供的型別會根據一般的.NET 設計慣例的適當時機出現：
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  某些型別提供者連接到單一專用的資料來源，並提供只有資料。 在此情況下，您應該卸除`TypeProvider`尾碼和使用的.NET 命名標準的慣例：
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  如需詳細資訊，請參閱`GetConnection`設計為在本主題稍後所述的慣例。
<br />


### <a name="design-patterns-for-type-providers"></a>型別提供者設計模式
下列章節說明撰寫型別提供者時，您可以使用設計模式。


#### <a name="the-getconnection-design-pattern"></a>GetConnection 設計模式
大部分的型別提供者應該將編寫成使用`GetConnection`由型別中的提供者 FSharp.Data.TypeProviders.dll，如下列範例所示的模式：

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>備份遠端資料和服務的型別提供者
建立遠端資料和服務所支援的類型提供者之前，您必須考慮各種連線程式設計中固有的問題。 其中包括下列考量：


- 結構描述對應
<br />

- liveness 和結構描述變更時失效
<br />

- 結構描述快取
<br />

- 資料存取作業的非同步實作
<br />

- 支援的查詢，包括 LINQ 查詢
<br />

- 認證和驗證
<br />

本主題不會探索這些進一步的問題。


### <a name="additional-authoring-techniques"></a>其他撰寫技巧
當您撰寫您自己的型別提供者時，您可以使用下列其他技巧。


- `Creating Types and Members On-Demand`
<br />  ProvidedType API 具有延遲 AddMember 的版本。
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  這些版本可用來建立隨空間的型別。
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  使用一般進行 （其簽章包含陣列類型、 byref 類型和具現化的泛型型別） 的成員提供`MakeArrayType`， `MakePointerType`，和`MakeGenericType`System.Type，任何執行個體上包括`ProvidedTypeDefinitions`。
<br />

- `Providing Unit of Measure Annotations`
<br />  ProvidedTypes API 會提供協助提供量值的註解。 例如，若要提供的型別`float<kg>`，使用下列程式碼：
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  若要提供型別`Nullable<decimal<kg/m^2>>`，使用下列程式碼：
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  每個型別提供者執行個體可以有`TypeProviderConfig`在建構期間的值。 這個值包含 「 解析資料夾 」 提供者 （也就是 [project] 資料夾的編譯或包含的指令碼的目錄）、 參考的組件的清單和其他資訊。
<br />

- `Invalidation`
<br />  提供者可以引發失效信號，通知可能已變更的結構描述假設 F # 語言服務。 失效時，如果提供者裝載在 Visual Studio 中，會重做 typecheck。 F # Interactive 中或 F # 編譯器 (fsc.exe) 所裝載的提供者時，將會忽略此訊號。
<br />

- `Caching Schema Information`
<br />  提供者通常必須快取結構描述資訊的存取權。 使用指定的檔案名稱，做為靜態參數或做為使用者資料應該儲存快取的資料。 舉例來說，結構描述快取是`LocalSchemaFile`參數中的型別提供者中`FSharp.Data.TypeProviders`組件。 在這些提供者實作中，這個靜態參數會指示要用於指定的本機檔案，而不是透過網路存取資料來源的結構描述資訊的類型提供者。 若要使用快取結構描述資訊，您也必須設定的靜態參數`ForceUpdate`至`false`。 若要啟用線上和離線的資料存取，您可以使用類似的技術。
<br />

- `Backing Assembly`
<br />  當您編譯.dll 或.exe 檔時，產生的型別支援.dll 檔是以靜態方式連結到產生的組件。 此連結會建立從備份組件到最終組件複製的中繼語言 (IL) 型別定義和任何 managed 的資源。 當您使用 F # Interactive 時，備份.dll 檔案不複製，並會改為直接載入至 F # 互動式處理序。
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  使用提供的類型中的所有成員的所有可能會擲回例外狀況。 在所有情況下，型別提供者會擲回的例外狀況，如果主機編譯器屬性錯誤的特定型別提供者。
<br />
  - 內部編譯器錯誤應該永遠不會產生型別提供者的例外狀況。
<br />

  - 型別提供者無法報告警告。
<br />

  - 當型別提供者裝載在 F # 編譯器、 F # 開發環境中，或 F # Interactive 時，會攔截到該提供者的所有例外狀況。 訊息屬性一定是錯誤的文字，而且沒有堆疊追蹤會出現。 如果您將會擲回例外狀況，您可以擲回下列的範例：
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a>提供產生的型別
目前為止，本文件說明如何提供它們的類型。 您也可以使用在 F # 中的型別提供者機制，提供產生的型別，可加入做為實際的.NET 型別定義，到使用者的程式。 您必須參考產生提供使用型別定義的類型。

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" http://services.odata.org/Northwind/Northwind.svc/">
```

是 F # 3.0 版中的一部分 ProvidedTypes 0.2 協助程式程式碼只具有有限的支援，提供產生的型別。 下列陳述式必須是產生的型別定義，則為 true:


- IsErased 必須設為`false`。
<br />

- 提供者必須具有相符的.dll 檔案在磁碟上的實際備份.NET.dll 檔案的組件。
<br />

您也必須呼叫`ConvertToGenerated`其巢狀型別形成的封閉的集合產生型別是提供的根類型上。 指定所提供的型別定義和其巢狀型別定義的組件就會發出此呼叫，並調整`Assembly`傳回該組件的所有提供的型別定義的屬性。 只有在組件屬性的根類型上第一次存取時，就會發出組件。 主機 F # 編譯器處理 generative 型別宣告類型時，沒有存取這個屬性。


## <a name="rules-and-limitations"></a>規則和限制
當您撰寫型別提供者時，請記住下列規則和限制。


- `Provided types must be reachable.`
<br />  所有提供的類型應該是從非巢狀型別。 呼叫中指定的非巢狀型別`TypeProviderForNamespaces`建構函式或呼叫`AddNamespace`。 例如，如果提供者提供的型別`StaticClass.P : T`，您必須確定 T 的非巢狀類型或巢狀方式的其中一個。
<br />  例如，某些提供者具有靜態類別，例如`DataTypes`，包含這些`T1, T2, T3, ...`型別。 否則，錯誤為找不到組件 A 中的型別 T 的參考，但在該組件中找不到型別。 如果出現這個錯誤，請確認您所有的子類型，可以達到從提供者類型。 注意： 這些`T1, T2, T3...`類型稱為*上即時*型別。 請記得將它們放在可存取的命名空間或父類型。
<br />

- `Limitations of the Type Provider Mechanism`
<br />  F # 中的型別提供者機制有下列限制：
<br />
  - 提供給泛型類型或泛型方法所提供，不支援 F # 中的型別提供者的基礎結構。
<br />

  - 機制並不支援巢狀的類型的靜態參數。
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  `ProvidedTypes`支援程式碼具有下列規則和限制：
<br />
  1. 提供與索引的 getter 和 setter 的屬性未實作。
<br />

  2. 未實作所提供的事件。
<br />

  3. 提供的類型和資訊的物件應該只能用於 F # 中的型別提供者機制。 它們不是更廣泛做 System.Type 物件。
<br />

  4. 您可以使用引號可定義方法實作中的建構有幾項限制。 您可以參考的原始程式碼 ProvidedTypes-*版本*以查看在引號內不支援的建構。
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a>開發秘訣
您可能會發現下列秘訣有助於在開發程序。


- `Run Two Instances of Visual Studio.`您可以開發一個執行個體中的型別提供者，並測試其他的提供者，因為測試 IDE 將會防止型別提供者正在重建的.dll 檔案鎖定。 因此，您必須關閉 Visual Studio 的第二個執行個體時，第一個執行個體中，內建提供者，然後您必須重新開啟第二個執行個體後建置提供者。
<br />

- `Debug type providers by using invocations of fsc.exe.`您可以使用下列工具來叫用型別提供者：
<br />
  - fsc.exe （F # 命令列編譯器）
<br />

  - fsi.exe （F # Interactive 編譯器）
<br />

  - devenv.exe (Visual Studio)
<br />

  您可以經常使用偵錯型別提供者最容易 fsc.exe 的測試指令碼檔案 (例如，script.fsx) 上。 您可以啟動偵錯工具從命令提示字元。
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  您可以使用列印至 stdout 記錄。
<br />


## <a name="see-also"></a>另請參閱
[類型提供者](index.md)
