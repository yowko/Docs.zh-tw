---
title: "private (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "private_CSharpKeyword"
  - "private"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "private 關鍵字 [C#]"
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# private (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`private` 關鍵字是成員存取修飾詞。  私用存取是最嚴格的存取層級。  Private 成員只能在宣告他們的類別主體或結構主體內存取，如本範例所示：  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 相同主體內的巢狀型別也可以存取這些 private 成員。  
  
 在宣告 private 成員的類別或結構外部參考 private 成員，是編譯時期的錯誤。  
  
 如需 `private` 與其他存取修飾詞的比較，請參閱[存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md) 和[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
## 範例  
 在這個範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。  做為私用成員，它們只能夠由成員方法加以存取。  因此會加入名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。  `name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取   \(如需詳細資訊，請參閱 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)\)。  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)