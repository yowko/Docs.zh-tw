---
title: 進入點 (F#)
description: '了解如何設定為 編譯為可執行檔，正式開始執行 F # 程式的進入點。'
ms.date: 05/16/2016
ms.openlocfilehash: 298500931d49c891a7a243295333df3a9f5d413e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675934"
---
# <a name="entry-point"></a>進入點

本主題說明您使用 F # 程式中設定的進入點方法。

## <a name="syntax"></a>語法

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>備註

在先前的語法*可讓函式繫結*中的函式的定義`let`繫結。

會編譯為可執行檔是正式開始執行的程式進入點。 將套用指定的 F # 應用程式的進入點`EntryPoint`屬性的程式`main`函式。 此函式 (使用建立`let`繫結) 必須是最後一個編譯檔案中的最後一個函式。 專案中的最後一個檔案或傳遞至命令列的最後一個檔案的最後一個編譯的檔案。

進入點函式具有類型`string array -> int`。 在命令列上提供的引數傳遞至`main`函式中的字串陣列。 陣列的第一個項目是第一個引數;可執行檔的名稱不會包含在陣列中，因為它在其他程式設計語言。 傳回值用於程序結束代碼。 零通常表示成功，非零值表示發生錯誤。 不沒有特定的意義，非零的傳回碼; 的任何慣例傳回碼的意義是特定應用程式。

下列範例說明簡單`main`函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

使用命令列執行此程式碼時`EntryPoint.exe 1 2 3`，輸出如下所示。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>隱含的進入點

當程式沒有任何**EntryPoint**明確指出 進入點，最後一個檔案中編譯的最上層繫結的屬性做為進入點。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
- [let 繫結](let-bindings.md)
