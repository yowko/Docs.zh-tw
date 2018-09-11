---
title: 運算式 (C# 程式設計手冊)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 3cf084102186d9e13727c36ed14e2ea72ca324f9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213802"
---
# <a name="expressions-c-programming-guide"></a>運算式 (C# 程式設計手冊)
「運算式」是一連串的一或多個運算元以及兩或多個運算子，可以評估為單一值、物件、方法或命名空間。 運算式可以包含常值、方法呼叫、運算子和其運算元，或「簡單名稱」。 簡單名稱可以是變數、型別成員、方法參數、命名空間或型別的名稱。  
  
 運算式可以使用運算子 (後者又可能使用其他運算式當作參數) 或方法呼叫 (它的參數又可能是其他方法呼叫)，因此運算式的範圍可以從簡單到非常複雜。 下列是兩個運算式範例：  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>運算式值  
 在大部分使用運算式的內容中 (例如在陳述式或方法參數中)，運算式必須評估為某個值。 如果 x 和 y 是整數，則運算式 `x + y` 評估為數值。 運算式 `new MyClass()` 評估為 `MyClass` 物件之新執行個體的參考。 運算式 `myClass.ToString()` 評估為字串，因為這是方法的傳回型別。 不過，雖然命名空間名稱分類為運算式，但是未評估為值，因此絕不會有任何運算式的最終結果。 您無法將命名空間名稱傳遞給方法參數，或用於新的運算式，或將它指派給變數。 您只能將它用作較大運算式中的子運算式。 這也適用於類型 (與 <xref:System.Type?displayProperty=nameWithType> 物件不同)、方法群組名稱 (與特定方法不同) 以及事件 [add](../../../csharp/language-reference/keywords/add.md) 和 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子。  
  
 每個值都有關聯型別。 例如，如果 x 和 y 都是 `int` 類型的變數，則運算式 `x + y` 的值也會輸入為 `int`。 如果將值指派給不同類型的變數，或者，如果 x 和 y 是不同的類型，則會套用類型轉換規則。 如需這類轉換運作方式的詳細資訊，請參閱[轉換和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
## <a name="overflows"></a>溢位  
 如果值大於實值型別的最大值，則數值運算式可能會造成溢位。 如需詳細資訊，請參閱 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) 以及[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
## <a name="operator-precedence-and-associativity"></a>運算子優先順序和關聯性  
 運算式的評估方式受到關聯性和運算子優先順序規則的管理。 如需詳細資訊，請參閱[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)。  
  
 大多數的運算式 (指派運算式和方法叫用運算式除外) 必須內嵌在陳述式中。 如需詳細資訊，請參閱[陳述式](../../../csharp/programming-guide/statements-expressions-operators/statements.md)。  
  
## <a name="literals-and-simple-names"></a>常值和簡單名稱  
 兩個最簡單類型的運算式是常值和簡單名稱。 常值是沒有名稱的常數值。 例如，在下列程式碼範例中，`5` 和 `"Hello World"` 都是常值︰  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 如需常值的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。  
  
 在上述範例中，`i` 和 `s` 是識別區域變數的簡單名稱。 在運算式中使用這些變數時，變數名稱會評估為目前儲存在記憶體中變數位置的值。 下列範例會顯示這一點：  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>叫用運算式  
 在下列程式碼範例中，`DoWork` 呼叫是叫用運算式。  
  
```csharp
DoWork();  
```  
  
 方法叫用需要後面接著括弧和任何方法參數的方法名稱，這是先前範例中的名稱，或另一個運算式的結果。 如需詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。 委派叫用會使用以括弧括住的委派和方法參數名稱。 如需詳細資訊，請參閱[委派](../../../csharp/programming-guide/delegates/index.md)。 如果方法傳回值，則方法叫用和委派叫用會評估為方法的傳回值。 傳回 void 的方法不能用來取代運算式中的值。  

## <a name="query-expressions"></a>查詢運算式  
 運算式的相同規則通常會套用到查詢運算式。 如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式代表「內嵌方法」，而這種方法沒有名稱，但可以有輸入參數和多個陳述式。 它們廣泛用於 LINQ，以將引數傳遞給方法。 根據所使用的內容，會將 Lambda 運算式編譯為委派或運算式樹狀架構。 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
## <a name="expression-trees"></a>運算式樹狀架構

運算式樹狀架構會將運算式代表為資料結構。 LINQ 提供者廣泛使用它們，以將查詢運算式轉譯為某個其他內容中有意義的程式碼，例如 SQL 資料庫。 如需詳細資訊，請參閱[運算式樹狀架構 (C#)](../concepts/expression-trees/index.md)。
  
## <a name="expression-body-definitions"></a>運算式主體定義

C# 支援「運算式主體成員」，可讓您提供方法、建構函式、完成項、屬性和索引子的精簡運算式主體定義。 如需詳細資訊，請參閱[運算式主體成員](expression-bodied-members.md)。

## <a name="remarks"></a>備註  
 只要從運算式識別變數、物件屬性或物件索引子存取，就會使用該項目的值作為運算式的值。 只要運算式最後評估為必要類型，就可以將運算式放在 C# 中需要值或物件的任何位置。  

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [委派](../../../csharp/programming-guide/delegates/index.md)  
- [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
- [型別](../../../csharp/programming-guide/types/index.md)  
- [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)
