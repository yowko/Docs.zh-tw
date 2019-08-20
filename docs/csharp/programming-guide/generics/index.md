---
title: 泛型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589601"
---
# <a name="generics-c-programming-guide"></a>泛型 (C# 程式設計手冊)
泛型是在 C# 語言和 Common Language Runtime (CLR) 的 2.0 版中新增的功能。 泛型將型別參數的概念引進 .NET Framework 中，使得類別和方法在設計時，可以先行擱置一或多個類型的規格，直到用戶端程式碼對類別或方法進行宣告或具現化時再行處理。 例如，您可以使用泛型型別參數 T，撰寫一個類別供其他用戶端程式碼使用，而不會在執行階段產生轉換或 boxing 作業的成本或風險，如下所示：  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

泛型類別和方法將再使用性、型別安全和效率三者結合在一起，發揮了非泛型類別和方法所無法提供的功能。 泛型最常搭配在其上操作的集合和方法使用。 .NET Framework 2.0 版類別庫提供了新的命名空間 <xref:System.Collections.Generic>，其中包含數個新的泛型集合類別。 建議以 .NET Framework 2.0 和更新版本為目標的所有應用程式都使用新的泛型集合類別，而不是舊版的非泛型集合類別，例如 <xref:System.Collections.ArrayList>。 如需詳細資訊，請參閱 [.NET 的泛型](../../../standard/generics/index.md)。  
  
 當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。 下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用 (在大部分情況下，您應該使用 .NET Framework 類別庫提供的 <xref:System.Collections.Generic.List%601> 類別，而不要自行建立類別)。在幾個位置會使用型別參數 `T`，這些位置一般會使用具象類型來表示清單中儲存的項目類型。 這個參數可以用於下列方面：  
  
- 作為 `AddHead` 方法中的方法參數類型。  
  
- 作為巢狀 `Node` 類別中 `Data` 屬性的傳回型別。  
  
- 作為巢狀類別中私用成員 `data` 的類型。  
  
 請注意，T 可用於巢狀 `Node` 類別。 當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。 您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>泛型概觀  
  
- 使用泛型型別以最佳化程式碼重複使用、型別安全和效能。  
  
- 泛型的最常見用法是建立集合類別。  
  
- .NET Framework 類別庫包含 <xref:System.Collections.Generic> 命名空間中的數種新泛型集合類別。 您應該盡可能使用這些類別，而不是使用類似在 <xref:System.Collections> 命名空間中的 <xref:System.Collections.ArrayList> 類別。  
  
- 您可以建立自己的泛型介面、類別、方法、事件和委派。  
  
- 泛型類別可限制為允許存取特定資料類型上的方法。  
  
- 泛型資料類型中所使用的類型相關資訊，可在執行階段透過反映取得。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
- [泛型型別參數](./generic-type-parameters.md)  
  
- [型別參數的條件約束](./constraints-on-type-parameters.md)  
  
- [泛型類別](./generic-classes.md)  
  
- [泛型介面](./generic-interfaces.md)  
  
- [泛型方法](./generic-methods.md)  
  
- [泛型委派](./generic-delegates.md)  
  
- [C++ 範本和 C# 泛型之間的差異](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [泛型和反映](./generics-and-reflection.md)  
  
- [執行階段中的泛型](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 如需詳細資訊，請參閱＜[C# 語言規格](~/_csharplang/spec/types.md#constructed-types)＞。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic>
- [C# 程式設計指南](../index.md)
- [型別](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [.NET 的泛型](../../../standard/generics/index.md)
