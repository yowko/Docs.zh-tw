---
title: "物件 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "物件 [C#], 關於物件"
  - "變數 [C#]"
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 物件 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

類別或結構定義就像是藍圖，會指定能夠使用的型別。  物件基本上是記憶體區塊，是根據藍圖加以配置和設定。  程式可能會建立很多相同類別的物件。  物件也稱為執行個體，可以儲存在已命名的變數、陣列或集合中。  用戶端程式碼是使用這些變數呼叫方法並存取物件之公用屬性的程式碼。  在物件導向的語言中 \(例如 C\#\)，一般程式是由彼此以動態方式進行互動的多個物件所組成。  
  
> [!NOTE]
>  靜態 \(Static\) 型別的運作方式與此處所述不同。  如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
## 結構執行個體傳遞至類別執行個體。.  
 由於類別為參考型別，因此類別物件的變數擁有 Managed 堆積上物件位址的參考。  如果將另一個相同型別的物件指派給第一個物件，則這兩個變數都會參考該位址的物件。  本主題稍後會詳細討論這一點。  
  
 類別的執行個體是使用 [new 運算子](../../../csharp/language-reference/keywords/new-operator.md)所建立。  在下列範例中，`Person` 為型別，而 `person1` 和 `person 2` 為該型別的執行個體或物件。  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 由於結構是實值型別 \(Value Type\)，因此結構物件的變數會擁有整個物件的複本。  結構的執行個體也可以使用 `new` 運算子建立，但是並不是必要，如以下範例所示：  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 `p1` 和 `p2` 的記憶體都配置在執行緒堆疊中。  該記憶體會與宣告它的型別或方法一起回收。  這就是在指派時複製結構的原因。  相較之下，配置給類別執行個體的記憶體則會在物件的所有參考都超出範圍時，由 Common Language Runtime 自動回收 \(記憶體回收\)。  因此無法如同在 C\+\+ 中一般，決定性地終結類別物件。  如需 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中記憶體回收的詳細資訊，請參閱[Garbage Collection](../Topic/Garbage%20Collection.md)。  
  
> [!NOTE]
>  Managed 堆積上記憶體的配置和解除配置都會在 Common Language Runtime 中高度最佳化。  大部分情況下，在堆積上配置類別執行個體與在堆疊上配置結構執行個體相較，在效能影響方面並沒有顯著的差異。  
  
## 物件識別對. 實值相等  
 當您比較兩個物件是否相等時，必須先區別您要知道的是這兩個變數是否代表記憶體中的相同物件，或是其中一個或多個欄位的值是否相等。  如果您想要比較值，則必須考慮物件為實值型別 \(結構\) 的執行個體，或是參考型別 \(類別、委派、陣列\) 的執行個體。  
  
-   若要判斷這兩個類別執行個體是否參考記憶體中的相同位置 \(表示擁有相同的「*識別* \(Identity\)」\)，請使用靜態 <xref:System.Object.Equals%2A> 方法  \(<xref:System.Object?displayProperty=fullName> 是所有實值型別和參考型別的隱含基底類別，包括使用者定義的結構和類別\)。  
  
-   若要判斷兩個結構執行個體中的執行個體欄位是否擁有相同的值，請使用 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 方法。  由於所有結構都會隱含繼承自 <xref:System.ValueType?displayProperty=fullName>，因此您可在物件上直接呼叫這個方法，如以下範例所示：  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 `Equals` 的 <xref:System.ValueType?displayProperty=fullName> 實作會使用反映，因為它必須能夠判斷任何結構中擁有的欄位。  建立您自己的結構時，請覆寫 `Equals` 方法以提供您的型別專屬的有效相等演算法。  
  
-   若要判斷兩個類別執行個體中的欄位值是否相等，您或許可以使用 <xref:System.Object.Equals%2A> 方法或 [\=\= 運算子](../../../csharp/language-reference/operators/equality-comparison-operator.md)。  但是，只有在類別覆蓋或多載它們時，才使用它們提供 "相等" 對於該類型物件的涵義的自訂意義。  該類別也可以實作 <xref:System.IEquatable%601>介面或<xref:System.Collections.Generic.IEqualityComparer%601>介面。  兩個介面都提供了方法，可用於測試值的相等性。  當您自己設計會覆寫 `Equals` 的類別時，請務必遵循 [如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) 和 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 中所述的方針。  
  
## 相關章節  
 如需詳細資訊，請參閱下列主題：  
  
-   [類別](../../../standard/base-types/classes.md)  
  
-   [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [事件](../../../csharp/programming-guide/events/index.md)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [繼承](../../../fsharp/language-reference/inheritance.md)   
 [Class \- 類別](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [new 運算子](../../../csharp/language-reference/keywords/new-operator.md)   
 [一般類型系統](../../../standard/base-types/common-type-system.md)