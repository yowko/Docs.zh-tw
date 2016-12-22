---
title: "如何：取得指標變數值 (C# 程式設計手冊) | Microsoft Docs"
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
  - "指標運算式 [C#], 間接取值 (Indirection)"
  - "指標 [C#], * 運算子"
  - "指標 [C#], 間接取值 (Indirection)"
  - "變數 [C#], 指標"
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：取得指標變數值 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用指標間接取值運算子，以取得位於指標所指之位置的變數。  此運算式的格式如下，其中  `p` 為指標型別 \(Pointer Type\)：  
  
```  
*p;  
```  
  
 除了指標型別以外，您無法在任何其他型別的運算式上使用一元間接取值運算子。  也無法將其套用至 [void](../../../csharp/language-reference/keywords/void.md) 指標。  
  
 當您將間接取值運算子套用至 [null](../../../csharp/language-reference/keywords/null.md) 指標時，結果會視實作而定。  
  
## 範例  
 在下列範例中，會使用不同型別的指標存取型別 `char` 的變數。  請注意，由於配置至變數的實體位置可能改變，因此 `theChar` 的位址在每次執行時都會不同。  
  
 [!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
  **Value of theChar \= Z**   
**Address of theChar \= 12F718**  
**Value of pChar \= Z**   
**Value of pInt \= 90**    
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)