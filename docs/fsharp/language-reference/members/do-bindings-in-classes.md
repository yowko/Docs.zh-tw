---
title: 類別中的 do 繫結
description: 瞭解如何在類別定義F#中使用「do」系結, 此系結會在物件建立時或第一次使用型別時, 執行動作。
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627584"
---
# <a name="do-bindings-in-classes"></a>類別中的 do 繫結

類別定義中的系結會在物件建立時執行動作, 或在第一`do`次使用該類型時, 針對靜態系結。 `do`

## <a name="syntax"></a>語法

```fsharp
[static] do expression
```

## <a name="remarks"></a>備註

系結會與系結一起`let`出現, 但在類別定義中的成員定義之前。 `do` 雖然關鍵字對於`do`模組層級的系結是選擇性的, 但對於`do`類別定義中的系結而言, 並不是選擇性的。 `do`

針對任何給定類型的每個物件的結構, 非靜態`do`系結和非靜態`let`系結會依照它們出現在類別定義中的順序來執行。 一個`do`類型中可能會發生多個系結。 非靜態`let`系結和非靜態`do`系結會成為主要函式的主體。 [非靜態`do`系結] 區段中的程式碼可以參考主要的函式參數, 以及系結區段`let`中所定義的任何值或函數。

只要類別具有`do`類別標題中`as`關鍵字所定義的自我識別碼, 而且這些成員的所有用法都是以類別的自我識別碼限定, 非靜態系結就可以存取類別的成員。

由於`let`系結會初始化類別的私用欄位, 因此通常必須確保成員如預期般運作, 而且`do`系結通常會在`let`系結之後放置, 讓`do`系結中的程式碼可以使用完全初始化的物件來執行。 如果您的程式碼在初始化完成之前嘗試使用成員, 則會引發 InvalidOperationException。

靜態`do`系結可以參考封閉式類別的靜態成員或欄位, 但不能參考實例成員或欄位。 靜態`do`系結會成為類別靜態初始化運算式的一部分, 保證會在第一次使用類別之前執行。

類型中的`do`系結會忽略屬性。 如果在系結中`do`執行的程式碼需要屬性, 則必須將它套用至主要的函式。

在下列程式碼中, 類別具有靜態`do`系結和非靜態`do`系結。 物件有一個具有兩個參數 ( `a`和`b`) 的函式, 以及兩個私用欄位`let`定義于類別的系結中。 也會定義兩個屬性。 這些全都位於 [非靜態`do`系結] 區段的 [範圍] 中, 如列印所有這些值的程式程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

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
- [`do`關係](../functions/do-Bindings.md)
