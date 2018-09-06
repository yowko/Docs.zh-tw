---
title: 類別 (F#)
description: '了解如何 F # 類別表示可以有屬性、 方法和事件的物件型別。'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802103"
---
# <a name="classes"></a>類別

*類別*是型別，代表可以有屬性、 方法和事件的物件。

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

類別代表基本的.NET 物件類型描述此類別是以 F # 支援物件導向程式設計的主要類型概念。

在上述語法中，`type-name`是任何有效的識別碼。 `type-params`描述選擇性的泛型型別參數。 該包含型別參數名稱和角括弧括住的條件約束 (`<`和`>`)。 如需詳細資訊，請參閱 <<c0> [ 泛型](generics/index.md)並[條件約束](generics/constraints.md)。 `parameter-list`描述建構函式參數。 第一個存取修飾詞與類型;第二個是關於的主要建構函式。 在這兩種情況下，預設值是`public`。

使用指定之類別的基底類別`inherit`關鍵字。 您必須提供引數以括號，基底類別建構函式。

您宣告欄位或函式所使用的本機類別的值`let`繫結，而且您必須遵循的一般規則`let`繫結。 `do-bindings`區段包含在物件建構時要執行的程式碼。

`member-list`其他建構函式、 執行個體和靜態方法宣告、 介面宣告，抽象的繫結，以及屬性和事件宣告所組成。 這些所述[成員](members/index.md)。

`identifier`搭配選擇性`as`關鍵字可讓執行個體變數或自我識別項，可用於型別定義中參考之型別的執行個體的名稱。 如需詳細資訊，請參閱本主題稍後的章節自我識別項。

關鍵字`class`和`end`，標記開始和結尾定義為選擇性。

相互遞迴類型，也就是彼此參考的類型，加入搭配`and`關鍵字，如同相互遞迴函式會。 如需範例，請參閱相互遞迴類型一節。

## <a name="constructors"></a>建構函式

建構函式是建立類別類型的執行個體的程式碼。 類別建構函式在 F # 中運作方式稍有不同，比在其他.NET 語言。 在 F # 類別中，總是有主要的建構函式的引數中所述`parameter-list`面的型別名稱，而其主體包含`let`(和`let rec`) 繫結的類別宣告，以及開頭`do`遵循的繫結。 主要的建構函式的引數會在整個類別宣告的範圍內。

您可以新增額外的建構函式使用`new`關鍵字來將成員，如下所示：

`new`(`argument-list`) = `constructor-body`

新的建構函式的主體必須叫用在類別宣告頂端指定的主要建構函式。

下列範例會說明這個概念。 下列程式碼，`MyClass`有兩個建構函式，接受兩個引數和其他建構函式的主要建構函式會採用任何引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>讓和 do 繫結

`let`和`do`類別定義中的繫結表單的主要類別建構函式主體，並因此執行時建立的類別執行個體。 如果`let`繫結函式，則它會編譯成一個成員。 如果`let`繫結是一個值，不會在任何函式或成員，則它會編譯成建構函式的本機變數。 否則，它會編譯到類別的欄位。 `do`遵循的運算式都會編譯成主要建構函式，並執行每個執行個體的初始化程式碼。 任何額外的建構函式一定要呼叫的主要建構函式，因為`let`繫結和`do`繫結一定會執行不論哪一個呼叫建構函式。

所建立的欄位`let`繫結可以存取整個方法和類別的屬性; 不過，它們無法存取的靜態方法，即使靜態方法會採用執行個體變數，做為參數。 無法存取使用自我識別項，如果有的話。

## <a name="self-identifiers"></a>自我識別項

A*自我識別項*是代表目前的執行個體的名稱。 自我識別項類似`this`C# 或 c + + 中的關鍵字或`Me`Visual Basic 中。 您可以在兩個不同的方式，取決於您是在範圍內的整個類別定義，或只是個別的方法本身的識別項定義自我識別項。

若要定義整個類別的自我識別項，請使用`as`關鍵字之後的左括號的建構函式參數清單，並指定識別項名稱。

若要定義本身的識別項，只有一個方法，提供在成員宣告中之前的方法名稱和句號 （.） 做為分隔符號, 的自我識別項。

下列程式碼範例說明兩種方式來建立自我識別項。 在第一行，`as`關鍵字用以定義自我識別項。 在第五個列中，識別項`this`用來定義本身的識別項，其範圍限於方法`PrintMessage`。

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

不同於其他.NET 語言，您可以命名自我識別項但您想要的選項;您不受限於名稱這類`self`， `Me`，或`this`。

自我識別項宣告`as`之前沒有初始化關鍵字之後`let`執行繫結。 因此，它不能在`let`繫結。 您可以使用中的自我識別項`do`繫結區段。

## <a name="generic-type-parameters"></a>泛型型別參數

角括號中指定泛型型別參數 (`<`和`>`)、 單引號後面接著識別項的形式。 以逗號分隔多個泛型型別參數。 泛型型別參數是在範圍中宣告。 下列程式碼範例示範如何指定泛型型別參數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

使用類型時，就會推斷類型引數。 在下列程式碼中，推斷的型別會是一系列 tuple。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>指定的繼承

`inherit`子句會識別直接基底類別中，如果有的話。 在 F # 中，允許只能有一個直接的基底類別。 類別實作的介面不會考慮基底類別。 介面會討論[介面](Interfaces.md)主題。

您可以從衍生類別存取的方法和屬性的基底類別，使用該語言關鍵字`base`做為識別項，後面接著句號 （.） 和成員的名稱。

如需詳細資訊，請參閱[繼承](inheritance.md)。

## <a name="members-section"></a>成員 區段

在本節中，您可以定義靜態或執行個體方法、 屬性、 介面實作，抽象成員、 事件宣告和其他建構函式。 可讓和執行繫結不能出現在這一節。 成員可以加入各種不同的 F # 型別除了類別之外，因為它們位於不同的主題，討論[成員](members/index.md)。

## <a name="mutually-recursive-types"></a>相互遞迴類型

當您定義的循環方式彼此參考的類型時，您串接在一起的類型定義使用`and`關鍵字。 `and`關鍵字取代`type`上以外，如下所示的第一個定義的所有關鍵字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

輸出是一份目前的目錄中的所有檔案。

## <a name="when-to-use-classes-unions-records-and-structures"></a>使用類別、 聯集、 記錄和結構的時機

提供的各種可從中選擇的類型，必須有充分的了解什麼每種類型專為以選取適當的型別為特定的情況。 類別專為在物件導向程式設計內容中。 物件導向程式設計是專為.NET Framework 撰寫的應用程式中使用的主要架構。 F # 程式碼是否與.NET Framework 或另一個物件導向程式庫密切合作，尤其是如果您的物件導向的型別系統，例如 UI 程式庫可以從擴充類別是可能適當。

如果您不緊密與物件導向程式碼互通，或如果您正在撰寫是各自獨立，因此防範頻繁互動以物件導向的程式碼的程式碼，您應該考慮使用記錄和差別聯集。 單一也想到 – 逾時已區分的聯集，以及適當的模式比對程式碼中，通常可用來當做物件階層架構較簡單的替代方案。 如需差別聯集的詳細資訊，請參閱[差別聯集](discriminated-unions.md)。

記錄都有的優點是比類別更簡單，但類型的需求超過功能可以使用它們簡便易行完成時，未適當的記錄。 記錄是基本上簡單的彙總的值，可以執行自訂動作的不同建構函式，不含隱藏的欄位，而不繼承或介面的實作。 雖然屬性和方法等成員可以加入，使其行為更複雜的記錄中，儲存在記錄的欄位仍是以簡單的彙總的值。 如需有關記錄的詳細資訊，請參閱 <<c0> [ 記錄](records.md)。

結構也適用於小型的彙總的資料，但它們不同於類別和記錄，因為它們是.NET 實值型別。 類別和記錄是.NET 參考型別。 由值傳遞實值型別，是不同的實值型別和參考型別語意。 這表示它們會複製做為參數傳遞或函式傳回時，位元的位元。 它們也儲存在堆疊上或者，如果做為欄位，內嵌於父物件，而不是儲存在他們自己在堆積上不同的位置。 因此，結構是適用於經常存取的資料，存取在堆積的額外負荷的記憶體問題時。 如需結構的詳細資訊，請參閱[結構](structures.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [成員](members/index.md)
- [繼承](inheritance.md)
- [介面](interfaces.md)
