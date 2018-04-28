---
title: Tuple (F#)
description: '深入了解 F # tuple 的未命名，但已排序的值，可能是不同類型的群組。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9710f4996a952fdeaab07a30916215f27969e1a3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="tuples"></a>Tuple

A *tuple*是未命名，但已排序，可能是不同類型的值的群組。  Tuple 可以是參考型別或結構。

## <a name="syntax"></a>語法

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>備註
每個*元素*先前語法中可以是任何有效 F # 運算式。

## <a name="examples"></a>範例
Tuple 的範例包括組、 三合一，依此類推，相同或不同類型。 部分範例是以下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>取得個別的值
您可以使用模式比對來存取和指派名稱 tuple 項目，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

您也可以解構模式比對外部透過 tuple`match`透過運算式`let`繫結：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

或是您可以在模式比對的 tuple，做為函式的輸入：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

如果您需要只能有一個元素的 tuple，萬用字元 （底線） 可用來避免建立不需要值的新名稱。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

將參考 tuple 中的項目複製到結構 tuple 也很簡單：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

函式`fst`和`snd`（參考 tuple 只） 傳回第一個和第二個 tuple 的項目分別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

沒有內建函式，會傳回第三個元素的三倍，但您可以輕鬆地撰寫一個，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般而言，最好使用模式比對以存取個別的 tuple 項目。

## <a name="using-tuples"></a>使用 Tuple
Tuple 提供便利的方式從函式，傳回多個值，如下列範例所示。 此範例會執行整數除法運算，並傳回 tuple 配對的第一個成員作業，並為第二個配對成員的其餘部分的進位的結果。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Tuple 也使用做為函式引數，當您想要避免隱含對一般函式語法所隱含的函式引數。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

定義函式的一般語法`let sum a b = a + b`可讓您定義部分的應用程式的函式，第一個引數的函式，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

使用 tuple 做為參數會停用對。 如需詳細資訊，請參閱 「 部分應用程式的引數 」 中[函式](functions/index.md)。

## <a name="names-of-tuple-types"></a>Tuple 類型的名稱
當您撰寫的是 tuple 的類型名稱時，您會使用`*`符號來分隔項目。 包含 tuple `int`、 `float`，和`string`，例如`(10, 10.0, "ten")`，型別會被寫入，如下所示。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>與 C# Tuple 的互通

C# 7.0 引進 tuple 的語言。  在 C# 中的 Tuple 結構，而且相當於在 F # 中的結構 tuple。  如果您需要使用 C# 交互操作，您必須使用結構 tuple。

這是容易的。  例如，假設您必須將 tuple 傳遞至 C# 類別，並使用它的結果，也是 tuple:

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

在您 F # 程式碼，您可以再傳遞結構 tuple 做為參數，並使用結構 tuple 形式的結果。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>參考的 Tuple 與結構間的轉換

參考的 Tuple 與結構已經完全不同的基礎表示法，因為它們都無法隱含地轉換。  亦即，不會編譯程式碼如下所示：

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

您必須在模式比對一個 tuple 和構成組件的其他建構。  例如: 

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>參考 Tuple 的編譯的形式
本章節將說明它們在編譯時的 tuple 形式。  這裡的資訊不需要讀取，除非您的目標.NET Framework 3.5 或更低。

Tuple 會編譯為物件的其中一種數個泛型類型，所有具名`System.Tuple`，引數數目，則型別參數數目上的多載。 當您從另一種語言，例如 C# 或 Visual Basic 中，檢視時，或當您使用一種工具，並不知道 F # 建構 Tuple 類型就會出現在這種形式。 `Tuple` .NET Framework 4 中導入型別。 如果您的目標舊版的.NET Framework，編譯器會使用新版[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)從 F # 核心程式庫 2.0 版。 此文件庫中的類型只能用於以 2.0、 3.0 和 3.5 版本的.NET Framework 為目標的應用程式。 類型轉送用來確保.NET Framework 2.0 和.NET Framework 4 F # 元件之間的二進位碼相容性。

### <a name="compiled-form-of-struct-tuples"></a>編譯的結構 Tuple 形式

Tuple 結構 (例如， `struct (x, y)`)，基本上不同於參考 tuple。  編譯成<xref:System.ValueTuple>型別引數數目或型別參數數目所多載。  它們是相當於[C# 7.0 Tuple](../../csharp/tuples.md)和[Visual Basic 2017 Tuple](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，以及雙向交互操作。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[F# 類型](fsharp-types.md)
