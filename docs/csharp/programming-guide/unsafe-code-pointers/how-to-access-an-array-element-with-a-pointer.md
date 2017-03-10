---
title: "如何：使用指標存取陣列元素 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "指標 [C#], 陣列存取"
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：使用指標存取陣列元素 (C# 程式設計手冊)
在 unsafe 內容中，您可以使用指標項目存取方式來存取記憶體內的某個項目，如下列範例所示：  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 方括號內的運算式必須可隱含轉換為 `int`、`uint`、`long` 或 `ulong`。  p\[e\] 運算相當於 \*\(p\+e\)。  指標項目存取功能也與 C 和 C\+\+ 一樣，都無法檢查超出範圍的錯誤。  
  
## 範例  
 在下面的範例中，會將 123 個記憶體位置配置到字元陣列 `charPointer` 中。  這個陣列會用來顯示兩個 [for](../../../csharp/language-reference/keywords/for.md) 迴圈中的小寫字母和大寫字母。  
  
 請注意，`charPointer[i]` 運算式相當於 `*(charPointer + i)` 運算式，使用這兩個運算式的任何一個都會得到相同的結果。  
  
 [!code-cs[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers2.cs#11)]  
  
 [!code-cs[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#12)]  
  
  **大寫字母：**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**小寫字母：**  
**abcdefghijklmnopqrstuvwxyz**   
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)