---
title: 類別 (F#)
description: '了解 F # 類別的型別，代表物件的屬性、 方法和事件的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 67164bd9f91c14f465bf05630259ad70cb8d90e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565882"
---
# <a name="classes"></a>類別

*類別*是代表物件的屬性、 方法和事件的型別。


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
類別代表基本的.NET 物件類型描述此類別是在 F # 支援物件導向程式設計的主要類型概念。

在上述語法中，`type-name`是任何有效的識別項。 `type-params`描述選擇性的泛型型別參數。 它包含型別參數名稱和角括弧括住條件約束 (`<`和`>`)。 如需詳細資訊，請參閱[泛型](generics/index.md)和[條件約束](generics/constraints.md)。 `parameter-list`描述建構函式參數。 第一個存取修飾詞都屬於型別。第二個屬於主要建構函式。 在這兩種情況下，預設值是`public`。

使用指定之類別的基底類別`inherit`關鍵字。 您必須提供引數以括號，基底類別建構函式。

宣告欄位，或函式使用的類別值`let`繫結，而且您必須遵循的一般規則`let`繫結。 `do-bindings`區段包含在物件建構時要執行的程式碼。

`member-list`組成其他建構函式、 執行個體和靜態方法宣告、 介面宣告，抽象的繫結，並且屬性和事件宣告。 這些述[成員](members/index.md)。

`identifier`搭配選擇性使用`as`關鍵字可讓執行個體變數或自我識別項，可以在類型定義中用來參考類型的執行個體名稱。 如需詳細資訊，請參閱本主題稍後的章節自我識別項。

關鍵字`class`和`end`，標記開始並定義結尾為選擇性。

相互遞迴類型，都是互相參考的類型，加入並搭配`and`一樣相互遞迴函式是關鍵字。 如需範例，請參閱相互遞迴類型一節。


## <a name="constructors"></a>建構函式
建構函式是建立類別類型的執行個體的程式碼。 類別的建構函式在 F # 中運作方式稍有不同，比在其他.NET 語言中。 在 F # 類別中，有永遠是主要的建構函式的引數中所述`parameter-list`一節的型別名稱，以及其主體包含`let`(和`let rec`) 繫結的類別宣告和開頭`do`遵循的繫結。 主要建構函式的引數是在範圍中的類別宣告。

您可以加入其他建構函式使用`new`關鍵字來新增成員，如下：

`new`(`argument-list`) = `constructor-body`

新的建構函式的主體必須叫用指定頂端的類別宣告的主要建構函式。

下列範例說明這個概念。 下列程式碼，`MyClass`有兩個建構函式，接受兩個引數和另一個建構函式的主要建構函式不接受引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a>let 和 do 繫結

`let`和`do`類別定義中的繫結表單的主要類別建構函式主體，因此執行每次建立類別執行個體時。 如果`let`繫結是函式，則它會先編譯成成員。 如果`let`繫結是不是在任何函式或成員的值，則它會先編譯成建構函式的本機變數。 否則，它會編譯為類別的欄位。 `do`遵循的運算式都會編譯成主要建構函式，和執行每個執行個體的初始化程式碼。 任何其他建構函式一定要呼叫的主要建構函式，因為`let`繫結和`do`繫結永遠執行無論哪個呼叫建構函式。

欄位所建立的`let`繫結可在整個的方法和屬性類別的存取; 不過，無法存取的靜態方法，即使靜態方法會採用做為參數的執行個體變數。 無法存取使用自我識別項，如果有的話。


## <a name="self-identifiers"></a>自我識別項

A*自我識別項*是代表目前的執行個體的名稱。 自我識別項類似`this`關鍵字以 C# 或 c + + 或`Me`在 Visual Basic 中。 您可以在兩個不同的方式，取決於您在範圍內的整個類別定義，或是只為個別的方法自我識別項中定義自我識別項。

若要定義為整個類別的自我識別項，請使用`as`關鍵字之後的右括號，建構函式參數清單，並指定識別項名稱。

若要定義本身的識別項，只有一個方法，提供在成員宣告中之前的方法名稱和做為分隔符號的句號 （.）, 自我識別項。

下列程式碼範例說明兩種方式來建立自我識別項。 在第一行，`as`關鍵字用來定義自我識別項。 在第五個列中的識別項`this`用來定義它的範圍僅限於方法的自我識別碼`PrintMessage`。

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

不同於其他.NET 語言中，您可以命名自我識別項想要;您不限於名稱例如`self`， `Me`，或`this`。

自我識別項宣告`as`關鍵字未初始化直到之後`let`執行繫結。 因此，它不能在`let`繫結。 您可以使用自我識別項中的`do`繫結區段。


## <a name="generic-type-parameters"></a>泛型型別參數

角括號中指定泛型型別參數 (`<`和`>`)、 單引號接識別項的形式。 以逗號分隔多個泛型型別參數。 泛型型別參數是在範圍中宣告。 下列程式碼範例示範如何指定泛型型別參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

使用類型時，就會推斷型別引數。 在下列程式碼中，推斷的型別會是 tuple 的一連串。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a>指定繼承

`inherit`子句會識別直接基底類別，如果有的話。 在 F # 中，允許只能有一個直接基底類別。 類別實作的介面不會視為基底類別。 介面中會討論[介面](Interfaces.md)主題。

您可以從衍生類別存取的方法和屬性的基底類別，使用該語言關鍵字`base`做為識別項，後面接著句號 （.） 和成員的名稱。

如需詳細資訊，請參閱[繼承](inheritance.md)。


## <a name="members-section"></a>成員 區段
本節中，您可以定義靜態或執行個體方法、 屬性、 介面實作，抽象成員、 事件宣告和其他建構函式。 可讓和執行繫結不能出現在這一節。 因為成員可以加入至各種不同的 F # 型別除了類別之外，因此它們會在不同的主題，討論[成員](members/index.md)。


## <a name="mutually-recursive-types"></a>相互遞迴類型
當您定義的循環方式互相參考的類型時，您的字串一起型別定義使用`and`關鍵字。 `and`關鍵字取代`type`以外，如下所示的第一個定義的所有關鍵字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

輸出是一份目前的目錄中的所有檔案。


## <a name="when-to-use-classes-unions-records-and-structures"></a>使用類別、 聯集、 記錄和結構的時機
提供的各種可從中選擇的類型，您需要深入了解的項目每個類型針對設計來選取在特定情況下的適當型別。 類別被設計來在物件導向程式設計內容中。 物件導向程式設計是.NET framework 撰寫的應用程式中使用的主控架構。 如果 F # 程式碼與.NET Framework 或另一個物件導向程式庫密切合作，尤其是如果您要擴充的物件導向的型別系統，例如 UI 程式庫類別是可能適合。

如果您不緊密地與物件導向程式碼互通，或如果您要撰寫獨立且從經常與物件導向的程式碼的互動，因此受保護的程式碼，您應該考慮使用記錄和差別等位。 單一也思考外延展差別聯集，以及適當的模式比對程式碼中，通常可用來當作物件階層架構較簡單的替代方案。 如需差別聯集的詳細資訊，請參閱[差別等位](discriminated-unions.md)。

記錄都有的優點是類別，比簡單，但記錄類型的要求超過其簡化可完成什麼時並不適當。 記錄會以基本上簡單彙總的值，可以執行自訂動作的不同建構函式、 不含隱藏欄位，而不繼承或介面的實作。 雖然成員例如屬性和方法可以加入至記錄，使其行為更複雜，儲存在記錄的欄位仍是值的簡單彙總。 如需記錄的詳細資訊，請參閱[記錄](records.md)。

結構也適用於小型的彙總的資料，但它們不同於類別與記錄，因為它們是.NET 實值類型。 類別與記錄是.NET 參考類型。 實值類型和參考類型的語意，在於傳值方式傳遞的實值型別都不同。 這表示它們複製做為參數傳遞或傳回從函式時，位元的位元。 位也儲存在堆疊上，或者，如果它們做為欄位，內嵌於父物件，而不是使用儲存在他們自己在堆積上不同的位置。 因此，結構是適用於經常存取之資料的額外負荷，存取在堆積的問題時。 如需結構的詳細資訊，請參閱[結構](structures.md)。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[成員](members/index.md)

[繼承](inheritance.md)

[介面](interfaces.md)

