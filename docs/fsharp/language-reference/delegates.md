---
title: 委派 (F#)
description: '了解如何使用 F # 中的委派。'
ms.date: 05/16/2016
ms.openlocfilehash: 664b4f80302871d05ea9604ca90219e19bc14ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="delegates"></a>委派

委派以物件表示函式呼叫。 在 F # 中，您通常應該使用函式值來表示函式做為第一級值;不過，委派會使用.NET Framework 中，而且當您希望他們的應用程式開發介面與交互操作時，因此需要。 此外，它們也可能使用時撰寫的程式庫針對使用其他.NET Framework 語言。


## <a name="syntax"></a>語法

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>備註
在先前的語法，`type1`表示的引數類型和`type2`表示的傳回型別。 引數型別以表示`type1`自動局部調用。 這可能表示，此類型局部調用目標函式的引數，如果您使用了 tuple 表單和括號括住 tuple 已 tuple 形式的引數。 自動對移除一組括號，讓符合目標方法的 tuple 引數。 請參閱程式碼範例，您應該在每個案例中使用的語法。

委派可以附加至 F # 函式值，與靜態或執行個體方法。 F # 函式值可以直接做為委派建構函式引數傳遞。 對於靜態方法，您可以建構委派使用類別和方法的名稱。 執行個體方法，為您提供的物件執行個體和一個引數中的方法。 在這兩種情況下，成員存取運算子 (`.`) 使用。

`Invoke`委派型別上的方法會呼叫封裝函式。 此外，委派可以藉由參考沒有括號叫用方法名稱傳遞做為函式值。

下列程式碼顯示的語法建立代表類別中的各種方法的委派。 根據是否方法為靜態方法或執行個體方法，以及是否有 tuple 或局部調用的表單中的引數，宣告並指派委派的語法會稍有不同。

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
[F# 語言參考](index.md)

[參數和引數](parameters-and-arguments.md)

[事件](members/events.md)
