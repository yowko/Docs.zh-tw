---
title: "namespace (C# 參考) | Microsoft Docs"
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
  - "namespace_CSharpKeyword"
  - "namespace"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "namespace 關鍵字 [C#]"
  - "範圍 [C#]"
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# namespace (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`namespace` 關鍵字是用來宣告包含一組相關物件的範圍。  您可以使用命名空間組織程式碼項目並建立全域唯一型別。  
  
 [!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## 備註  
 在命名空間裡，您可以宣告一個或多個下列型別：  
  
-   另一個命名空間  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [Delegate \- 委派](../../../csharp/language-reference/keywords/delegate.md)  
  
 不論您是否在 C\# 原始程式檔 \(Source File\) 內明確宣告命名空間，編譯器都會加入預設的命名空間。  這種未命名的命名空間 \(有時稱為全域命名空間\) 存在於每一個檔案中。  全域命名空間裡的任何一個識別項都可用於已命名的命名空間。  
  
 命名空間隱含公用存取而且無法更改。  如需命名空間中可指派給項目的存取修飾詞之相關討論，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 命名空間可以定義在兩個或多重宣告裡。  例如，下列範例會將兩個類別定義為 `MyCompany` 命名空間的一部分：  
  
 [!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## 範例  
 下列範例顯示如何在巢狀命名空間裡呼叫靜態方法。  
  
 [!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## 如需詳細資訊  
 如需使用命名空間的詳細資訊，請參閱下列主題：  
  
-   [命名空間](../../../visual-basic/reference/command-line-compiler/index.md)  
  
-   [使用命名空間](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [使用](../../../csharp/language-reference/keywords/using.md)