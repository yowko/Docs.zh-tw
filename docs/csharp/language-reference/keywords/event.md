---
title: "event (C# 參考) | Microsoft Docs"
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
  - "event"
  - "remove"
  - "event_CSharpKeyword"
  - "add"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "event 關鍵字 [C#]"
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# event (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`event` 關鍵字用於在發行者 \(Publisher\) 類別中宣告事件。  
  
## 範例  
 下列範例會示範如何宣告及引發使用 <xref:System.EventHandler> 當做基礎委派型別的事件。  如需取得示範如何使用泛型 <xref:System.EventHandler%601> 委派型別，以及如何訂閱事件並建立事件處理常式方法的完整程式碼範例，請參閱 [如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。  
  
 [!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]  
  
 事件是特殊種類的多點傳送委派，只能從宣告它們的類別或結構 \(Struct\) 內叫用 \(即 Publisher 類別\)。  如果其他類別或結構訂閱該事件，則當 Publisher 類別引發該事件時，會叫用它們的事件處理常式方法。  如需詳細資訊與程式碼範例，請參閱[事件](../../../csharp/programming-guide/events/index.md) 和[委派](../../../visual-basic/reference/command-line-compiler/index.md)。  
  
 事件可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected` `internal`。  這些存取修飾詞將定義類別使用者如何存取事件。  如需詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
## 關鍵字和事件  
 下列關鍵字會套用到事件上。  
  
|Keyword|描述|如需詳細資訊|  
|-------------|--------|------------|  
|[static](../../../visual-basic/language-reference/modifiers/static.md)|讓呼叫端可以隨時使用該事件，即使沒有類別的執行個體 \(Instance\) 也一樣。|[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|可讓衍生類別 \(Derived Class\) 使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字覆寫事件行為。|[繼承](../../../fsharp/language-reference/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|指定對於衍生類別而言，它不再是虛擬。||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|編譯器將不會產生 `add` 和 `remove` 事件存取子 \(Accessor\) 區塊，因此，衍生類別必須提供自己的實作 \(Implementation\)。||  
  
 您可以使用 [static](../../../visual-basic/language-reference/modifiers/static.md) 關鍵字，將事件宣告為靜態事件。  這讓呼叫端即使沒有類別的執行個體，也可以隨時使用事件。  如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 您可以使用 [virtual](../../../csharp/language-reference/keywords/virtual.md) 關鍵字，將事件標記為虛擬事件。  如此一來，衍生類別便可以使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字來覆寫事件行為。  如需詳細資訊，請參閱 [繼承](../../../fsharp/language-reference/inheritance.md)。  覆寫虛擬事件的事件也可以是 [sealed](../../../csharp/language-reference/keywords/sealed.md) 事件，這樣便會指定該事件對衍生類別而言將不再是虛擬的。  最後，事件可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)，這表示編譯器將不會產生 `add` 和 `remove` 事件存取子區塊。  因此，衍生類別必須提供自己的實作。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [add](../../../csharp/language-reference/keywords/add.md)   
 [移除](../../../csharp/language-reference/keywords/remove.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [如何：組合委派 \(多點傳送委派\)](../Topic/How%20to:%20Combine%20Delegates%20\(Multicast%20Delegates\)\(C%23%20Programming%20Guide\).md)