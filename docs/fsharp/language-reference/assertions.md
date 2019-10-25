---
title: 判斷提示
description: 瞭解如何使用「判斷提示」運算式做為程式F#設計語言中測試運算式的偵錯工具。
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799069"
---
# <a name="assertions"></a>判斷提示

`assert` 運算式是一個可供您用來測試運算式的偵錯工具。 當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。

## <a name="syntax"></a>語法

```fsharp
assert condition
```

## <a name="remarks"></a>備註

`assert` 運算式的類型 `bool -> unit`。

`assert` 函式會解析為 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。 這表示其行為等同于直接呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。

只有當您在 Debug 模式下編譯時，才會啟用判斷提示檢查;也就是，如果已定義常數 `DEBUG`。 在專案系統中，預設會在 [偵錯工具] 設定中定義 `DEBUG` 常數，而不是在 [發行] 設定中。

無法使用F#例外狀況處理來攔截判斷提示失敗錯誤。

## <a name="example"></a>範例

下列程式碼範例說明如何使用 `assert` 運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>請參閱

- [F# 語言參考](index.md)
