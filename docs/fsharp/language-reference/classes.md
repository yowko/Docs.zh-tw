---
title: 類別
description: '瞭解 F # 類別是代表可以有屬性、方法和事件之物件的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: fd6638e0f1c08cf667a73582e19b2bb5bba46e20
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970163"
---
# <a name="classes"></a>類別

*類別* 是代表可以有屬性、方法和事件之物件的類型。

## <a name="syntax"></a>語法

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>備註

類別代表 .NET 物件類型的基本描述;類別是一種主要類型概念，支援 F # 中的物件導向程式設計。

在上述語法中， `type-name` 是任何有效的識別碼。 `type-params`描述選擇性的泛型型別參數。 它包含以角括弧括住的型別參數名稱和條件約束 (`<` 和 `>`) 。 如需詳細資訊，請參閱 [泛型](./generics/index.md) 和 [條件約束](./generics/constraints.md)。 描述函式 `parameter-list` 參數。 第一個存取修飾詞與類型有關。第二個則是主要的函式。 在這兩種情況下，預設值為 `public` 。

您可以使用關鍵字來指定類別的基類 `inherit` 。 您必須為基類的函式提供引數（以括弧括住）。

您可以使用系結來宣告類別本機的欄位或函式值 `let` ，而且必須遵循系結的一般規則 `let` 。 `do-bindings`區段包含要在物件結構上執行的程式碼。

`member-list`包含其他的函式、實例和靜態方法宣告、介面宣告、抽象系結，以及屬性和事件宣告。 這些是 [成員](./members/index.md)中的描述。

搭配 `identifier` 選擇性關鍵字使用的會 `as` 提供執行個體變數的名稱或本身的識別碼，可在類型定義中用來參考該類型的實例。 如需詳細資訊，請參閱本主題稍後的「自我識別碼」一節。

`class` `end` 標示定義開始和結束的關鍵字是選擇性的。

相互遞迴的型別（也就是彼此參考的型別）會與關鍵字聯結在一起， `and` 就像互相遞迴函數一樣。 如需範例，請參閱「相互遞迴類型」一節。

## <a name="constructors"></a>建構函式

此函式是建立類別型別實例的程式碼。 類別的函式在 F # 中的運作方式與其他 .NET 語言中的運作方式稍有不同。 在 F # 類別中，一律會有一個主要的函式，其中的引數會在 `parameter-list` 型別名稱後面，且主體是由 `let` 類別宣告開頭的 (和) 系結 `let rec` ，以及 `do` 接下來的系結所組成。 主要函式的引數位於整個類別宣告的範圍內。

您可以使用關鍵字加入其他的函式 `new` ，以新增成員，如下所示：

`new`(`argument-list`) = `constructor-body`

新的函式主體必須叫用在類別宣告頂端指定的主要函式。

下列範例將說明這個概念。 在下列程式碼中， `MyClass` 有兩個函式，這是採用兩個引數的主要函式，以及不接受引數的另一個函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>let 和 do 系結

`let`類別定義中的和系結 `do` 會形成主要類別的函式內文，因此每當建立類別實例時，就會執行這些系結。 如果系結 `let` 是函數，則會將它編譯成成員。 如果系結 `let` 是未在任何函式或成員中使用的值，則會將它編譯成函式的本機變數。 否則，它會編譯成類別的欄位。 `do`接下來的運算式會編譯成主要的函式，並對每個實例執行初始化程式碼。 因為任何其他的函式一律會呼叫主要的函式，所以不論呼叫哪一個函式，系結和系結 `let` `do` 一律都會執行。

系結所建立的欄位 `let` 可以在類別的方法和屬性中存取，不過，即使靜態方法採用執行個體變數作為參數，也無法從靜態方法存取這些欄位。 如果有的話，就無法使用自我識別碼來存取它們。

## <a name="self-identifiers"></a>自我識別碼

*自我識別碼* 是表示目前實例的名稱。 自我識別碼與 `this` c # 或 c + + 或 `Me` Visual Basic 中的關鍵字類似。 您可以使用兩種不同的方式來定義自我識別碼，視您是否要讓自我識別碼位於整個類別定義的範圍中，或僅針對個別的方法而定。

若要定義整個類別的自我識別碼，請在 [函式 `as` 參數清單] 的右括弧後面使用關鍵字，並指定識別碼名稱。

若只要定義一個方法的自我識別碼，請在方法名稱和句點 ( 之前，在成員宣告中提供自我識別碼。 ) 為分隔符號。

下列程式碼範例說明建立自我識別碼的兩種方式。 在第一行中， `as` 關鍵字是用來定義自我識別碼。 在第五行中，識別碼 `this` 是用來定義其範圍限制為方法的自我識別碼 `PrintMessage` 。

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

不同于其他 .NET 語言，您可以在想要的情況下命名自我識別碼;您不受限於、或之類的 `self` 名稱 `Me` `this` 。

使用關鍵字宣告的自我識別碼，在 `as` 基底的函式之前都不會初始化。 因此，在基底函式之前或內部使用時， `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` 會在執行時間引發。 您可以在基底的函式之後自由使用自我識別碼，例如在系結或系結中 `let` `do` 。

## <a name="generic-type-parameters"></a>泛型類型參數

泛型型別參數是以角括弧 (`<` 和 `>`) 來指定，並以單引號的形式加上識別碼。 多個泛型型別參數會以逗號分隔。 泛型型別參數在整個宣告的範圍中。 下列程式碼範例示範如何指定泛型型別參數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

使用型別時，會推斷型別引數。 在下列程式碼中，推斷的型別是一系列的元組。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>指定繼承

`inherit`子句會識別直接基類（如果有的話）。 在 F # 中，只允許一個直接基類。 類別所執行的介面不會被視為基類。 [介面主題中](Interfaces.md)會討論介面。

您可以從衍生類別存取基類的方法和屬性，方法是使用 language 關鍵字 `base` 做為識別碼，後面接著一個句點 (。 ) 和成員的名稱。

如需詳細資訊，請參閱[繼承](inheritance.md)。

## <a name="members-section"></a>成員區段

您可以在本節中定義靜態或實例方法、屬性、介面執行、抽象成員、事件宣告和其他的函式。 此區段中不能出現 Let 和 do 系結。 因為成員可以新增至類別以外的各種 F # 型別，所以會在個別的主題中討論 [成員](./members/index.md)。

## <a name="mutually-recursive-types"></a>相互遞迴類型

當您定義以迴圈方式參考彼此的型別時，您可以使用關鍵字將型別定義組成一串 `and` 。 `and`關鍵字會取代 `type` 第一個定義以外的所有關鍵詞，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

輸出是目前目錄中所有檔案的清單。

## <a name="when-to-use-classes-unions-records-and-structures"></a>使用類別、等位、記錄和結構的時機

由於有各種類型可供選擇，因此您需要充分瞭解每種類型的設計目的，以針對特定情況選取適當的類型。 類別是設計用來在物件導向程式設計環境中使用。 物件導向程式設計是針對 .NET Framework 所撰寫的應用程式中所使用的主要範例。 如果您的 F # 程式碼必須與 .NET Framework 或另一個物件導向的程式庫密切合作，特別是當您必須從物件導向的型別系統（例如 UI 程式庫）延伸時，類別可能很適合。

如果您未與物件導向程式碼緊密地互通，或您正在撰寫獨立的程式碼，因而受到保護而無法經常與物件導向程式碼互動，您應該考慮使用記錄和區分等位。 您可以使用一種簡單的方法，也就是使用適當的模式比對程式碼，將其視為更簡單的物件階層替代方法。 如需差異聯集的詳細資訊，請參閱 [區分](discriminated-unions.md)聯集。

記錄的優點是比類別更簡單，但是當類型的需求超過其簡單的需求時，記錄就不適用。 記錄基本上是值的簡單匯總，沒有可執行自訂動作的個別函式，而不需要隱藏的欄位，也不需要繼承或介面。 雖然可以將屬性和方法等成員新增至記錄，以使其行為更複雜，但儲存在記錄中的欄位仍是值的簡單匯總。 如需記錄的詳細資訊，請參閱 [記錄](records.md)。

結構也適用于小型資料匯總，但它們與類別和記錄不同，因為它們是 .NET 實數值型別。 類別和記錄是 .NET 參考型別。 實值型別和參考型別的語義在實值型別是以傳值方式傳遞的。 這表示當其以參數形式傳遞或從函式傳回時，會為位複製位。 它們也會儲存在堆疊上，或者，如果當做欄位使用，則內嵌于父物件中，而不是儲存在堆積上的個別位置。 因此，當存取堆積的額外負荷發生問題時，結構適用于經常存取的資料。 如需結構的詳細資訊，請參閱 [結構](structures.md)。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [成員](./members/index.md)
- [繼承](inheritance.md)
- [介面](interfaces.md)
