---
title: Tuple
description: 瞭解F#元組, 這是一組未命名但已排序的值, 可能會有不同的類型。
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630234"
---
# <a name="tuples"></a>Tuple

*元組*是未命名但已排序值的群組, 可能會有不同的類型。  元組可以是參考型別或結構。

## <a name="syntax"></a>語法

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>備註

上述語法中的每個*元素*都可以是F#任何有效的運算式。

## <a name="examples"></a>範例

元組範例包括相同或不同類型的配對、三合一等等。 下列程式碼說明一些範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>取得個別值

您可以使用模式比對來存取和指派元組元素的名稱, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

您也可以透過系結, 透過`match` `let`運算式外部的模式比對來解構元組:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

或者, 您可以在元組上進行模式比對, 以作為函數的輸入:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

如果您只需要元組的一個元素, 則可以使用萬用字元 (底線) 來避免為不需要的值建立新名稱。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

將元素從參考元組複製到結構元組也很簡單:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

函數`fst` 和`snd` (僅限參考元組) 會分別傳回元組的第一個和第二個元素。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

沒有任何內建函數會傳回第三個元素, 但您可以輕鬆地撰寫一個, 如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般來說, 最好是使用模式比對來存取個別的元組元素。

## <a name="using-tuples"></a>使用元組

元組提供一個便利的方式, 可從函式傳回多個值, 如下列範例所示。 這個範例會執行整數除法, 並將運算的四捨五入結果當做元組配對的第一個成員, 並將餘數當做配對的第二個成員。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

當您想要避免使用一般函式語法所隱含之函式引數的隱含 currying 時, 元組也可以做為函數引數。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

定義函式的一般語法可`let sum a b = a + b`讓您定義函式, 該函式是函式第一個引數的部分應用, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

使用元組作為參數時, 會停用 currying。 如需詳細資訊, 請參閱[函數](./functions/index.md)中的「部分引數應用程式」。

## <a name="names-of-tuple-types"></a>元組類型的名稱

當您寫出屬於元組的型別名稱時, 您可以使用`*`符號來分隔元素。 若`int`為包含`float`、 `string`和的元組 (例如),則會以下列方式寫入類型。`(10, 10.0, "ten")`

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>與C#元組交互操作

C#7.0 引進了語言的元組。  中C#的元組是結構, 而且相當於中的F#結構元組。  如果您需要與C#相交互操作, 您必須使用結構元組。

這很容易執行。  例如, 假設您必須將元組傳遞給C#類別, 然後再取用其結果, 這也是一個元組:

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

在您F#的程式碼中, 您可以將結構元組當做參數傳遞, 並以結構元組的形式取用結果。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>在參考元組和結構元組之間轉換

因為參考元組和結構元組具有完全不同的基礎標記法, 所以它們無法隱含轉換。  也就是說, 下面這類程式碼不會進行編譯:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

您必須在一個元組上進行比對, 並使用組成的部分來建立另一個。  例如：

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>參考元組的已編譯形式

本節說明元組在編譯時的形式。  除非您的目標是 .NET Framework 3.5 或更低版本, 否則不需要閱讀這裡的資訊。

元組會編譯成數個泛型型別之一的物件, `System.Tuple`這些型別會在 arity 上多載, 或型別參數的數目。 當您從另一種語言 (例如C#或 Visual Basic) 或使用不知道結構的F#工具時, 元組類型會以此形式出現。 `Tuple`類型是在 .NET Framework 4 中引進。 如果您的目標是舊版的 .NET Framework, 編譯器會使用2.0 版F#核心程式庫的[system.object](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)版本。 此程式庫中的類型僅適用于以 .NET Framework 2.0、3.0 和3.5 版本為目標的應用程式。 類型轉送是用來確保 .NET Framework 2.0 和 .NET Framework 4 F#元件之間的二進位相容性。

### <a name="compiled-form-of-struct-tuples"></a>結構元組的已編譯形式

結構元組 (例如, `struct (x, y)`) 在本質上與參考元組不同。  它們會編譯成<xref:System.ValueTuple>型別、以 arity 進行多載, 或型別參數的數目。  它們相當於[ C# 7.0 元組](../../csharp/tuples.md)和[Visual Basic 2017 元組](../../visual-basic/programming-guide/language-features/data-types/tuples.md), 並可交互操作雙向。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
