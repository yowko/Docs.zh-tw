---
title: "partial (類型) (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "partialtype"
  - "partialtype_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "部分類型 [C#]"
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# partial (類型) (C# 參考)
部分型別定義允許類別、結構 \(Struct\) 或介面等的定義分割成多個檔案。  
  
 在 File1.cs 中：  
  
 [!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 在 File2.cs 中，下列宣告：  
  
 [!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## 備註  
 當使用大型專案或自動產生的程式碼 \(如 [Windows Forms Designer](http://msdn.microsoft.com/zh-tw/3c3d61f8-f36c-4d41-b9c3-398376fabb15)所提供的程式碼\) 時，將類別、結構 \(Struct\) 或介面型別 \(Interface Type\) 分割成數個檔案可能會非常實用。  部分型別可能包含[部分方法](../../../csharp/language-reference/keywords/partial-method.md)。  如需詳細資訊，請參閱 [部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)