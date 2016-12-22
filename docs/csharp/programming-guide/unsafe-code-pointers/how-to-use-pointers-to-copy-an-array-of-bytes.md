---
title: "如何：使用指標複製位元組陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "陣列 [C#], byte"
  - "位元組陣列 [C#]"
  - "指標 [C#], 複製位元組"
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：使用指標複製位元組陣列 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下列範例會使用指標在陣列之間複製位元組。  
  
 這個範例使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，可讓您在 `Copy` 方法中使用指標。  [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式是用於宣告指向來源和目標陣列的指標。  這會「*固定*」\(Pin\) 來源和目的地陣列在記憶體中的位置，如此一來就不會因記憶體回收而移動。  陣列的記憶體區塊會在 `fixed` 區塊完成時解除固定狀態。  由於這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，因此必須使用 **\/unsafe** 編譯器選項進行編譯。  若要在 Visual Studio 中設定選項，以滑鼠右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  在 \[**建置**\] 索引標籤上，選取 \[**容許 Unsafe 程式碼**\]。  
  
## 範例  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [\/unsafe \(Enable Unsafe Mode\)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)