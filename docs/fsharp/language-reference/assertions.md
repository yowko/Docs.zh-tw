---
title: 判斷提示 (F#)
description: "了解如何使用 'assert' 運算式做為偵錯功能的測試在 F # 程式語言中的運算式。"
ms.date: 05/16/2016
ms.openlocfilehash: 83e6cd77bbbb2c32e9b778e5bf6dd9d2e9c8fe32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="assertions"></a>判斷提示

`assert`運算式是偵錯功能，可用來測試一個運算式。 當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。

## <a name="syntax"></a>語法

```fsharp
assert condition
```

## <a name="remarks"></a>備註

`assert`運算式具有型別`bool -> unit`。

在先前的語法，*條件*表示要測試的布林運算式。 如果運算式評估為`true`，執行會持續不受影響。 如果評估為`false`，系統錯誤 對話方塊就會產生。 錯誤對話方塊具有標題包含字串**判斷提示失敗**。 此對話方塊包含堆疊追蹤，指出發生判斷提示失敗。

判斷提示檢查只有當您偵錯模式，在編譯時，才會啟用也就是說，如果常數`DEBUG`定義。 在專案系統中，依預設，`DEBUG`常數定義在偵錯組態，但不是在發行組態。

無法使用 F # 例外狀況處理攔截判斷提示失敗錯誤。

>[!NOTE]
`assert`函式會解析成<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列程式碼範例說明使用`assert`運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)
