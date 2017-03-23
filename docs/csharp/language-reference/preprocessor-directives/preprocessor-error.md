---
title: "#error (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#error"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#error 指示詞 [C#]"
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# #error (C# 參考)
`#error` 可讓您從程式碼中的特定位置產生錯誤。  例如：  
  
```  
#error Deprecated code in this method.  
```  
  
## 備註  
 `#error` 通常使用在條件式指示詞中。  
  
 不過也有可能使用 [\#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 來產生使用者定義警告。  
  
## 範例  
  
```  
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)