---
title: "如何：使用規則運算式搜尋字串 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "搜尋字串 [C#]"
  - "字串 [C#]，使用 RegEx 搜尋"
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 如何：使用規則運算式搜尋字串 (C# 程式設計手冊)
<xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> 類別可用來搜尋字串。  這些搜尋的複雜度範圍，可能介於非常簡單到充分使用規則運算式之間。  下列是使用 <xref:System.Text.RegularExpressions.Regex> 類別搜尋字串的兩個範例。  如需詳細資訊，請參閱[.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)。  
  
## 範例  
 下列程式碼是主控台應用程式，會在陣列中執行不區分大小寫的簡單字串搜尋。  <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> 靜態方法會執行搜尋 \(提供要搜尋的字串及包含搜尋模式的字串\)。  在上述情形中，會使用第三個引數表示應該忽略大小寫。  如需詳細資訊，請參閱<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>。  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## 範例  
 下列程式碼是一個主控台應用程式，會使用規則運算式驗證陣列中每個字串格式。  驗證需要每個字串都使用電話號碼的格式，其中三組數字之間都以破折號分隔，前兩組包含三個數字而第三組包含四個數字。  這可以使用規則運算式 `^\\d{3}-\\d{3}-\\d{4}$` 來完成。  如需詳細資訊，請參閱[規則運算式語言 \- 快速參考](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)。  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## 請參閱  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [.NET Framework 規則運算式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [規則運算式語言 \- 快速參考](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)