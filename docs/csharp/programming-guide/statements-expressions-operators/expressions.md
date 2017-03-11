---
title: "運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 運算式"
  - "運算式 [C#]"
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 運算式 (C# 程式設計手冊)
「*運算式*」\(Expression\) 是一個或多個運算元和零或多個運算子的序列，可計算出單一值、物件、方法或命名空間 \(Namespace\)。  運算式可包含常值、方法引動過程、運算子和運算元，或「*簡單名稱*」\(Simple Name\)。  簡單名稱可以是變數的名稱、型別成員、方法參數、命名空間或型別。  
  
 運算式可以使用將其他運算式用來做為參數的運算子，或使用其參數為其他方法呼叫的方法呼叫，所以運算式的範圍可從簡單到極複雜。  以下是兩個運算式的範例：  
  
```  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25))   
System.Convert.ToInt32("35")  
```  
  
## 運算式的值  
 用到運算式的大部分環境中，例如陳述式 \(Statement\) 或方法參數中，都是將運算式用來評估某個值。  如果 x 和 y 是整數，則運算式 `x + y` 會評估得到一個數值。  運算式 `new MyClass()` 會評估為 `MyClass` 物件之新執行個體 \(Instance\) 的參考。  運算式 `myClass.ToString()` 會評估為字串，因為這是該方法的傳回類型。  不過，雖然命名空間名稱也分類為運算式，但它並不會評估值，所以也不會是運算式的最終結果。  您不能將命名空間名稱傳遞給方法參數、將它用在新運算式中，或將它指派給變數。  您只能將它用做大型運算式的子運算式。  這也適用於型別 \(不同於 <xref:System.Type?displayProperty=fullName> 物件\)、方法群組名稱 \(不同於特定方法\) 以及事件 [add](../../../csharp/language-reference/keywords/add.md) 和 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子 \(Accessor\)。  
  
 每個值都有關聯型別。  例如，如果 x 和 y 都是 `int` 型別的變數，則運算式 `x + y` 的值也會是 `int` 型別。  如果將值指派給不同型別的變數，或 x 和 y 屬於不同型別，這時會套用型別轉換規則。  如需此類轉換運作方式的詳細資訊，請參閱[轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
## 溢位  
 如果數值運算式的值大於該值型別的最大值，便可能引起溢位。  如需詳細資訊，請參閱 [Checked 與 Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)和 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
## 運算子優先順序和順序關聯性  
 運算式的評估方式由順序關聯性 \(Associativity\) 和運算子優先順序 \(Operator Precedence\) 的規則所控制。  如需詳細資訊，請參閱 [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)。  
  
 大部分運算式 \(指派運算式和方法引動運算式除外\) 都必須內嵌於陳述式中。  如需詳細資訊，請參閱 [陳述式](../../../csharp/programming-guide/statements-expressions-operators/statements.md)。  
  
## 常值和簡單名稱  
 最簡單的兩種運算式類型為常值和簡單名稱。  常值是沒有名稱的常數值。  例如，在下列程式碼範例中，`5` 和 `"Hello World"` 都是常值︰  
  
 [!code-cs[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/expressions_1.cs)]  
  
 如需常值的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。  
  
 在上述範例中，`i` 和 `s` 都是用來辨識區域變數的簡單名稱。  在運算式中使用這些變數時，變數名稱會評估為目前儲存在記憶體中變數位置上的值。  這會在下列範例中示範：  
  
 [!code-cs[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/expressions_2.cs)]  
  
## 叫用運算式  
 以下程式碼範例中，`DoWork` 的呼叫為叫用運算式。  
  
```  
DoWork();  
```  
  
 方法引動過程需要方法的名稱，這個名稱可以是先前範例中的名稱，或是另一個運算式的結果，後面再接著括號和任何方法參數。  如需詳細資訊，請參閱 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。  委派 \(Delegate\) 叫用則需要使用委派的名稱，並用括號括住方法參數。  如需詳細資訊，請參閱 [委派](../../../csharp/programming-guide/delegates/index.md)。  如果方法傳回值，則方法叫用和委派叫用會評估為該方法以產生傳回值。  傳回 void 的方法不可以當做運算式中的值。  
  
## 查詢運算式  
 相同的運算式規則通常會套用至查詢運算式。  如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)。  
  
## Lambda 運算式  
 Lambda 運算式代表「內嵌方法」，沒有名稱但是可以有輸入參數和多個陳述式。  它們廣泛用於 LINQ 以傳遞引數給方法。  Lambda 運算式取決於所使用的內容，會編譯為委派或運算式樹狀架構。  如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
## 運算式樹狀架構  
 運算式樹狀架構可以讓運算式代表資料結構。  它們由 LINQ 提供者廣泛使用以將查詢運算式轉譯為在某些其他內容中有意義的程式碼，例如 SQL 資料庫。  如需詳細資訊，請參閱 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 備註  
 只要運算式辨識出有任何變數、物件屬性或物件索引子 \(Indexer\) 存取，該項目的值都會當做運算式的值使用。  運算式可以放在 C\# 中任何需要值或物件的位置，只要運算式評估的結果為所需的型別即可。  
  
## 精選書籍章節  
 [變數和運算式](完整.嗎？LinkId%20=%20221228) 在 [開頭 2010 視覺化 C\#](完整.嗎？LinkId%20=%20221214)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [類型](../../../csharp/programming-guide/types/index.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)