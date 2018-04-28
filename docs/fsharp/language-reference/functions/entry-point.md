---
title: 進入點 (F#)
description: '了解如何設定為 編譯為可執行檔，正式開始執行 F # 程式的進入點。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 42e5fe7f85285f990ef92e9791ed5bdfacb85059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="entry-point"></a>進入點

本主題描述您用來設定 F # 程式的進入點方法。


## <a name="syntax"></a>語法

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>備註
在先前的語法，*讓函式繫結*是在函式定義`let`繫結。

會編譯為可執行檔是正式開始執行程式進入點。 您套用指定的 F # 應用程式的進入點`EntryPoint`屬性的程式`main`函式。 此函式 (使用建立`let`繫結) 必須是最後一個編譯檔案中的最後一個函式。 最後一個已編譯的檔案是專案中的最後一個檔案或傳遞至命令列的最後一個檔案。

進入點函式具有類型`string array -> int`。 在命令列上所提供的引數會傳遞至`main`函式的字串陣列中。 陣列的第一個項目是第一個引數。可執行檔的名稱不會包含在陣列中，因為它是其他語言中。 處理序結束碼為使用的傳回值。 零通常會表示成功。非零值表示錯誤。 沒有任何特定的意義，則為非零的傳回碼; 的慣例傳回碼的意義是特定應用程式。

下列範例將說明簡單`main`函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

使用命令列執行此程式碼時`EntryPoint.exe 1 2 3`，輸出如下所示。

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>隱含的進入點
當程式沒有任何**EntryPoint**屬性會明確指出 進入點，最後一個檔案中編譯的最上層繫結會用做為進入點。


## <a name="see-also"></a>另請參閱
[函式](index.md)

[let 繫結](let-bindings.md)
