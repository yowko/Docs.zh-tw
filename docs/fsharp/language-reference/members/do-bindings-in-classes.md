---
title: 類別中的 do 繫結
description: 了解如何使用F#'do' 在類別定義中，這會執行動作，或第一次使用的型別時，物件建構的繫結。
ms.date: 05/16/2016
ms.openlocfilehash: c924c882974989436d8ea404ebee0a7ef3c54fd3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641787"
---
# <a name="do-bindings-in-classes"></a>類別中的 do 繫結

A`do`在類別定義的繫結會執行動作的物件建構時或者，若為靜態`do`繫結，當第一次使用類型。

## <a name="syntax"></a>語法

```fsharp
[static] do expression
```

## <a name="remarks"></a>備註

A`do`搭配使用，或是之後，就會出現繫結`let`繫結類別定義中的成員定義之前。 雖然`do`是選擇性的關鍵字`do`繫結在模組層級中，它不是選擇性的`do`類別定義中的繫結。

針對每個物件的任何建構指定的型別，而非靜態`do`繫結和非靜態`let`繫結以其出現在類別定義的順序執行。 多個`do`繫結可能會發生在一種類型。 非靜態`let`繫結和非靜態`do`繫結會變成主要建構函式的主體。 在非靜態程式碼`do`主要建構函式參數的任何值或函式中所定義的可以參考繫結區段`let`繫結區段。

非靜態`do`繫結可以存取類別的成員，只要類別具有本身的識別項所定義`as`標題，並只要所有使用這些成員的類別的自我識別項都限定的類別中的關鍵字。

因為`let`繫結初始化的類別，也就是通常需要保證成員會在如預期般運作，私用欄位`do`繫結通常會放在後`let`繫結中的程式碼以便`do`繫結可以執行與完整初始化的物件。 如果您的程式碼嘗試使用成員初始設定完成之前，會引發 InvalidOperationException。

靜態`do`繫結可以參考靜態成員或欄位的封入類別，但不是執行個體成員或欄位。 靜態`do`繫結會成為類別，會執行之前先使用此類別的靜態初始設定式的一部分。

屬性會忽略`do`類型中的繫結。 如果屬性是的執行中的程式碼需要`do`繫結，它必須套用至主要建構函式。

下列程式碼中，類別所擁有的靜態`do`繫結和非靜態`do`繫結。 物件具有兩個參數的建構函式`a`並`b`，且兩個私用欄位已定義在`let`類別的繫結。 此外，也會定義兩個屬性。 這些都在範圍內非靜態`do`繫結區段，如線條會列印所有這些值的說明。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

輸出如下。

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [類別](../classes.md)
- [建構函式](constructors.md)
- [類別中的 `let` 繫結](let-bindings-in-classes.md)
- [`do` Bindings](../functions/do-Bindings.md)
