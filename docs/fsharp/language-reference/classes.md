---
title: 類別
description: 瞭解類別F#如何代表可以有屬性、方法和事件的物件。
ms.date: 05/16/2016
ms.openlocfilehash: 5c012d028bc1f89e3e9f5969b3461faab9aad3a0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630451"
---
# <a name="classes"></a>類別

*類別*是代表可以具有屬性、方法和事件之物件的類型。

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

類別代表 .NET 物件類型的基本描述;類別是在中F#支援物件導向程式設計的主要類型概念。

在上述語法中, 是`type-name`任何有效的識別碼。 描述`type-params`選擇性的泛型型別參數。 其包含以角括弧 (`<`和`>`) 括住的類型參數名稱和條件約束。 如需詳細資訊, 請參閱[泛型](./generics/index.md)和[條件約束](./generics/constraints.md)。 描述`parameter-list`的是函數參數。 第一個存取修飾詞屬於類型;第二個則與主要的「函式」有關。 在這兩種情況下, `public`預設值為。

您可以使用`inherit`關鍵字來指定類別的基類。 您必須為基類的參數提供引數 (以括弧括住)。

您可以使用`let`系結來宣告類別的本機欄位或函數值, 而且必須遵循系結的一般`let`規則。 `do-bindings`區段包含要在物件結構上執行的程式碼。

`member-list`包含額外的函式、實例和靜態方法宣告、介面宣告、抽象系結, 以及屬性和事件宣告。 這些內容會在[成員](./members/index.md)中說明。

搭配`identifier` 選擇性`as`關鍵字使用的會提供執行個體變數的名稱, 或自我識別碼, 可以在類型定義中用來參考該類型的實例。 如需詳細資訊, 請參閱本主題稍後的「自我識別碼」一節。

關鍵字`class` 和`end`標示定義的開始和結束是選擇性的。

相互遞迴類型 (互相參考的類型) 與`and`關鍵字聯結在一起, 就像是互相遞迴函式一樣。 如需範例, 請參閱相互遞迴類型一節。

## <a name="constructors"></a>建構函式

此函式是建立類別類型實例的程式碼。 類別的函式F#與其他 .net 語言的處理方式稍有不同。 在F#類別中, 一律會有一個主要的函式, 其引數`parameter-list`會在型別名稱後面的中描述, 而其`let`主體則`let rec`是由類別宣告開頭的 (和) 系結所組成, 而`do`遵循的系結。 主要函式的引數會在整個類別宣告的範圍中。

您可以使用`new`關鍵字新增其他的函式, 以加入成員, 如下所示:

`new`(`argument-list`) = `constructor-body`

新的函式的主體必須叫用在類別宣告最上方指定的主要函式。

下列範例說明此概念。 在下列程式碼中`MyClass` , 有兩個函式, 這是採用兩個引數的主要函式, 以及不接受引數的另一個函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>let 和 do 系結

類別`let`定義`do`中的和系結會形成主要類別的函式主體, 因此每當建立類別實例時, 就會執行這些系結。 `let`如果系結是函式, 則會將它編譯成成員。 `let`如果系結是不會在任何函式或成員中使用的值, 則會將它編譯成此函式的本機變數。 否則, 它會編譯成類別的欄位。 接`do`下來的運算式會編譯成主要的函式, 並對每個實例執行初始化程式碼。 由於任何其他的函式一律會呼叫主要的`let`函式`do` , 因此不論呼叫哪一個函式, 系結和系結一律會執行。

系結所建立`let`的欄位可以在類別的方法和屬性中存取, 不過, 它們無法從靜態方法存取, 即使靜態方法採用執行個體變數做為參數也一樣。 您無法使用本身的識別碼 (如果有的話) 來存取它們。

## <a name="self-identifiers"></a>自我識別碼

*自我識別碼*是代表目前實例的名稱。 自我識別碼類似C#或`this` C++或`Me`中的關鍵字, Visual Basic。 您可以使用兩種不同的方式定義自我識別碼, 取決於您想要讓自我識別碼位於整個類別定義的範圍內, 還是僅適用于個別的方法。

若要定義整個類別的自我識別碼, 請在 [ `as`函式參數清單] 的右括弧後面使用關鍵字, 並指定識別碼名稱。

若只要定義一個方法的自我識別碼, 請在成員宣告中提供自我識別碼, 方法名稱和句號 (.) 的前面都是分隔符號。

下列程式碼範例說明建立自我識別碼的兩種方式。 在第一行中, `as`關鍵字是用來定義自我識別碼。 在第五行中, 識別碼`this`是用來定義本身的識別碼, 其範圍限制為方法。 `PrintMessage`

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

不同于其他 .NET 語言, 您可以將自己的識別碼命名為, 但不像您想要的名稱;您不受限於`self`、 `Me`或`this`之類的名稱。

在執行系結`as` `let`之後, 才會初始化使用關鍵字宣告的自我識別碼。 因此, 它不能用在系`let`結中。 您可以在 [ `do`系結] 區段中使用自我識別碼。

## <a name="generic-type-parameters"></a>泛型類型參數

泛型型別參數是以角括弧 (`<`和`>`) 來指定, 其格式為單引號, 後面接著識別碼。 多個泛型型別參數會以逗號分隔。 泛型型別參數在整個宣告的範圍中。 下列程式碼範例顯示如何指定泛型型別參數。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

使用類型時, 會推斷型別引數。 在下列程式碼中, 推斷的型別是一系列的元組。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>指定繼承

`inherit`子句會識別直接基類 (如果有的話)。 在F#中, 只允許一個直接基底類別。 類別所執行的介面不會被視為基類。 [介面](Interfaces.md)主題中會討論介面。

您可以從衍生類別存取基類的方法和屬性, 方法是使用 language 關鍵字`base`做為識別碼, 後面接著句號 (.) 和成員的名稱。

如需詳細資訊，請參閱[繼承](inheritance.md)。

## <a name="members-section"></a>成員區段

您可以在此區段中定義靜態或實例方法、屬性、介面執行、抽象成員、事件宣告和其他函數。 「Let」和「do 系結」無法出現在此區段中。 由於成員除了類別之外, 也可以新增F#至各種類型, 因此會在個別的[成員](./members/index.md)中加以討論。

## <a name="mutually-recursive-types"></a>相互遞迴類型

當您定義以迴圈方式參考彼此的型別時, 您可以使用`and`關鍵字, 將型別定義加上字串。 關鍵字會取代第一個定義以外的所有關鍵字,如下所示。`type` `and`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

輸出是目前目錄中所有檔案的清單。

## <a name="when-to-use-classes-unions-records-and-structures"></a>使用類別、等位、記錄和結構的時機

假設有各種類型可供選擇, 您必須充分瞭解每種類型的設計, 才能針對特定情況選取適當的類型。 類別是設計用來在物件導向的程式設計內容中使用。 物件導向程式設計是針對 .NET Framework 所撰寫的應用程式中所使用的主要架構。 如果您F#的程式碼必須與 .NET Framework 或其他物件導向程式庫密切合作, 特別是當您必須從物件導向的類型系統 (例如 UI 程式庫) 進行擴充時, 類別可能是適當的。

如果您不會與物件導向程式碼緊密互通, 或如果您撰寫的程式碼是獨立的, 因而受到保護, 而無法經常與物件導向的程式碼互動, 您應該考慮使用記錄和區分等位。 單一且仔細思考的區分等位, 以及適當的模式比對程式碼, 通常可用來做為物件階層的較簡單替代方案。 如需有關區分等位的詳細資訊, 請參閱[區分](discriminated-unions.md)等位。

記錄的優點是比類別簡單, 但當類型的需求超過可透過其簡單性完成的內容時, 不適合使用記錄。 記錄基本上是值的簡單匯總, 沒有個別的可執行自訂動作的函式, 也不需要隱藏的欄位, 也不需要繼承或介面的實現。 雖然屬性和方法之類的成員可以加入記錄以使其行為更複雜, 但儲存在記錄中的欄位仍是簡單的值匯總。 如需記錄的詳細資訊, 請參閱[記錄](records.md)。

結構也適用于資料的小型匯總, 但它們與類別和記錄不同, 因為它們都是 .NET 實數值型別。 類別和記錄是 .NET 參考型別。 實值型別和參考型別的語義在值型別中是以傳值方式來傳遞。 這表示當以參數的形式傳遞或從函式傳回時, 它們會複製位。 它們也會儲存在堆疊上, 如果當做欄位使用, 則內嵌于父物件中, 而不是儲存在堆積上的個別位置。 因此, 當存取堆積的額外負荷造成問題時, 結構適用于經常存取的資料。 如需結構的詳細資訊, 請參閱[結構](structures.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [成員](./members/index.md)
- [繼承](inheritance.md)
- [介面](interfaces.md)
