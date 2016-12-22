---
title: "泛型委派 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "委派 [C#], 泛型"
  - "泛型 [C#], 委派"
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 泛型委派 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[delegate](../../../csharp/language-reference/keywords/delegate.md) 能夠定義自己的型別參數。  如下列程式碼範例所示，參考泛型委派 \(Delegate\) 的程式碼可以指定型別引數以建立封閉式建構型別，就像在產生泛型類別或呼叫泛型方法時一樣：  
  
 [!CODE [csProgGuideGenerics#36](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#36)]  
  
 C\# 2.0 版有一項適用於具象和泛型委派型別，稱為方法群組轉換的新功能，能夠讓您使用下列簡化的語法撰寫上一行程式碼：  
  
 [!CODE [csProgGuideGenerics#37](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#37)]  
  
 在泛型類別中定義的委派可像類別方法一樣，使用泛型類別型別參數。  
  
 [!CODE [csProgGuideGenerics#38](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#38)]  
  
 參考委派的程式碼必須指定包含類別的型別引數，如下所示：  
  
 [!CODE [csProgGuideGenerics#39](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#39)]  
  
 泛型委派對於根據一般設計模式定義事件特別有用，因為寄件人引數可以是強型別並且不再需要從 <xref:System.Object> 轉換。  
  
 [!CODE [csProgGuideGenerics#40](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideGenerics#40)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [泛型方法](../../../csharp/programming-guide/generics/generic-methods.md)   
 [泛型類別](../../../csharp/programming-guide/generics/generic-classes.md)   
 [泛型介面](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [委派](../../../visual-basic/reference/command-line-compiler/index.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)