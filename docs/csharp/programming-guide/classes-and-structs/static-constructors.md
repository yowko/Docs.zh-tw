---
title: "靜態建構函式 (C# 程式設計手冊) | Microsoft Docs"
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
  - "建構函式 [C#], static"
  - "靜態建構函式 [C#]"
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 靜態建構函式 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

靜態建構函式可以用來初始化任何[靜態](../../../visual-basic/language-reference/modifiers/static.md)資料，或執行只需執行一次的特定動作。  在建立第一個執行個體或參考任何靜態成員之前，會自動呼叫靜態建構函式。  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 靜態建構函式有下列屬性：  
  
-   靜態建構函式並不使用存取修飾詞，也沒有參數。  
  
-   在建立第一個執行個體或參考任何靜態成員之前，就會自動呼叫靜態建構函式以初始化[類別](../../../csharp/language-reference/keywords/class.md)。  
  
-   不能直接呼叫靜態建構函式。  
  
-   使用者無法控制程式中靜態建構函式執行的時間。  
  
-   靜態建構函式通常用在當類別使用記錄檔，而建構函式被用來將項目寫入該檔案。  
  
-   當靜態建構函式可呼叫 `LoadLibrary` 方法時，也可以使用這種建構函式為 Unmanaged 程式碼建立包裝函式類別。  
  
-   如果靜態建構函式擲回例外狀況，執行階段將不會再一次叫用它，且在您的程式執行的應用程式定義域存留期中，型別都將保持未初始化狀態。  
  
## 範例  
 在這個範例中，類別 `Bus` 有一個靜態建構函式。  建立 `Bus` 的第一個執行個體 \(`bus1`\) 時，會呼叫此建構函式來初始化該類別。  這個範例輸出確認靜態建構函式只會執行一次，即使建立了兩個 `Bus` 的執行個體也是如此，並且確認該建構函式會在執行個體建構函式執行之前執行。  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)