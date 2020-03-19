---
title: F# 4.7 - F# 指南中的新增功能
description: 獲取 F# 4.7 中提供的新功能的概述。
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185867"
---
# <a name="whats-new-in-f-47"></a>F# 4.7 中的新增功能

F# 4.7 為 F# 語言添加了多項改進。

## <a name="get-started"></a>開始使用

F# 4.7 在所有 .NET 核心發行版本和視覺化工作室工具中均可用。 [開始使用 F#](../get-started/index.md)瞭解更多資訊。

## <a name="language-version"></a>語言版本

F# 4.7 編譯器引入了通過專案檔案中的屬性設置有效語言版本的能力：

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

可以將其`4.6`設置為 值 、`4.7``latest`和`preview`。 預設值為 `latest`。

如果將其設置為`preview`，編譯器將啟動編譯器中實現的所有 F# 預覽功能。

## <a name="implicit-yields"></a>隱式收益

不再需要在`yield`可以推斷類型的陣列、清單、序列或計算運算式中應用關鍵字。 在下面的示例中，兩個運算式都需要 F# 4.7 之前每個條目的`yield`語句：

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

如果引入單個`yield`關鍵字，則所有其他項也必須已`yield`應用於該關鍵字。

在運算式中使用時，隱式收益不會啟動，該運算式`yield!`還用於執行諸如拼平序列之類的操作。 在這些情況下，今天必須繼續`yield`使用。

## <a name="wildcard-identifiers"></a>萬用字元識別碼

在涉及類的 F# 代碼中，自識別碼必須始終在成員聲明中顯式。 但是，在從未使用自識別碼的情況下，傳統上使用雙底線來指示無名的自識別碼是慣例。 現在可以使用單個底線：

```fsharp
type C() =
    member _.M() = ()
```

這也適用于`for`迴圈：

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>縮進鬆弛

在 F# 4.7 之前，主建構函式和靜態成員參數的縮進要求要求過高的縮進。 它們現在只需要一個縮進範圍：

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
