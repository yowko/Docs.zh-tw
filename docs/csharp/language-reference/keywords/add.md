---
title: "add (C# 參考) | Microsoft Docs"
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
  - "add_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "加入事件存取子 [C#]"
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# add (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`add` 內容關鍵字可用來定義當用戶端程式碼訂閱您的[事件](../../../csharp/language-reference/keywords/event.md)時，所叫用 \(Invoke\) 的自訂事件存取子 \(Accessor\)。  如果您提供自訂 `add` 存取子，則也必須提供 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子。  
  
## 範例  
 下列範例說明具有自訂 `add` 和 [remove](../../../csharp/language-reference/keywords/remove.md) 存取子的事件。  如需完整的範例，請參閱 [如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)。  
  
 [!CODE [csrefKeywordsContextual#15](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsContextual#15)]  
  
 一般而言，您不需要提供自訂的事件存取子。  在大部分情況下，編譯器 \(Compiler\) 在您宣告事件時自動產生的存取子已經足夠。  
  
## 請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)