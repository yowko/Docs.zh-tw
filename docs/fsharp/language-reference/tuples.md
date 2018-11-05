---
title: Tuple (F#)
description: 深入了解 F# tuple 的群組不具名但有已排序，可能是不同類型的值。
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43749219"
---
# <a name="tuples"></a>Tuple

A *tuple*是群組不具名但有已排序，可能是不同類型的值。  Tuple 可以是參考型別或結構。

## <a name="syntax"></a>語法

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>備註

每個*項目*在先前的語法可以是任何有效 F# 運算式。

## <a name="examples"></a>範例

Tuple 的範例包括組、 三合一、 等等的相同或不同的型別。 一些範例是以下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>取得個別值

您可以使用模式比對來存取和指派名稱的元組元素，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

您也可以解構 tuple，以透過模式比對的外部`match`透過運算式`let`繫結：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

或是您可以在模式比對 tuple 中，做為函式的輸入：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

如果您需要的只有一個元素的元組，萬用字元 （底線） 可用來避免建立新的名稱，您不需要的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

將參考 tuple 中的項目複製到的結構元組也很簡單：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

函式`fst`和`snd`（參考 tuple 只） 傳回第一個和第二個元素的元組，分別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

沒有內建函式會傳回三重物件，第三個元素，但您可以輕鬆地撰寫，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般而言，最好使用模式比對來存取個別的 tuple 項目。

## <a name="using-tuples"></a>使用 Tuple

下列範例所示，Tuple 會提供便利的方式，從函式，傳回多個值。 此範例會執行整數除法運算，並傳回為元組配對的第一個成員作業，並為第二個配對成員的其餘部分的進位的結果。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Tuple 也使用函式引數，當您想要避免隱含對一般函式語法所默許的函式引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

定義函式的一般語法`let sum a b = a + b`可讓您定義部分的應用程式，第一個引數的函式的函式，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

使用 tuple 的參數會停用對。 如需詳細資訊，請參閱 「 部分應用程式的引數 」 中[函式](functions/index.md)。

## <a name="names-of-tuple-types"></a>元組類型的名稱

當您撰寫出的是 tuple 型別名稱時，您會使用`*`符號來分隔元素。 所組成的 tuple `int`，則`float`，和`string`，例如`(10, 10.0, "ten")`，型別會被寫入，如下所示。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>使用 C# Tuple 的互通性

C# 7.0 引進 tuple 的語言。  Tuple 在 C# 中為結構，並相當於在 F# 中的結構元組。  如果您需要使用 C# 交互操作，您必須使用結構元組。

這很簡單。  例如，假設您必須將 tuple 傳遞至 C# 類別，然後取用它的結果，這也是 tuple:

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

在 F# 程式碼，您可以再做為參數傳遞的結構元組，並使用結構 tuple 形式的結果。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>參考 Tuple 及結構元組間的轉換

因為參考 Tuple 和結構元組有完全不同的基礎表示法，所以它們不會隱含地轉換。  也就是說，如下所示的程式碼無法編譯：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

您必須在模式比對一的 tuple，並建構的組成組件與其他。  例如: 

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>已編譯的形式的參考 Tuple

本章節將說明 tuple 的形式時編譯。  此處提供的資訊不需要讀取，除非您的目標.NET Framework 3.5 或更低。

Tuple 會編譯成其中一種數個泛型類型，所有具名物件`System.Tuple`的多載上的引數數目或類型參數的數目。 當您從另一種語言，例如 C# 或 Visual Basic 中，檢視時，或當您使用一種工具，並不知道 F# 建構，元組類型會出現在這種形式。 `Tuple` .NET Framework 4 中導入類型。 如果您的目標是舊版的.NET Framework，編譯器會使用新版[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)從 F# 核心程式庫 2.0 版。 此文件庫中的類型僅用於在 2.0、 3.0 和 3.5 版本的.NET framework 為目標的應用程式。 類型轉送用來確保.NET Framework 2.0 和.NET Framework 4 F# 元件之間的二進位相容性。

### <a name="compiled-form-of-struct-tuples"></a>已編譯的結構元組的形式

結構元組 (比方說， `struct (x, y)`)，是本質上不同於參考 tuple。  還是會編譯至<xref:System.ValueTuple>型別，多載引數數目或類型參數的數目。  它們是相當於[C# 7.0 Tuple](../../csharp/tuples.md)並[Visual Basic 2017 Tuple](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，以及交互操作雙向。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
