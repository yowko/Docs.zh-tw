---
title: "C# 結構 - C# 語言教學課程"
description: "了解 C# 實值型別 (稱為結構) 的基本概念"
keywords: ".NET, C#, 結構, 實值型別"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="structs"></a>結構

和類別一樣，***結構***是可包含資料成員和函式成員的資料結構，但不同於類別，結構是實值型別，不需要堆積配置。 結構型別的變數直接儲存結構的資料，而類別型別的變數則儲存動態配置物件的參考。 結構型別不支援使用者指定的繼承，且所有結構型別都隱含地繼承自 `object` 型別。

結構特別適用於含有實值語意的小型資料結構。 複數、座標系統中的點或字典中的索引鍵/值組都是結構的良好範例。 針對小型資料結構使用結構而不使用類別，在應用程式執行的記憶體配置數目上有很大的差別。 比方說，下列程式會建立並初始化 100 個點的陣列。 使用 `Point` 做為類別，會具現化 101 個不同的物件 — 一個代表陣列，剩下的每個代表 100 個元素。

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

替代方案是將 Point 變為結構。

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

現在，只有一個物件會具現化 — 代表陣列的物件 — 而 `Point` 執行個體會以內嵌方式儲存在陣列中。

結構建構函式使用新的運算子叫用，但並不代表會配置記憶體。 結構建構函式只會傳回結構值本身 (通常是在堆疊上的暫存位置)，然後再視需要複製此值，而不是動態配置一個物件並傳回該物件的參考。

使用類別時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數參考的物件。 使用結構時，變數各有自己的資料複本，因此在某一個變數上進行的作業不可能會影響其他變數。 例如，下列程式碼片段所產生的輸出取決於點是類別或結構。

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

如果 `Point` 是類別，輸出為 20，因為 a 和 b 參考相同的物件。 如果 Point 是結構，則輸出為 10，因為指派 `a` 至 `b` 會建立值的複本，而後續指派給 `a.x` 時此複本不受影響。

前一個範例會反白顯示結構的兩個限制。 首先，複製整個結構通常較複製物件參考沒有效率，因此，結構的指派和實值參數傳遞會比參考型別耗用更多資源。 再者，除了 `ref` 和 `out` 參數外，不可能建立結構的參考，因此在許多情況下無法使用它們。

>[!div class="step-by-step"]
[上一頁](classes-and-objects.md)
[下一頁](arrays.md)

