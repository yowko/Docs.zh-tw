---
title: 類別中的 do 繫結 (F#)
description: "了解如何使用 F # 'do' 繫結，在類別定義中，這會執行動作，當物件的建構或第一次使用的型別。"
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565187"
---
# <a name="do-bindings-in-classes"></a>類別中的 do 繫結

A`do`繫結的類別定義中執行的動作，當物件的建構或時，靜態`do`繫結，當第一次使用類型。


## <a name="syntax"></a>語法

```fsharp
[static] do expression
```

## <a name="remarks"></a>備註
A`do`搭配或之後，會顯示繫結`let`繫結的類別定義中的成員定義之前。 雖然`do`關鍵字是選擇性的`do`繫結在模組層級，它不是選擇性的`do`類別定義中的繫結。

針對每個物件的任何建構指定的型別，而非靜態`do`繫結和非靜態`let`繫結以它們出現在類別定義中的順序執行。 多個`do`繫結可能會發生一個類型中。 非靜態`let`繫結和非靜態`do`繫結會變成主要建構函式的主體。 在非靜態程式碼`do`主要建構函式參數和值或定義中的函式，可以參考繫結區段`let`繫結區段。

非靜態`do`繫結可存取類別的成員，只要類別有本身的識別項所定義`as`行標頭，，只要所有使用這些成員以類別自我識別項都限定的類別中的關鍵字。

因為`let`繫結初始化私用欄位的類別，這個方法通常需要保證成員會如預期運作，`do`繫結通常會放在之後`let`繫結中的程式碼讓`do`繫結可以執行與完整初始化的物件。 如果您的程式碼嘗試使用成員初始設定完成之前，會引發 InvalidOperationException。

靜態`do`繫結可以參考靜態成員或欄位封入類別，但不是執行個體成員或欄位。 靜態`do`繫結會成為類別，可保證執行之前先使用的類別的靜態初始設定式的一部分。

屬性會被忽略`do`類型中的繫結。 屬性是否需要執行的程式碼`do`繫結時，它必須套用至主要建構函式。

下列程式碼中，類別還具有靜態`do`繫結和非靜態`do`繫結。 物件具有兩個參數的建構函式`a`和`b`，且兩個私用欄位定義於`let`繫結的類別。 也會定義兩個屬性。 所有這些都是在非靜態範圍中`do`繫結區段中，會列印所有這些值的行中所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

輸出如下。

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>另請參閱
[成員](index.md)

[類別](../classes.md)

[建構函式](constructors.md)

[類別中的 `let` 繫結](let-bindings-in-classes.md)

[`do` 繫結](../functions/do-Bindings.md)
