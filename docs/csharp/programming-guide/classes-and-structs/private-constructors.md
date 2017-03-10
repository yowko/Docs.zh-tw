---
title: "私用建構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 私用建構函式"
  - "私用建構函式 [C#]"
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 私用建構函式 (C# 程式設計手冊)
私用建構函式是一種特殊的執行個體建構函式。  它通常是用在只包含靜態成員的類別 \(Class\) 中。  如果類別具有一個或多個 private \(私用\) 建構函式，而且沒有任何 public \(公用\) 建構函式，則其他類別 \(巢狀類別除外\) 就不能建立這個類別的執行個體。  例如：  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_1.cs)]  
  
 空的建構函式宣告防止自動產生預設建構函式。  請注意，如果您不搭配存取修飾詞 \(Modifier\) 來使用建構函式，則它依然會根據預設值而成為 private \(私用\)。  然而，[private](../../../csharp/language-reference/keywords/private.md) 修飾詞通常用來明確指出無法對該類別執行個體化。  
  
 當類別沒有執行個體欄位或方法 \(例如 <xref:System.Math>\)，或是要呼叫方法取得類別的執行個體時，private \(私用\) 建構函式可以用來防止建立類別的執行個體。  如果類別中的所有方法都是靜態的，請考慮將整個類別變為靜態。  如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
## 範例  
 以下是一個類別使用私用建構函式的範例。  
  
 [!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_2.cs)]  
  
 請注意，如果您將範例中的下列陳述式取消註解，這時將會產生錯誤，因為建構函式會因其保護層級而無法存取：  
  
 [!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)