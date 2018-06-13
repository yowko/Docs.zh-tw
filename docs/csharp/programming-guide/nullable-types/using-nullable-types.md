---
title: 使用可為 Null 的類型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2fe0f34c45d3de0516a71ca5ed4dc807df4bf93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336917"
---
# <a name="using-nullable-types-c-programming-guide"></a>使用可為 Null 的類型 (C# 程式設計手冊)
可為 Null 的型別能代表基礎類型的所有值，以及額外的 [null](../../../csharp/language-reference/keywords/null.md) 值。 可為 Null 的型別會以下列兩種方法之一宣告︰  
  
 `System.Nullable<T> variable`  
  
 -或-  
  
 `T? variable`  
  
 `T` 是可為 Null 類型的基礎類型。 `T` 可以是包括 `struct` 在內的任何實值型別，不能是參考型別。  
  
 如需可能使用可為 Null 類型的範例，請考慮一般的布林值變數如何能有兩個值︰true 和 false。 沒有任何表示「未定義」的值。 在許多程式設計應用程式最值得注意的資料庫互動中，變數會出現在未定義的狀態。 例如，資料庫的欄位可能包含值 true 或 false，但也可能完全不包含任何值。 同樣地，參考型別可以設為 `null` 以表示其尚未初始化。  
  
 此差異會造成額外的程式設計工作、使用額外的變數儲存狀態資訊、使用特殊值等等。 可為 Null 的型別修飾詞可讓 C# 建立實值型別變數，指出未定義的值。  
  
## <a name="examples-of-nullable-types"></a>可為 Null 類型的範例  
 任何實值型別皆可用為可為 Null 類型的基礎。 例如:   
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>可為 Null 類型的成員  
 每個可為 Null 類型的執行個體皆有兩個公用唯讀屬性：  
  
-   `HasValue`  
  
     `HasValue` 是 `bool` 類型。 當變數包含非 Null 值時，它會設成 `true`。  
  
-   `Value`  
  
     `Value` 是與基礎類型相同的類型。 如果 `HasValue` 為 `true`，則 `Value` 包含有意義的值。 如果 `HasValue` 為 `false`，存取 `Value` 將會擲回 <xref:System.InvalidOperationException>。  
  
 本例使用 `HasValue` 成員先測試變數是否包含值，再嘗試顯示它。  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 您也可以如下列範例所示測試值︰  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>明確轉換  
 可為 Null 的型別可以明確轉換，或使用 `Value` 屬性轉換成一般類型。 例如:   
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 如果在兩種資料類別之間定義使用者定義轉換，則這些資料類型的可為 Null 版本也可使用相同的轉換。  
  
## <a name="implicit-conversions"></a>隱含轉換  
 可為 Null 類型的變數可以 `null` 關鍵字設定為 Null，如下例所示︰  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 一般類型是隱含轉換成可為 Null 的型別。  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>運算子  
 預先定義的一元和二元運算子，以及針對實值型別而存在的任何使用者定義的運算子，也能為可為 Null 的型別所用。 如果運算元是 Null，則這些運算子會產生 Null 值；否則，運算子會使用所包含的值來計算結果。 例如:   
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 當您使用可為 Null 的型別執行比較時，如果其中一個可為 Null 類型的值為 Null 而另一個不是時，除 `!=` (不等於) 之外，所有的比較都會評估為 `false`。 請絕對不要因為特定的比較傳回 `false`，所以就假設相反的情況會傳回 `true`。 在下列範例中，10 不大於、小於、也不等於 Null。 只有 `num1 != num2` 評估為 `true`。  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 兩個都是 Null 的可為 Null 類型的相等比較評估為 `true`。  
  
## <a name="the--operator"></a>?? 運算子  
 `??` 運算子定義的預設值，會在可為 Null 的型別指派給不可為 Null 的型別時傳回。  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 這個運算子也可以搭配多個可為 Null 的型別使用。 例如:   
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>bool? 類型  
 `bool?` 可為 Null 的型別可以包含三個不同的值︰[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 和 [null](../../../csharp/language-reference/keywords/null.md)。 如需如何從 bool? 轉換成 bool 的資訊，請參閱[如何：從 bool? 安全轉型到 bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)。  
  
 可為 Null 的布林值就像 SQL 中使用的布林值變數類型。 為確定 `&` 和 `|` 運算子所產生的結果與 SQL 的三個布林值類型一致，會提供下列預先定義的運算子︰  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 下表列出這些運算子的結果：  
  
|X|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|False|false|true|  
|true|null|null|true|  
|False|true|False|true|  
|False|False|False|False|  
|False|null|False|null|  
|null|true|null|true|  
|null|False|False|null|  
|null|null|null|null|  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)  
 [對可為 Null 的型別進行 boxing](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
