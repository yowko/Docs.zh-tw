---
title: 判斷提示 (F#)
description: "了解如何使用 '判斷提示' 運算式做為偵錯功能在 F # 程式設計語言中測試運算式。"
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579318"
---
# <a name="assertions"></a>判斷提示

`assert`運算式是偵錯功能，您可以使用它來測試運算式。 當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。

## <a name="syntax"></a>語法

```fsharp
assert condition
```

## <a name="remarks"></a>備註

`assert`運算式具有類型`bool -> unit`。

在先前的語法*條件*表示要測試的布林運算式。 如果運算式評估為`true`，執行會持續不受影響。 如果評估為`false`，就會產生系統錯誤 對話方塊。 [錯誤] 對話方塊中已包含字串的標題**判斷提示失敗**。 對話方塊包含堆疊追蹤，指出判斷提示失敗發生的位置。

判斷提示檢查偵錯模式，在編譯時，才會啟用也就是說，如果常數`DEBUG`定義。 在專案系統中，根據預設，`DEBUG`常數定義在偵錯組態，但不是在發行組態。

無法使用 F # 例外狀況處理攔截判斷提示失敗錯誤。

>[!NOTE]
`assert`函式會解析成<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列程式碼範例示範如何將`assert`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
