---
title: 泛型 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167488"
---
# <a name="generics-c-programming-guide"></a>泛型 (C# 程式設計手冊)

泛型將類型參數的概念引入 .NET Framework，從而可以設計類和方法，在用戶端代碼聲明和具現化類或方法之前，可以延遲一個或多個類型的規範。 例如，通過使用泛型型別參數`T`，可以編寫一個其他用戶端代碼可以使用的類，而不會產生運行時強制轉換或裝箱操作的成本或風險，如下所示：

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

泛型類和方法以非泛型類無法實現的方式將再使用性、型別安全性和效率結合起來。 泛型最常搭配在其上操作的集合和方法使用。 命名<xref:System.Collections.Generic>空間包含多個基於泛型的集合類。 非泛型集合（如<xref:System.Collections.ArrayList>不推薦）是為相容性目的維護的。 如需詳細資訊，請參閱 [.NET 的泛型](../../../standard/generics/index.md)。

當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。 下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用 （在大多數情況下，應使用 .NET <xref:System.Collections.Generic.List%601> Framework 類庫提供的類，而不是創建自己的類。類型參數`T`用於多個位置，其中通常使用具體類型來指示存儲在清單中的項的類型。 這個參數可以用於下列方面：

- 作為 `AddHead` 方法中的方法參數類型。
- 作為巢狀 `Node` 類別中 `Data` 屬性的傳回型別。
- 作為巢狀類別中私用成員 `data` 的類型。

 請注意，`T`嵌套`Node`類可用。 當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。 您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>泛型概述

- 使用泛型型別以最佳化程式碼重複使用、型別安全和效能。
- 泛型的最常見用法是建立集合類別。
- .NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。 您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。
- 您可以創建自己的通用介面、類、方法、事件和委託。
- 泛型類別可限制為允許存取特定資料類型上的方法。
- 泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。

## <a name="related-sections"></a>相關章節

- [泛型型別參數](generic-type-parameters.md)
- [型別參數的條件約束](constraints-on-type-parameters.md)
- [通用類](generic-classes.md)
- [泛型介面](generic-interfaces.md)
- [通用方法](generic-methods.md)
- [通用委託](generic-delegates.md)
- [C++ 範本和 C# 泛型之間的差異](differences-between-cpp-templates-and-csharp-generics.md)
- [泛型和反映](generics-and-reflection.md)
- [執行階段中的泛型](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/types.md#constructed-types)。

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C# 程式設計指南](../index.md)
- [型別](../types/index.md)
- [\<類型帕拉姆>](../xmldoc/typeparam.md)
- [\<類型帕阿姆夫>](../xmldoc/typeparamref.md)
- [.NET 的泛型](../../../standard/generics/index.md)
