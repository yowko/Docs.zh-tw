---
title: "一維陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "陣列 [C#], 一維"
  - "一維陣列 [C#]"
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 一維陣列 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以宣告具有五個整數的一維陣列，如下列範例所示：  
  
 [!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 這個陣列包含從 `array[0]` 到 `array[4]` 的元素。  [new](../../../csharp/language-reference/keywords/new.md) 運算子是用來建立陣列，並將陣列項目初始化為其預設值。  在這個範例中，所有陣列元素都初始化為零。  
  
 儲存字串元素的陣列也可以同樣的方式宣告。  例如：  
  
 [!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## 陣列初始化  
 陣列可在宣告時進行初始化，在這種情況下不需要指定陣序規範，因為它已由初始化清單中的元素數目提供。  例如：  
  
 [!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 字串陣列可以同樣的方式進行初始化。  以下是字串陣列的宣告，其中每個陣列元素都是以日期名稱初始化：  
  
 [!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 當您在宣告時初始化陣列，可以使用下列捷徑：  
  
 [!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 可以不初始化就宣告陣列變數，但當您將陣列指派給這個變數時，就必須使用 `new` 運算子。  例如：  
  
 [!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C\# 3.0 引進隱含型別陣列。  如需詳細資訊，請參閱 [隱含類型陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。  
  
## 實值型別和參考具型別陣列  
 以下列陣列宣告為例：  
  
 [!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 這個陳述式的結果會視 `SomeType` 是實值型別或參考型別而定。  如果是實值型別，陳述式就會建立有 10 個項目的陣列，其中每個項目都有 `SomeType` 型別。  如果 `SomeType` 是參考型別，則陳述式會建立 10 個元素的陣列，每個元素都會初始化 Null 參考。  
  
 如需參考型別和實值型別的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。  
  
## 請參閱  
 <xref:System.Array>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)