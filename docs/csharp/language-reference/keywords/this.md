---
title: "this (C# 參考) | Microsoft Docs"
description: this keyword (C# Reference)
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "this"
  - "this_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "this 關鍵字 [C#]"
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# this (C# 參考)
`this` 關鍵字所指的是類別 \(Class\) 的目前執行個體 \(Instance\)，而且也用來當做擴充方法之第一個參數的修飾詞 \(Modifier\)。  
  
> [!NOTE]
>  本文將會討論搭配類別執行個體來使用 `this`。  如需在擴充方法中使用此關鍵字的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
 以下為 `this` 的常見用法：  
  
-   要限定被類似名稱所隱藏的成員，例如：  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   要將物件做為參數傳遞到其他方法，例如：  
  
    ```  
    CalcTax(this);  
    ```  
  
-   要宣告索引子，例如：  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 因為靜態成員函式存在於類別層級，且非物件的一部分，所以不具有 `this` 指標。  在靜態方法中參考 `this` 是錯誤的。  
  
## 範例  
 這個範例使用 `this` 限定被類似名稱隱藏的 `Employee` 類別成員，`name` 和 `alias`。  它也用來將物件傳遞給 `CalcTax` 這個屬於其他類別的方法。  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)