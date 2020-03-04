---
title: C# 陣列 - C# 語言教學課程
description: 陣列是 C# 語言中最基本的集合類型
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159191"
---
# <a name="arrays"></a>陣列

***陣列***是一種資料結構，其中包含一些可透過計算索引存取的變數。 陣列中包含的變數 (也稱為陣列的***元素***) 屬於相同的型別，這種型別稱為陣列的***元素型別***。

陣列型別是參考型別，而陣列變數的宣告只是預留空間給陣列執行個體的參考。 實際的陣列執行個體是執行階段期間使用 New 運算子動態建立。 新增作業會指定新陣列執行個體的***長度***，這在該執行個體的存留期是固定的。 陣列元素的索引範圍在 `0` 到 `Length - 1` 之間。 `new` 運算子會自動將陣列的元素初始化為其預設值，例如，針對所有數值型別，此值為零，而針對所有參考型別，此值為 `null`。

下列範例會建立 `int` 元素的陣列、初始化陣列，並印出陣列的內容。

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

這個範例會建立並操作***一維陣列***。 C# 也支援***多維陣列***。 一個陣列型別的維度數目 (亦稱為陣列型別的***順位***)，是寫入陣列型別的方括弧之間的逗號數目加一。 下列範例會分別配置一個單維、一個二維和一個三維陣列。

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` 陣列包含 10 個元素、`a2`陣列包含 50 (10 × 5) 個元素，`a3` 陣列包含 100 (10 × 5 × 2) 個元素。
陣列的元素型別可以是任一型別，包括陣列型別。 具有陣列類型之元素的陣列有時稱為***不規則陣列***，因為元素陣列的長度不一定是相同的。 下列範例會配置一個 `int` 型別的陣列：

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

第一行建立包含三個元素的陣列，每個元素的型別均為 `int[]`，每個元素的初始值均為 `null`。 接下來的幾行則使用不同長度的個別陣列執行個體的參考初始化三個元素。

New 運算子允許使用***陣列初始設定式***指定陣列元素的初始值，這是寫入分隔符號 `{` 和 `}` 之間的運算式清單。 下列範例使用三個元素配置並初始化 `int[]`。

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

陣列的長度是從 {和} 之間的運算式數目推斷而來。 本機變數與欄位宣告可以進一步縮短，就不需要重新敘述陣列型別。

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

上述兩個範例都相當於下列程式碼：

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[上一頁](classes-and-objects.md)
>[下一頁](interfaces.md)
