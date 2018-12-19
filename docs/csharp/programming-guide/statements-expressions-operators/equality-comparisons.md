---
title: 相等比較 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 2bf1e788c635dd466739178f80b0f2f147c04cfd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235354"
---
# <a name="equality-comparisons-c-programming-guide"></a>相等比較 (C# 程式設計手冊)
有時候需要比較兩個值是否相等。 在某些情況下，您要測試「值是否相等」 (也稱為「等價」，表示兩個變數所含的值相等。 在其他情況下，您必須判斷兩個變數是否參照記憶體中的相同基礎物件。 這類型的相等稱為「參考相等」或「識別」。 本主題描述這兩種相等，並提供其他主題的連結以取得詳細資訊。  
  
## <a name="reference-equality"></a>參考相等  
 參考相等表示兩個物件參考都指向相同的基礎物件。 這可能是透過簡單指派所發生，如下列範例所示。  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 在這個程式碼中，建立兩個物件，但在指派陳述式之後，這兩個參考都指向相同的物件。 因此，它們具有參考相等。 使用 <xref:System.Object.ReferenceEquals%2A> 方法，以判斷兩個參考是否指向相同的物件。  
  
 參考相等的概念只適用於參考類型。 因為將實值型別的執行個體指派給變數時會建立實值的複本，所以實值型別物件不能具有參考相等。 因此，您絕不會有兩個參照記憶體中相同位置的 Unboxed 結構。 此外，如果您使用 <xref:System.Object.ReferenceEquals%2A> 來比較兩個實值型別，則結果一律為 `false`，即使物件中所包含的值完全相同也是一樣。 這是因為每個變數都會對個別物件執行個體進行 Boxed 處理。 如需詳細資訊，請參閱[＜How to：參考相等 (識別) 的測試](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)。  
  
## <a name="value-equality"></a>實值相等  
 實值相等表示兩個物件包含相同的值。 對於 [int](../../../csharp/language-reference/keywords/int.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) 這類基本實值型別，測試實值相等十分簡單。 您可以使用 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 運算子，如下列範例所示。  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 對於大部分其他類型，測試實值相等較為複雜，因為您需要了解類型如何定義它。 對於具有多個欄位或屬性的類別和結構，通常會定義實值相等，表示所有欄位或屬性具有相同的值。 例如，如果 pointA.X 等於 pointB.X 而且 pointA.Y 等於 pointB.Y，則兩個 `Point` 物件可能定義為相等。  
  
 不過，相等性不需要根據類型中的所有欄位。 而是根據子集。 當您比較不屬於您的類型時，務必特別了解如何定義該類型的相等性。 如需如何在您自己的類別和結構中定義實值相等的詳細資訊，請參閱[如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)。  
  
### <a name="value-equality-for-floating-point-values"></a>浮點值的實值相等  
 浮點值的相等比較 ([double](../../../csharp/language-reference/keywords/double.md) 和 [float](../../../csharp/language-reference/keywords/float.md)) 有問題，因為二進位電腦上的浮點算術不精確。 如需詳細資訊，請參閱 <xref:System.Double?displayProperty=nameWithType> 主題中的備註。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何：參考相等 (識別) 的測試](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|描述如何判斷兩個變數是否具有參考相等。|  
|[如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|描述如何提供類型實值相等的自訂定義。|  
|[C# 程式設計指南](../../../csharp/programming-guide/index.md)|提供重要 C# 語言功能以及可透過 .NET Framework 以 C# 取得之功能的詳細資訊連結。|  
|[型別](../../../csharp/programming-guide/types/index.md)|提供 C# 類型系統的相關資訊以及其他資訊的連結。|  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
