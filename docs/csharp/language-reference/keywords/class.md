---
title: "類別 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "class_CSharpKeyword"
  - "class"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "class 關鍵字 [C#]"
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 類別 (C# 參考)
類別是使用 `class` 關鍵字宣告，如下列範例所示：  
  
```  
  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## 備註  
 只有單一繼承在 C\# 中啟用。  換句話說，類別只能從一個基底類別繼承實作。  但是，類別可以實作一個以上的介面。  下表顯示類別繼承和介面實作的範例：  
  
|繼承|範例|  
|--------|--------|  
|None|`class ClassA { }`|  
|Single|`class DerivedClass: BaseClass { }`|  
|無繼承，實作兩個介面|`class ImplClass: IFace1, IFace2 { }`|  
|單一繼承，實作一個介面|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 您可以直接在命名空間中宣告的類別，而不是在其他類別內，可能是 [公用](../../../csharp/language-reference/keywords/public.md) 或 [內部](../../../csharp/language-reference/keywords/internal.md)。  類別預設是 `internal` 。  
  
 類別成員，包括巢狀類別，可以是 `protected internal`、 [公用](../../../csharp/language-reference/keywords/public.md)、 [保護](../../../csharp/language-reference/keywords/protected.md)、 [內部](../../../csharp/language-reference/keywords/internal.md)或 [私用](../../../csharp/language-reference/keywords/private.md)。  預設成員是 [私用](../../../csharp/language-reference/keywords/private.md) 。  
  
 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 您可以宣告具有型別參數的泛型類別。  如需詳細資訊，請參閱 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)。  
  
 類別可以包含下列成員的宣告：  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [索引子](../../../csharp/programming-guide/indexers/index.md)  
  
-   [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
-   [委派](../../../csharp/programming-guide/delegates/index.md)  
  
-   [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [介面](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## 範例  
 下列範例示範類別欄位、建構函式和方法的宣告。  它也示範物件執行個體化 \(Instantiation\) 和列印執行個體資料。  在這個範例裡，宣告了兩個類別，其中 `Child` 類別包含兩個私用 \(Private\) 欄位 \(`name` 和 `age`\) 和兩個公用 \(Public\) 方法。  第二個類別 `StringTest` 是用來包含 `Main`。  
  
 [!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/csharp/class_1.cs)]  
  
## 註解  
 請注意，在上述範例裡，私用欄位 \(`name` 和 `age`\) 只能經由 `Child` 類別的公用方法來存取。  例如，使用以下陳述式時，您就不能從 `Main` 方法中輸出小孩的名字：  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 只有在 `Main` 為類別成員的情況下，才可以從 `Main` 存取 `Child` 的私用成員。  
  
 型別在類別內宣告，而不使用存取修飾詞會預設值為 `private`，因此，在這個範例中的資料成員會是 `private` ，如果移除關鍵字。  
  
 最後，請注意對於使用預設建構函式 \(`child3`\) 建立的物件，年齡欄位預設會初始化為零。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)