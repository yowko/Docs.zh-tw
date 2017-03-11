---
title: "使用可為 Null 的類型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "可為 null 的類型 [C#], 關於可為 null 的類型"
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 使用可為 Null 的類型 (C# 程式設計手冊)
可為 Null 的型別可以代表基礎型別的所有值，也可以代表另一個 [null](../../../csharp/language-reference/keywords/null.md) 值。  您可以使用下列其中一種方法宣告可為 Null 的型別：  
  
 `System.Nullable<T> variable`  
  
 \-或\-  
  
 `T?  variable`  
  
 `T` 是可為 Null 之型別的基礎型別。  `T` 可以是任何實值型別，包括 `struct` ，它不能是參考型別。  
  
 何時該使用可為 null 的型別，可舉一般的布林變數為例，這種變數有兩個可能的值：true 和 false。  但沒有值可以代表「未定義」。  在許多設計程式的應用程式中，特別是資料庫互動的程式，變數有可能是以未定義的狀態存在。  例如，資料庫中的某個欄位可能包含 true 或 false 值，但也可能不包含任何值。  同樣地，參考型別可以設定為 `null` 表示其並非初始化的。  
  
 由於這些值的性質不同，就需要在程式上另做設計，包括使用其他變數存放狀態資訊、使用特殊值等等。  可為 null 的型別修飾詞能夠讓 C\# 建立表示未定義之值的實值型別 \(Value Type\) 變數。  
  
## 可為 Null 的型別範例  
 任何實值型別都可以當做可為 null 的型別的基礎，  例如：  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_1.cs)]  
  
## 可為 Null 的型別成員  
 可為 null 之型別的每個執行個體 \(Instance\) 有兩個公用唯讀屬性：  
  
-   `HasValue`  
  
     `HasValue` 屬於 `bool` 型別。  當變數包含非 null 的值時，該屬性會設定為 `true`。  
  
-   `Value`  
  
     `Value` 的型別與基礎型別相同。  如果 `HasValue` 為 `true`，`Value` 會包含有意義的值。  如果 `HasValue` 為 `false`，存取 `Value` 將會擲回 <xref:System.InvalidOperationException>。  
  
 在這個範例中，會先使用 `HasValue` 成員測試變數是否包含值，然後才會嘗試顯示該值。  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_2.cs)]  
  
 也可使用下列範例完成測試值的作業：  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_3.cs)]  
  
## 明確轉換  
 您可以明確使用轉型或使用 `Value` 屬性，將可為 null 的型別轉換成標準型別。  例如：  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_4.cs)]  
  
 如果在兩資料型別之間定義了使用者定義轉換，這兩個資料型別的可為 Null 的型別版本也可以使用該轉換。  
  
## 隱含轉換  
 可為 Null 的型別 \(Nullable Type\) 可使用 `null` 關鍵字設為 null，如下列範例所示：  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_5.cs)]  
  
 從一般型別轉換成可為 null 的型別是隱含轉換。  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_6.cs)]  
  
## 運算子  
 可為 Null 的型別也可以使用預先定義的一元和二元運算子，以及現有實值型別的任何使用者定義運算子。  如果運算元都是 null，這些運算子就會產生 null 值，否則運算子會使用所包含的值計算結果。  例如：  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_7.cs)]  
  
 使用可為 Null 的型別執行比較時，如果其中一個可為 Null 的型別值為 Null，但是其他的值不為 Null，則除了 `!=` \(不等於\) 以外，其他所有比較都會評估為 `false`。  此時，請勿因為特定的比較傳回 `false`，因而認定其他相反的情況就會傳回 `true`。  在下列範例中，10 不會大於、小於或等於 Null。  只有 `num1 != num2` 評估為 `true`。  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_8.cs)]  
  
 兩個皆為 Null 之可為 Null 的型別進行相等比較時，評估結果將會是 `true`。  
  
## ?? 運算子  
 `??` 運算子會定義當可為 null 的型別指派給不可為 null 的型別時，要傳回的預設值。  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_9.cs)]  
  
 這個運算子也可以搭配多個可為 null 的型別使用。  例如：  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/using-nullable-types_10.cs)]  
  
## bool?type  
 可為 null 的 `bool?` 型別可包含三種不同的值：[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 和 [null](../../../csharp/language-reference/keywords/null.md)。  如需從 bool? 轉換為   bool 的詳細資訊，請參閱 [如何：從 bool? 安全轉型到 bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)。  
  
 可為 Null 的布林值就像 SQL 中使用的布林值變數型別。  若要確保 `&` 所產生的結果和  `|` 運算子與 SQL 中三個值的布林型別一致，提供下列預先定義的運算子：  
  
 `bool?  operator &(bool?  x, bool?  y)`  
  
 `bool?  operator |(bool?  x, bool?  y)`  
  
 這些運算子的結果列於下表：  
  
|X|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)   
 [Box 處理可為 Null 的類型](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)