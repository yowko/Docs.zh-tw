---
title: Tuple
description: '深入瞭解 F # 元組，這是一個未命名但排序值的群組，可能是不同的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 6f4adf7e10e22d8b7a8cf697baee15962adf3630
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720357"
---
# <a name="tuples"></a>Tuple

*元組*是未命名但排序值的群組，可能是不同的類型。  元組可以是參考型別或結構。

## <a name="syntax"></a>語法

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>備註

上述語法中的每個 *元素* 都可以是任何有效的 F # 運算式。

## <a name="examples"></a>範例

元組的範例包括相同或不同類型的配對、三合一等等。 下列程式碼說明一些範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>取得個別值

您可以使用模式比對來存取和指派元組元素的名稱，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

您也可以透過系結，透過運算式外部的模式比對來解構元組 `match`  `let` ：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

或者，您可以對元組進行模式比對，作為函式的輸入：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

如果您只需要一個元組的元素，則可以使用 (底線) 的萬用字元，以避免為不需要的值建立新的名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

從參考元組將元素複製到結構元組也很簡單：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

`fst` `snd` 只有) 傳回元組的第一個和第二個元素時，才會有函數和 (參考元組。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

沒有可傳回三個三個元素的內建函數，但您可以輕鬆地撰寫一個，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般而言，最好使用模式比對來存取個別的元組元素。

## <a name="using-tuples"></a>使用元組

元組提供一個便利的方式，從函式傳回多個值，如下列範例所示。 此範例會執行整數除法運算，並將作業的舍入結果傳回為元組配對的第一個成員，並傳回餘數做為配對的第二個成員。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

當您想要避免一般函數語法所隱含的函式引數隱含 currying 時，元組也可以當做函式引數使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

定義函式的一般語法可 `let sum a b = a + b` 讓您定義函式，該函式是函式之第一個引數的部分應用，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

使用元組作為參數會停用 currying。 如需詳細資訊，請參閱函 [式中的](./functions/index.md)「部分引數應用程式」。

## <a name="names-of-tuple-types"></a>元組類型的名稱

當您寫出屬於元組的型別名稱時，會使用 `*` 符號來分隔專案。 若為包含 `int` 、和的元組（ `float` `string` 例如 `(10, 10.0, "ten")` ），則會以下列方式寫入類型。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>與 c # 元組交互操作

C # 7.0 引進了元組至語言。  C # 中的元組是結構，相當於 F # 中的結構元組。  如果您需要與 c # 交互操作，您必須使用結構元組。

這麼做很簡單。  例如，假設您必須將元組傳遞給 c # 類別，然後使用它的結果，也就是元組：

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

在您的 F # 程式碼中，您可以傳遞結構元組作為參數，並將結果作為結構元組使用。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>在參考元組和結構元組之間轉換

由於參考元組和結構元組具有完全不同的基礎標記法，因此它們無法隱含轉換。  也就是說，如下所示的程式碼將不會編譯：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

您必須在一個元組上進行模式比對，並使用組成零件來建立另一個。  例如：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>參考元組的編譯形式

本節說明編譯元組的形式。  除非您的目標是 .NET Framework 3.5 或更低版本，否則不需要讀取此處的資訊。

元組會編譯成數個泛型型別之一的物件，這些泛型型別全都命名為 arity 上的多載， `System.Tuple` 或類型參數的數目。 當您從另一種語言（例如 c # 或 Visual Basic，或使用不知道 F # 結構的工具）來查看元組類型時，元組類型會以此形式出現。 這些 `Tuple` 類型是在 .NET Framework 4 中引進。 如果您的目標是舊版 .NET Framework，編譯器會使用 `System.Tuple` 來自2.0 版 F # 核心程式庫的版本。 此程式庫中的類型僅適用于以 .NET Framework 2.0、3.0 和3.5 版本為目標的應用程式。 類型轉送是用來確保 .NET Framework 2.0 和 .NET Framework 4 F # 元件之間的二進位相容性。

### <a name="compiled-form-of-struct-tuples"></a>結構元組的編譯形式

結構元組 (例如 `struct (x, y)`) ，基本上與參考元組不同。  它們會編譯成 <xref:System.ValueTuple> 類型、以 arity 來多載，或是類型參數的數目。  它們相當於 [c # 7.0 元組](../../csharp/language-reference/builtin-types/value-tuples.md) 和 [Visual Basic 2017 元組](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，而且可交互操作雙向。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [F# 類型](fsharp-types.md)
