---
title: "base (C# 參考) | Microsoft Docs"
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
  - "base"
  - "BaseClass.BaseClass"
  - "base_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "base 關鍵字 [C#]"
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# base (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`base` 關鍵字用於存取衍生類別中的基底類別 \(Base Class\) 成員：  
  
-   呼叫一個已被其他方法覆寫的基底類別中方法。  
  
-   指定建立衍生類別執行個體 \(Instance\) 時，所要呼叫的基底類別建構函式。  
  
 基底類別只允許在建構函式、執行個體方法 \(Instance Method\) 或執行個體屬性存取子中存取。  
  
 在靜態方法中使用 `base` 關鍵字是錯誤的。  
  
 所存取的基底類別就是在類別宣告中指定的基底類別。  例如，如果您指定 `class ClassB : ClassA`，無論 ClassA 的基底類別為何，都可以從 ClassB 存取 ClassA 的成員。  
  
## 範例  
 於此例中，基底類別 `Person` 和衍生類別 `Employee` 都有一個名為 `Getinfo` 的方法。  使用 `base` 關鍵字，就可以從衍生類別中呼叫基底類別的 `Getinfo` 方法。  
  
 [!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]  
  
 如需其他範例，請參閱 [new](../../../csharp/language-reference/keywords/new.md)、[virtual](../../../csharp/language-reference/keywords/virtual.md) 和 [override](../../../csharp/language-reference/keywords/override.md)。  
  
## 範例  
 此範例顯示了在建立衍生類別的執行個體時，要如何指定被呼叫的基底類別建構函式。  
  
 [!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)