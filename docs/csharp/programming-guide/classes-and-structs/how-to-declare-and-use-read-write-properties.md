---
title: "如何：宣告及使用讀寫屬性 (C# 程式設計指南) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "get 存取子 [C#]，宣告屬性"
  - "set 存取子 [C#]"
  - "屬性 [C#]，宣告"
  - "讀取/寫入屬性 [C#]"
  - "存取子 [C#]，宣告屬性方式"
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 如何：宣告及使用讀寫屬性 (C# 程式設計指南)
屬性提供公用資料成員的便利，同時免除了未受保護、未受控制和未經驗證即存取物件資料帶來的風險。  這是因為有「*存取子*」\(Accessor\) 的關係：這是一種特殊方法，用來指派及擷取基礎資料成員的值。  [set](../../../csharp/language-reference/keywords/set.md) 存取子可讓資料成員獲得指派，而 [get](../../../csharp/language-reference/keywords/get.md) 存取子則會擷取資料成員值。  
  
 在下面的範例中，`Person` 類別有兩個屬性，分別是 `Name` \(string\) 和 `Age` \(int\)。  兩個屬性都提供了 `get` 和 `set` 存取子，所以被視為讀取\/寫入屬性。  
  
## 範例  
 [!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## 穩固程式設計  
 在先前的範例中，`Name` 和 `Age` 屬性為 [public](../../../csharp/language-reference/keywords/public.md)，且同時包含 `get` 和 `set` 存取子。  這可讓任何物件讀取和寫入這些屬性。  然而，有時候最好排除其中一個存取子。  例如，省略 `set` 存取子，讓屬性成為唯讀：  
  
 [!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 或者，您可以將其中一個存取子公開為公用，但讓另一個成為私用或保護的。  如需詳細資訊，請參閱[非對稱存取子存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
 屬性一經宣告，它們可以用於做為是否為類別的欄位。  當同時取得和設定屬性值時，此允許一個非常自然的語法，如下列陳述式所示：  
  
 [!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 請注意，屬性的 `set` 方法可以使用特殊的 `value` 變數。  例如，這個變數包含使用者指定的數值：  
  
 [!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 注意 `Person` 物件中遞增 `Age` 屬性的簡潔語法：  
  
 [!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 如果個別的 `set` 和 `get` 方法用於建構屬性，那麼作用相當的程式碼可能會看起來像這樣：  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 這個範例會覆寫 `ToString` 方法：  
  
 [!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 請注意，程式中並不是明確使用 `ToString`，  而是預設會由 `WriteLine` 呼叫來叫用。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)