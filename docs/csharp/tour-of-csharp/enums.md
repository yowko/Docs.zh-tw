---
title: C# 列舉 - C# 語言教學課程
description: 了解 C# 中的列舉、離散的具名常數。
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 8c1c29c3c06829da81a9c9be8bb5bd99f1c9e395
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57843120"
---
# <a name="enums"></a>列舉

「列舉型別」是含一組具名常數的相異實值型別。 當您需要定義可擁有一組離散值的型別時，便可定義列舉。 它們使用其中一個整數值型別作為其基礎儲存體。 它們會為離散值提供語意意義。

下列範例會宣告並使用名為 `Color` 的 `enum` 型別搭配三個常數值 `Red`、`Green` 及 `Blue`。

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

每個 `enum` 型別都有對應的整數型別，稱為 `enum` 型別的「基礎型別」。 未明確宣告基礎型別的 `enum` 型別會擁有 `int` 基礎型別。 `enum` 型別的儲存格式和可能的值範圍取決於其基礎型別。 `enum` 型別可接受的一組值並不受其 `enum` 成員限制。 特別是，`enum` 之基礎型別的任何值都可轉換成 `enum` 型別，並且是該 `enum` 型別的相異有效值。

下列範例會宣告一個基礎型別為 `sbyte`、名為 `Alignment` 的 `enum` 型別。

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

如上一個範例所示，`enum` 成員宣告可以包含會指定成員值的常數運算式。 每個 `enum` 成員的常數值都必須在 `enum` 的基礎型別範圍內。 當 `enum` 成員宣告並未明確指定值時，賦予成員的值會是零 (如果它是 `enum` 型別中的第一個成員) 或是本文上前面 `enum` 成員的值加 1。

您可以使用型別轉換將 `Enum` 值轉換成整數值。 例如：

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

任何 `enum` 型別的預設值都是轉換成 `enum` 型別的整數值零。 在變數自動初始化成預設值的情況中，這是賦予 `enum` 型別之變數的值。 為了讓 `enum` 型別的預設值可供輕鬆取得，常值 `0` 會隱含地轉換成任何 `enum` 型別。 因此，允許以下的情況。

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

> [!div class="step-by-step"]
> [上一頁](interfaces.md)
> [下一頁](delegates.md)
