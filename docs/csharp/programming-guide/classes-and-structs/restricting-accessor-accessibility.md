---
title: "限制存取子的存取範圍 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取子 [C#]"
  - "非對稱存取子的存取範圍 [C#]"
  - "索引子 [C#], 唯讀"
  - "屬性 [C#], 唯讀"
  - "唯讀索引子 [C#]"
  - "唯讀屬性 [C#]"
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# 限制存取子的存取範圍 (C# 程式設計手冊)
屬性或索引子的 [get](../../../csharp/language-reference/keywords/get.md) 和 [set](../../../csharp/language-reference/keywords/set.md) 部分稱為「*存取子*」\(Accessor\)。  根據預設，這些存取子具有相同的可視性 \(或存取層級\)：即屬性或索引子所隸屬的層級。  如需詳細資訊，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。  不過，有時候限制對其中一個存取子的存取會很有用。  通常，這會涉及限制 `set` 存取子的存取範圍，但同時讓 `get` 存取子保持為可公用存取。  例如：  
  
 [!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/restricting-accessor-acc_1.cs)]  
  
 在此範例中，名為 `Name` 的屬性會定義 `get` 和 `set` 存取子。  `get` 存取子會接收屬性本身的存取範圍層級 \(在此案例中為 `public`\)，同時套用 [protected](../../../csharp/language-reference/keywords/protected.md) 存取修飾詞至 `set` 存取子本身以明確限制此存取子。  
  
## 在存取子上存取修飾詞的限制  
 在屬性或索引子上使用存取修飾詞必須遵從下列條件：  
  
-   在介面或明確[介面](../../../csharp/language-reference/keywords/interface.md)成員實作上不能使用存取修飾詞。  
  
-   只有當屬性或索引子同時有 `set` 和 `get` 存取子時，您才可使用存取子修飾詞。  在這種情況下，只能在兩個存取子的其中一個使用修飾詞。  
  
-   如果屬性或索引子有 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞，存取子修飾詞必須符合被覆寫存取子的存取子 \(若有的話\)。  
  
-   存取子的存取範圍層級必須比屬性或索引子本身的存取層級更嚴格。  
  
## 覆寫存取子的存取修飾詞  
 當您覆寫屬性或索引子時，覆寫程式碼必須能夠存取覆寫存取子。  同時，屬性\/索引子的存取範圍層級，以及存取子的存取層級，都必須與對應的被覆寫屬性\/索引子和存取子相符。  例如：  
  
 [!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/restricting-accessor-acc_2.cs)]  
  
## 實作介面  
 當您使用存取子實作介面時，存取子不能有存取修飾詞。  不過，如果您使用如 `get` 的存取子實作介面，那麼另一個存取子便可以具有存取修飾詞，如下列範例所示：  
  
 [!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/restricting-accessor-acc_3.cs)]  
  
## 存取子的存取範圍定義域  
 如果您在存取子上使用存取修飾詞，那麼存取子的[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)即由該修飾詞決定。  
  
 如果存取子沒有使用存取修飾詞，則存取子的存取範圍定義域，會由屬性或索引子的存取範圍層級決定。  
  
## 範例  
 下列範例包含三個類別，分別是 `BaseClass`、`DerivedClass` 和 `MainClass`。  `BaseClass` 和其衍生類別都有兩個屬性，分別是 `Name` 和 `Id`。  此範例將示範使用限制存取修飾詞時 \(例如 [protected](../../../csharp/language-reference/keywords/protected.md) 或 [private](../../../csharp/language-reference/keywords/private.md)\)，`BaseClass` 的 `Id` 屬性如何隱藏 `DerivedClass` 的 `Id` 屬性。  因此，當您對這個屬性指派值時，會改為呼叫 `BaseClass` 類別的屬性。  若您將存取修飾詞替換成 [public](../../../csharp/language-reference/keywords/public.md)，則屬性將可供存取。  
  
 這段程式碼同時也將示範限制存取修飾詞 \(例如 `private` 或 `protected`\) 套用在 `DerivedClass` 中 `Name` 屬性的 `set` 存取子時，會使存取子無法存取，並在指派時產生錯誤。  
  
 [!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/restricting-accessor-acc_4.cs)]  
  
## 註解  
 請注意，如果您以 `new public string Id` 取代宣告 `new private string Id`，輸出就會變成：  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)