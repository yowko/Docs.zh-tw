---
title: 參照儲存格 (F#)
description: '了解 F # 參考儲存格的儲存體位置，可讓您以參考語意建立可變值的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892413"
---
# <a name="reference-cells"></a>參考儲存格

*參考儲存格*是可讓您以參考語意建立可變值的儲存體位置。

## <a name="syntax"></a>語法

```fsharp
ref expression
```

## <a name="remarks"></a>備註

您可以在值的前面使用 `ref` 運算子，建立可封裝值的新參考儲存格。 由於基礎值是可變的，因此您接著可以變更這個基礎值。

參考儲存格不只是地址，還會保存實際值。 當您使用 `ref` 運算子建立參考儲存格時，會建立基礎值的複本做為已封裝的可變值。

您可以使用 `!` (驚嘆號) 運算子來取值 (Dereference) 參考儲存格。

下列程式碼範例將示範參考儲存格的宣告和用法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

輸出為 `50`。

參考儲存格為 `Ref` 泛型記錄型別的執行個體，其宣告如下。

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

`'a ref` 型別是 `Ref<'a>` 的同義字。 IDE 中的編譯器和 IntelliSense 會對此型別顯示前者，但基礎定義則為後者。

`ref` 運算子會建立新的參考儲存格。 下列程式碼為 `ref` 運算子的宣告。

```fsharp
let ref x = { contents = x }
```

下表顯示參考儲存格上的可用功能。

|運算子、成員或欄位|描述|類型|定義|
|--------------------------|-----------|----|----------|
|`!` (取值運算子)|傳回基礎值。|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (指派運算子)|變更基礎值。|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (運算子)|將值封裝至新的參考儲存格。|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (屬性)|取得或設定基礎值。|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (記錄欄位)|取得或設定基礎值。|`'a`|`let ref x = { contents = x }`|
有數個方式可以存取基礎值。 取值運算子 (`!`) 傳回的值不是可指派的值。 因此如果您要修改基礎值，則必須改用指派運算子 (`:=`)。

`Value` 屬性和 `contents` 欄位都是可指派的值。 因此，您可以使用它們來存取或變更基礎值，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

輸出如下。

```
10
10
11
12
```

`contents` 欄位是針對與其他 ML 版本相容而提供，而且會在編譯期間產生警告。 若要停用這個警告，請使用 `--mlcompatibility` 編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

下列程式碼將示範如何將參考儲存格用於參數傳遞。 增量器類型有一個方法使用參數來包含 byref 參數類型中的 Increment。 Byref 參數類型中的表示呼叫端，必須傳遞參考儲存格或指定型別的一般變數位址，在此案例的 int。其餘的程式碼示範如何使用這兩種類型的引數，呼叫遞增，並示範使用 ref 運算子建立參考儲存格 (ref myDelta1) 的變數上。 接著，程式碼會示範如何使用傳址運算子 (&amp;) 來產生適當引數。 最後，使用參考儲存格所使用的 let 繫結宣告時再次呼叫 Increment 方法。 最後一行程式碼示範如何使用 ！ 運算子來取值 （dereference） 參考儲存格供列印。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

如需如何以傳址方式傳遞的詳細資訊，請參閱[參數和引數](parameters-and-arguments.md)。

>[!NOTE]
C# 程式設計人員應該了解運作方式不同，該參考 F # 中不同於 C#。 比方說，使用 ref 時傳遞引數並沒有相同的效果在 F # 如同在 C# 中。

>[!NOTE]
`mutable` 變數可能會自動升級為`'a ref`如果擷取的 closure; 請參閱[值](values/index.md)。

## <a name="consuming-c-ref-returns"></a>使用 C#`ref`傳回

從 F # 4.1 開始，您可以使用`ref`傳回 C# 中產生。  這類呼叫的結果是`byref<_>`指標。

下列 C# 方法：

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

可以明確地呼叫 F # 使用任何特殊的語法：

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

您也可以宣告函式，這可能需要`ref`傳回做為輸入，例如：

```fsharp
let f (x: byref<int>) = &x
```

目前沒有任何方法來產生`ref`在 F # 中無法使用 C# 中傳回。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [參數和引數](parameters-and-arguments.md)
- [符號和運算子參考](symbol-and-operator-reference/index.md)
- [值](values/index.md)
