---
title: 委派
description: 了解如何在使用中的委派F#。
ms.date: 05/16/2016
ms.openlocfilehash: 772685488b7caef92123979d817929c631248afb
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612890"
---
# <a name="delegates"></a>委派

委派為物件，表示函式呼叫。 在F#，您通常應該使用函式值來表示函式做為第一級值;不過，委派會在.NET Framework 和您預期的 Api 與交互操作時，因此需要。 此外，它們也可能使用專為撰寫的程式庫會使用從其他.NET Framework 語言時。

## <a name="syntax"></a>語法

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>備註

在先前的語法`type1`表示的引數型別或型別和`type2`表示傳回型別。 引數類型表示的`type1`自動局部調用。 這可能表示，您會使用 tuple 形式，如果目標函式的引數局部調用，此類型與已在 tuple 形式的引數的括號括住 tuple。 自動調用移除一組括號，保留的元組引數，符合目標方法。 請參閱每個案例中，您應該使用的語法的程式碼範例。

委派可以附加至F#函式值，以及靜態或執行個體方法。 F#函式值可以直接當做委派建構函式的引數傳遞。 是靜態的方法中，您可以建構委派使用類別和方法的名稱。 執行個體方法，為您提供的物件執行個體和一個引數中的方法。 在這兩種情況下，成員存取運算子 (`.`) 使用。

`Invoke`的委派類型的方法呼叫的封裝函式。 此外，委派可以藉由參考沒有括號的 Invoke 方法名稱傳遞為函式值。

下列程式碼顯示建立代表類別中的各種方法的委派的語法。 根據是否方法為靜態方法或執行個體方法，以及是否有 tuple 或局部調用的表單中的引數，宣告和指派委派的語法是有點不同。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

下列程式碼顯示一些不同的方式，您可以使用委派。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

上述程式碼範例的輸出如下所示。

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [參數和引數](parameters-and-arguments.md)
- [事件](members/events.md)