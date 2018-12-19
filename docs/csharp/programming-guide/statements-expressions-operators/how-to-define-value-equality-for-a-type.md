---
title: HOW TO：定義類型的實值相等 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: a2d71994647e50afc8d343725e639b6e9d24831f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244423"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>HOW TO：定義類型的實值相等 (C# 程式設計指南)
當您定義類別或結構時，需判斷是否有必要為類型建立實值相等 (或等價) 的自訂定義。 通常，當該類型的物件必須新增至某種集合，或物件的主要目的是為了儲存一組欄位或屬性時，就會實作實值相等。 您可以根據對該類型中所有欄位和屬性的比較來定義實值相等，也可以根據子集來進行定義。 不論使用哪種方法，在類別和結構中，您的實作都必須遵循下列五項等價保證：  
  
1.  `x.Equals(x)` 會傳回 `true`。 這稱為自反屬性。  
  
2.  `x.Equals(y)` 會傳回與 `y.Equals(x)` 相同的值。 這稱為對稱屬性。  
  
3.  如果 `(x.Equals(y) && y.Equals(z))` 傳回 `true`，則 `x.Equals(z)` 會傳回 `true`。 這稱為可轉移屬性。  
  
4.  只要 x 和 y 所參考的物件沒有經過修改，後續叫用 `x.Equals(y)` 就會傳回相同的值。  
  
5.  `x.Equals(null)` 會傳回 `false`。 不過，`null.Equals(null)` 會擲回例外狀況，而不會遵守上述第二項規則。  
  
 任何您已定義的結構，皆有繼承自 <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> 方法的 <xref:System.ValueType?displayProperty=nameWithType> 覆寫的預設實作實值相等。 此實作使用反映來檢查類型中的所有欄位和屬性。 雖然此實作會產生正確的結果，但相較於您針對該類型特別撰寫的自訂實作卻慢得多。  
  
 對類別和結構而言，實值相等的實作細節並不同。 不過，類別和結構都需要相同的基本步驟來實作相等：  
  
1.  覆寫[虛擬](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> 方法。 在大部分情況下，實作 `bool Equals( object obj )` 應該只會呼叫特定類型的 `Equals` 方法，這是 <xref:System.IEquatable%601?displayProperty=nameWithType> 介面的實作。 (請參閱步驟 2)。  
  
2.  透過提供類型專屬的 `Equals` 方法實作 <xref:System.IEquatable%601?displayProperty=nameWithType> 介面。 實際的等價比較是在這裡執行。 例如，您可能決定只比較類型中的一個或兩個欄位，以定義相等。 不會從 `Equals` 擲回例外狀況。 僅適用於類別：此方法只會檢查在類別中宣告的欄位。 它應該呼叫 `base.Equals` 以檢查基底類別中的欄位 (如果類型直接繼承自 <xref:System.Object>，請不要這樣做，因為 <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> 的 <xref:System.Object> 實作會執行參考相等檢查。)  
  
3.  選擇性但建議使用：將 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子多載。  
  
4.  覆寫 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>，以便有實值相等的兩個物件產生相同的雜湊碼。  
  
5.  選擇項：若要支援「大於」或「小於」的定義，請為類型實作 <xref:System.IComparable%601> 介面，並同時多載 [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 和 [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) 運算子。  
  
 接下來的第一個範例示範類別實作。 第二個範例示範結構實作。  
  
## <a name="example"></a>範例  
 下列範例示範如何在類別 (參考型別) 中實作實值相等。  
  
 [!code-csharp[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 在類別 (參考型別) 上，<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> 方法的預設實作都是執行參考相等比較，而不是實值相等檢查。 當實作器覆寫虛擬方法時，其目的是為了提供實值相等語意。  
  
 `==` 和 `!=` 運算子可以和類別搭配使用，即使類別未多載這些運算子也一樣。 不過，預設行為是執行參考相等檢查。 在類別中，如果您多載 `Equals` 方法，您應該多載 `==` 和 `!=` 運算子，但這並非必要。  
  
## <a name="example"></a>範例  
 下列範例示範如何在結構 (實值型別) 中實作實值相等：  
  
 [!code-csharp[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 若為結構，預設實作 <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (這是 <xref:System.ValueType?displayProperty=nameWithType> 中的覆寫版本) 會使用反映執行實值相等檢查，比較類型中的每個欄位值。 當實作器覆寫結構中的虛擬 `Equals` 方法時，其目的是為了提供更有效率的方法來執行實值相等檢查，以及選擇性地根據結構的一部分欄位或屬性進行比較。  
  
 除非結構明確多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子，否則這些運算子無法用於結構。  
  
## <a name="see-also"></a>請參閱

- [相等比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
