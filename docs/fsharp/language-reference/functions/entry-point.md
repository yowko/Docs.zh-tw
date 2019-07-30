---
title: 進入點
description: 瞭解如何將進入點設定為編譯為F#可執行檔的程式, 其中會正式開始執行。
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630529"
---
# <a name="entry-point"></a>進入點

本主題說明用來設定F#程式進入點的方法。

## <a name="syntax"></a>語法

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>備註

在先前的語法中, *let 函數*系結是系結中`let`函式的定義。

編譯為可執行檔之程式的進入點是執行正式開始的位置。 您可以藉由F# `EntryPoint`將屬性套用至程式的`main`函式, 來指定應用程式的進入點。 這個函式 (使用`let`系結所建立) 必須是上次編譯檔案中的最後一個函式。 上次編譯的檔案是專案中的最後一個檔案, 或傳遞至命令列的最後一個檔案。

進入點函式具有類型`string array -> int`。 在命令列上提供的引數會傳遞至`main`字串陣列中的函式。 陣列的第一個元素是第一個引數;可執行檔的名稱不會包含在陣列中, 因為它是在某些其他語言中。 傳回值會當做進程的結束代碼使用。 零通常表示成功;非零值表示發生錯誤。 非零傳回碼的特定意義沒有任何慣例;傳回碼的意義是應用程式特有的。

下列範例說明簡單`main`的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

當使用命令列`EntryPoint.exe 1 2 3`來執行此程式碼時, 輸出會如下所示。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>隱含進入點

當程式沒有明確指出進入點的**EntryPoint**屬性時, 最後一個要編譯的檔案中的最上層系結會當做進入點使用。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
- [let 繫結](let-bindings.md)
