---
title: 泛型 (F#)
description: '了解如何使用 F # 泛型函式和類型，可讓您撰寫搭配各種類型，而不需要重複程式碼的程式碼。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0e5c7ad59f0e4d278f478e9fd8e6da70a13aba02
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="generics"></a>泛型

F# 函式值、方法、屬性和彙總類型 (例如類別、記錄和差別聯集) 都可以是「泛型」。 泛型建構至少包含一個類型參數，此參數通常是由泛型建構的使用者所提供。 泛型函式和類型可讓您撰寫適用於各種類型的程式碼，而不需對每一種類型重複輸入程式碼。 由於編譯器的型別推斷和自動一般化機制通常會將程式碼隱含推斷為泛型，所以要讓程式碼在 F# 中成為泛型很簡單。


## <a name="syntax"></a>語法

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>備註
在函式或類型名稱之後的角括弧中，明確泛型函式或類型的宣告非常類似於非泛型函式或類型的宣告，但類型參數的規格 (和使用方式) 除外。

宣告通常為隱含泛型。 若您並未完全指定每一個用於組成函式或類型之參數的類型，則編譯器會嘗試根據您撰寫的程式碼來推斷每一個參數、值和變數的類型。 如需詳細資訊，請參閱[型別推斷](../type-inference.md)。 若類型或函式的程式碼並未限制參數的類型，則函式或類型即為隱含泛型。 此程序稱為「自動一般化」。 自動一般化有一些限制。 例如，若 F# 編譯器無法推斷泛型建構的類型，則該編譯器所回報的錯誤會參考一種稱為「值限制」的限制。 在此情況下，您可能必須新增一些類型註解。 如需自動一般化和值限制的詳細資訊，以及如何變更程式碼來解決問題的詳細資訊，請參閱[自動產生](automatic-generalization.md)。

在先前的語法中，*type-parameters* 是一份代表未知類型的參數清單 (以逗號分隔)，而每一個參數都是以單引號開頭，並選擇性加入條件約束子句，以進一步限制哪些類型可用於該類型參數。 如需各種條件約束子句的語法以及條件約束的其他資訊，請參閱[條件約束](constraints.md)。

語法中的 *type-definition* 與非泛型型別的類型定義相同。 這包含類別類型的建構函式參數、選擇性 `as` 子句、等號、記錄欄位、`inherit` 子句、差別聯集的選項、`let` 和 `do` 繫結、成員定義，以及非泛型型別定義中允許的任何其他項目。

其他語法項目與非泛型函式和類型的語法項目相同。 例如，*object-identifier* 是一個代表包含物件本身的識別項。

屬性、欄位和建構函式不能比封入類型更加泛型。 此外，模組中的值不可以為泛型。


## <a name="implicitly-generic-constructs"></a>隱含泛型建構
當 F# 編譯器推斷程式碼中的類型時，它會自動將任何可以成為泛型的函式自動視為泛型。 若您明確指定類型 (例如參數類型)，則會防止自動一般化。

在下列程式碼範例中，`makeList` 是泛型的，即使它或它的參數皆未明確地宣告為泛型。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

此函式的簽章被推斷為 `'a -> 'a -> 'a list`。 請注意，這個範例中的 `a` 和 `b` 被推斷為具有相同的類型。 這是因為它們一起包含在清單中，而且清單的所有項目都必須是相同的類型。

您也可以在類型註解中使用單引號語法，表示參數類型是泛型型別參數，而讓函式成為泛型。 在下列程式碼中，`function1` 為泛型，因為它的參數已用這種方式宣告為類型參數。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a>明確泛型建構
以角括弧 (`<type-parameter>`) 明確宣告函式的類型參數，也可以讓函式變成泛型函式。 以下的程式碼可說明這點。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a>使用泛型建構
當您使用泛型函式或方法時，您不一定要指定類型引數。 編譯器會使用型別推斷來推斷適當的類型引數。 若仍然模稜兩可，您可以在角括弧中提供類型引數，並以逗號分隔多個類型引數。

下列程式碼顯示如何使用先前章節中定義的函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
依照名稱參考泛型型別的方法有兩種。 例如，`list<int>` 和 `int list` 就是兩種用於參考具有單一類型引數 `int` 之泛型型別 `list` 的方法。 後面的形式照慣例僅適用於內建的 F# 類型，例如 `list` 和 `option`。 若有多個類型引數，您通常會使用語法 `Dictionary<int, string>`，但是也可以使用語法 `(int, string) Dictionary`。

## <a name="wildcards-as-type-arguments"></a>使用萬用字元作為類型引數
若要指定應該由編譯器推斷的類型引數，您可以使用底線或萬用字元符號 (`_`)，而非使用具名的類型引數。 如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a>泛型型別和函式的條件約束
在泛型型別或函式定義中，您只能使用已知可用於泛型型別參數的建構。 如此一來，才能在編譯階段啟用函式和方法呼叫的驗證。 若您明確宣告類型參數，則可以將明確條件約束套用至泛型型別參數，以通知編譯器可以使用某些方法和函式。 不過，若您允許 F# 編譯器推斷您的泛型參數類型，則它會為您判斷適當的條件約束。 如需詳細資訊，請參閱[條件約束](constraints.md)。


## <a name="statically-resolved-type-parameters"></a>以統計方式解析的型別參數
F# 程式中可以使用的類型參數有兩種。 第一種是前幾節中所描述的該類泛型型別參數。 這一種類型參數等同於在 Visual Basic 和 C# 等語言中使用的泛型型別參數。 另一種類型參數則專屬於 F#，稱為「以統計方式解析的類型參數」。 如需這類建構的資訊，請參閱[以統計方式解析的類型參數](statically-resolved-type-parameters.md)。


## <a name="examples"></a>範例
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a>另請參閱
[語言參考](../index.md)

[型別](../fsharp-types.md)

[以統計方式解析的類型參數](statically-resolved-type-parameters.md)

[.NET Framework 中的泛型](~/docs/standard/generics/index.md)

[自動一般化](automatic-generalization.md)

[條件約束](constraints.md)
