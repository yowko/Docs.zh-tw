---
title: "如何：在衍生類別中引發基底類別事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "事件 [C#], 衍生類別中"
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 如何：在衍生類別中引發基底類別事件 (C# 程式設計手冊)
下列的簡單範例會示範在基底類別 \(Base Class\) 內宣告事件的標準方式，讓事件也可以從衍生類別 \(Derived Class\) 中引發。  這個模式會在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別庫 \(Class Library\) 的 Windows Form 類別中廣泛使用。  
  
 當您建立可當做其他類別之基底類別的類別時，您應該考量一項事實：事件是一種委派 \(Delegate\) 的特殊型別，只能從宣告事件的類別中予以叫用 \(Invoke\)。  衍生類別無法直接叫用在基底類別中宣告的事件。  雖然有時您可能會想要使用只能由基底類別所引發的事件，但是在多數情形下，您應該啟用衍生類別來叫用基底類別事件。  若要這樣做，您可以在包裝事件的基底類別內建立保護的 \(Protected\) 的叫用方法；  藉由呼叫或覆寫這個叫用方法，衍生類別便能夠間接地叫用該事件。  
  
> [!NOTE]
>  請勿在基底類別中宣告虛擬事件，以及進而在衍生類別中覆寫它們。  C\#編譯器會控制代碼這些正確而且衍生的事件訂閱者 」 實際上訂閱基底類別事件是否發生無法預期。  
  
## 範例  
 [!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/csharp/how-to-raise-base-class-_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [委派](../../../csharp/programming-guide/delegates/index.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [在 Windows Form 中建立事件處理常式](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)