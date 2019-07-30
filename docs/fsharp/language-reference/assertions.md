---
title: 判斷提示
description: 瞭解如何使用「判斷提示」運算式做為程式F#設計語言中測試運算式的偵錯工具。
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630032"
---
# <a name="assertions"></a>判斷提示

`assert`運算式是一種可供您用來測試運算式的偵錯工具。 當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。

## <a name="syntax"></a>語法

```fsharp
assert condition
```

## <a name="remarks"></a>備註

運算式`assert`的類型`bool -> unit`為。

在先前的語法中,*條件*代表要測試的布林運算式。 如果運算式評估為`true`, 則執行會繼續受到影響。 如果評估為`false`, 就會產生 [系統錯誤] 對話方塊。 錯誤對話方塊具有包含字串判斷提示**失敗**的標題。 此對話方塊包含一個堆疊追蹤, 指出判斷提示失敗的位置。

只有當您在 Debug 模式下編譯時, 才會啟用判斷提示檢查;也就是說, 如果已定義常數`DEBUG` , 則為。 根據預設, 專案系統中的`DEBUG`常數是在 Debug 設定中定義, 而不是在發行設定中定義。

無法使用F#例外狀況處理來攔截判斷提示失敗錯誤。

> [!NOTE]
> 函式會將<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>解析為。 `assert`

## <a name="example"></a>範例

下列程式碼範例說明`assert`運算式的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
