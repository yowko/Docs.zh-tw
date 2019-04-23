---
title: 索引子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 5ab0a5e524979110c355391cf800cc82e6d6244f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680153"
---
# <a name="indexers-c-programming-guide"></a>索引子 (C# 程式設計手冊)

索引子允許類別或結構的執行個體像陣列一樣地編製索引。 您不需明確指定型別或執行個體成員，就能設定或擷取已索引的值。 索引子和[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)類似，差異在於它們的存取子會採用參數。  
 
 下列範例定義具有簡單 [get](../../../csharp/language-reference/keywords/get.md) 和 [set](../../../csharp/language-reference/keywords/set.md) 存取子方法的泛型類別來指派和擷取值。 `Program` 類別會建立此類別的執行個體以儲存字串。  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  如需更多範例，請參閱[相關章節](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)。  
  
## <a name="expression-body-definitions"></a>運算式主體定義  
 
通常會利用索引子的 get 或 set 存取子來組成要傳回或設定值的陳述式。 運算式主體成員提供簡化的語法來支援此案例。 從 C# 6 開始，可將唯讀索引子實作為運算式主體成員，如下列範例所示。

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

請注意，`=>` 會引進運算式主體，且不使用 `get` 關鍵字。 

從 C# 7.0 開始，可同時將 get 和 set 存取子實作為運算式主體成員。 在此情況下，必須同時使用 `get` 和 `set` 關鍵字。 例如：

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>索引子概觀  
  
-   索引子可以讓物件利用與陣列類似的方式編製索引。  
  
-   `get` 存取子會傳回值。 `set` 存取子會指派值。  
  
-   [this](../../../csharp/language-reference/keywords/this.md) 關鍵字是用來定義索引子。  
  
-   [value`set` 關鍵字是用來定義 ](../../../csharp/language-reference/keywords/value.md) 索引子要指派的值。  
  
-   索引子不一定要由整數值編製索引。您可自行決定如何定義特定的查詢機制。  
  
-   索引子可以多載。  
  
-   索引子可具有一個以上的型式參數，例如，存取二維陣列時。  
  
## <a name="BKMK_RelatedSections"></a> 相關章節  
  
-   [使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [介面中的索引子](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [屬性與索引子之間的比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[索引子](~/_csharplang/spec/classes.md#indexers)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)
