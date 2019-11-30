---
title: F# 4.7 的新功能- F#指南
description: 取得4.7 中F#可用的新功能總覽。
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644065"
---
# <a name="whats-new-in-f-47"></a>4\.7 中F#的新功能

F#4.7 新增多項語言的F#增強功能。

## <a name="get-started"></a>開始使用

F#4.7 適用于所有 .NET Core 發行版本和 Visual Studio 工具。 [開始使用F# ](../get-started/index.md)以深入瞭解。

## <a name="language-version"></a>語言版本

F# 4.7 編譯器導入了透過專案檔中的屬性來設定有效語言版本的功能：

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

您可以將它設定為 `4.6`、`4.7`、`latest`和 `preview`的值。 預設為 `latest`。

如果您將它設定為 `preview`，您的編譯器將F#會啟動在編譯器中執行的所有預覽功能。

## <a name="implicit-yields"></a>隱含產生

您不再需要在可推斷類型的陣列、清單、序列或計算運算式中套用 `yield` 關鍵字。 在下列範例中，兩個運算式都需要F# 4.7 之前每個專案的 `yield` 語句：

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [ 
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then 
            "Saturday"
            "Sunday"
    ] 
```

如果您引進單一 `yield` 關鍵字，則每個其他專案也必須套用 `yield`。

在運算式中使用時，隱含產生不會啟動，也會使用 `yield!` 來執行像是壓平定序序列等動作。 在這些情況下，您必須繼續使用 `yield`。

## <a name="wildcard-identifiers"></a>萬用字元識別碼

在F#涉及類別的程式碼中，自我識別元在成員宣告中必須一律是明確的。 但在從未使用過自我識別碼的情況下，傳統上使用雙底線來表示不具有任何自我識別元的慣例。 您現在可以使用單一底線：

```fsharp
type C() =
    member _.M() = ()
```

這也適用于 `for` 迴圈：

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>縮排 relaxations

在F# 4.7 之前，主要的函式和靜態成員引數的縮排需求需要過多的縮排。 它們現在只需要單一縮排範圍：

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
