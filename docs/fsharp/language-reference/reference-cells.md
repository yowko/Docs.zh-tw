---
title: 參考儲存格
description: 瞭解參考F#儲存格如何為儲存位置, 讓您使用參考語義建立可變值。
ms.date: 05/16/2016
ms.openlocfilehash: faaa4a6b54ff0366163b6821edff7fa4cb2f5a88
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627245"
---
# <a name="reference-cells"></a>參考儲存格

*參考儲存格*是儲存位置, 可讓您使用參考語義建立可變值。

## <a name="syntax"></a>語法

```fsharp
ref expression
```

## <a name="remarks"></a>備註

您可以在值的前面使用 `ref` 運算子，建立可封裝值的新參考儲存格。 由於基礎值是可變的，因此您接著可以變更這個基礎值。

參考儲存格不只是地址，還會保存實際值。 當您使用 `ref` 運算子建立參考儲存格時，會建立基礎值的複本做為已封裝的可變值。

您可以使用 `!` (驚嘆號) 運算子來取值 (Dereference) 參考儲存格。

下列程式碼範例將示範參考儲存格的宣告和用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

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
|`ref`操作|將值封裝至新的參考儲存格。|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value`property|取得或設定基礎值。|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (記錄欄位)|取得或設定基礎值。|`'a`|`let ref x = { contents = x }`|

有數個方式可以存取基礎值。 取值運算子 (`!`) 傳回的值不是可指派的值。 因此如果您要修改基礎值，則必須改用指派運算子 (`:=`)。

`Value` 屬性和 `contents` 欄位都是可指派的值。 因此，您可以使用它們來存取或變更基礎值，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

輸出如下。

```
10
10
11
12
```

`contents` 欄位是針對與其他 ML 版本相容而提供，而且會在編譯期間產生警告。 若要停用這個警告，請使用 `--mlcompatibility` 編譯器選項。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

C#程式設計人員應該`ref`知道C#在中的不是相同`ref`的F#東西。 中F#的對等結構是[byref](byrefs.md), 這是與參考儲存格不同的概念。

如果已關閉`mutable`, 則標示為的`'a ref`值可能會自動升級為, 請參閱[values](./values/index.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [參數和引數](parameters-and-arguments.md)
- [符號和運算子參考](./symbol-and-operator-reference/index.md)
- [值](./values/index.md)
