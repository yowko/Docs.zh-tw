---
title: 使用結構 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: b1e1405941cf9076e88aee5689ed933724727bb2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237099"
---
# <a name="using-structs-c-programming-guide"></a>使用結構 (C# 程式設計手冊)
`struct` 類型很適合用於代表輕量型物件，例如 `Point`、 `Rectangle`和 `Color`。 雖然使用 [自動實作的屬性](../../../csharp/language-reference/keywords/class.md) 可以輕鬆地將一個點表示為一個 [類別](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)，但是在某些情節中 [結構](../../../csharp/language-reference/keywords/struct.md) 可能會更有效率。 例如，如果您宣告含有 1000 個 `Point` 物件的陣列，您會配置額外的記憶體來參考每個物件；在此案例下，結構所耗用的記憶體會較少。 因為 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 含有名為 <xref:System.Drawing.Point>的物件，所以本範例中的結構會改稱為 "CoOrds"。  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 為結構定義預設 (無參數) 的建構函式時會發生錯誤。 初始化結構主體中的執行個體欄位時也會發生錯誤。 您只能透過使用參數化建構函式、隱含的預設建構函式、[物件初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)，或在宣告結構後個別存取成員，來將可外部存取的結構成員初始化。 任何私用或無法以其他方式存取的成員都需要建構函式的專屬使用。
  
 當您使用 [new](../../../csharp/language-reference/keywords/new.md) 運算子建立結構物件時，不僅會建立物件，還會根據[建構函式的簽章](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax)呼叫適當的建構函式。 不同於類別，結構不需要使用 `new` 運算子就能具現化。 在此案例下，不會有建構函式呼叫，因此配置會更有效率。 不過，欄位會維持未指派狀態，而且必須等到所有欄位都初始化後才能使用物件。 這包括無法透過自動實作的屬性取得或設定值。
 
 如果您使用預設值、無參數建構函式具現化結構物件，所有成員都會根據其[預設值](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)指派。
  
 在使用結構的參數撰寫建構函式時，您必須明確初始化所有成員，否則一或多個成員仍會維持未指派，而且無法使用結構，因而產生編譯器錯誤 CS0171。  
  
 不同於類別，結構沒有繼承。 結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 不過，結構可以繼承自基底類別 <xref:System.Object>。 結構可以實作介面，而且其作法就跟類別一樣。  
  
 您無法使用關鍵字 `struct`宣告類別。 在 C# 中，類別和結構在語意上是不同的。 結構是實值類型，而類別是參考類型。 如需詳細資訊，請參閱 [實值類型](../../../csharp/language-reference/keywords/value-types.md)。  
  
 除非您需要參考類型語意，否則系統處理小型類別可能會更有效率 (如果您改為將其宣告為結構)。  
  
## <a name="example-1"></a>範例 1  
  
### <a name="description"></a>說明  
 此範例示範如何使用預設和參數化建構函式進行 `struct` 初始化。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>範例 2  
  
### <a name="description"></a>說明  
 此範例示範結構特有的功能。 它在建立 CoOrds 物件時並未使用 `new` 運算子。 如果您以 `class` 一字取代 `struct` 一字，將不會編譯程式。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)
