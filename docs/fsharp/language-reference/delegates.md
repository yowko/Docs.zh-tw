---
title: 委派
description: 瞭解如何在中F#使用委派。
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630364"
---
# <a name="delegates"></a>委派

委派代表當做物件的函式呼叫。 在F#中, 您通常應該使用函式值來將函式表示為第一類的值;不過, 委派會在 .NET Framework 中使用, 因此當您與預期它們的 Api 互通時, 需要用到。 撰寫專供其他 .NET Framework 語言使用的程式庫時, 也可能會使用它們。

## <a name="syntax"></a>語法

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>備註

在先前的語法中`type1` , 代表引數類型或類型`type2` , 而表示傳回類型。 所表示`type1`的引數類型會自動進行擴充。 這表示針對此類型, 如果目標函式的引數是已擴充的, 而且已經在元組表單中的引數有括弧的元組, 您就可以使用元組表單。 自動 currying 會移除一組括弧, 並保留符合目標方法的元組引數。 請參閱程式碼範例, 以瞭解您在每個案例中應該使用的語法。

委派可以附加至F#函數值, 以及靜態或實例方法。 F#函數值可以直接當做引數傳遞至委派的函式。 若為靜態方法, 您可以使用類別的名稱和方法來建立委派。 若為實例方法, 您可以在一個引數中提供物件實例和方法。 在這兩種情況下, 都會使用`.`成員存取運算子 ()。

委派`Invoke`類型上的方法會呼叫封裝的函式。 此外, 委派可以藉由參考不含括弧的叫用方法名稱, 以函式值的方式傳遞。

下列程式碼顯示用來建立委派的語法, 代表類別中的各種方法。 根據該方法是靜態方法或實例方法, 以及它在元組形式或擴充形式中是否有引數, 宣告和指派委派的語法稍有不同。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

下列程式碼顯示一些您可以使用委派的不同方式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

先前程式碼範例的輸出如下所示。

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [參數和引數](parameters-and-arguments.md)
- [事件](./members/events.md)
