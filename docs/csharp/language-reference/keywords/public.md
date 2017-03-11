---
title: "public (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "public"
  - "public_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "public 關鍵字 [C#]"
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# public (C# 參考)
`public` 關鍵字是型別和型別成員的存取修飾詞。  公用存取是最寬鬆的存取層級。  存取 public 成員時並沒有限制，如本範例所示：  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)以及 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。  
  
## 範例  
 下列範例中，宣告兩個類別，`PointTest` 和 `MainClass`。  `PointTest` 的公用成員 `x` 與 `y` 可直接由 `MainClass` 存取。  
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#13)]  
  
 如果您將 `public` 存取層級更改為 [private](../../../csharp/language-reference/keywords/private.md) 或 [protected](../../../csharp/language-reference/keywords/protected.md)，就會得到下列錯誤訊息：  
  
 'PointTest.y' 的保護層級導致無法對其進行存取。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)