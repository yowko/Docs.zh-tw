---
title: "事件 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "類別 [C#], 事件"
  - "C# 語言, 事件"
  - "事件 [C#]"
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 事件 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

事件可讓[類別](../../../csharp/language-reference/keywords/class.md)或物件在某些相關的事情發生時，告知其他類別或物件。 傳送 \(或*「引發」*\(raise\)\) 事件的類別稱為*「發行者」*\(publisher\)，而接收 \(或*「處理」*\(handle\)\) 事件的類別則稱為*「訂閱者」*\(subscriber\)。  
  
 在典型的 C\# Windows Forms 或 Web 應用程式中，您可訂閱由控制項 \(如按鈕和清單方塊\) 引發的事件。 您可以使用 [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] 整合式開發環境 \(IDE\) 來瀏覽控制項發行的事件，並選擇您想要處理的事件。 IDE 會自動新增空的事件處理常式方法和程式碼，以訂閱該事件。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。  
  
## 事件概觀  
 事件有下列屬性：  
  
-   發行者會判斷引發事件的時間，而訂閱者則決定要採取什麼動作來回應該事件。  
  
-   一個事件可以有多個訂閱者， 而訂閱者可以處理來自多個發行者的多個事件。  
  
-   沒有訂閱者的事件永遠不會被引發。  
  
-   事件通常用於對使用者的動作 \(例如在圖形化使用者介面內按一下按鈕或選取功能表\) 發出信號。  
  
-   當某事件擁有多個訂閱者時，便會在事件引發的同時叫用事件處理常式。 若要以非同步方式叫用事件，請參閱 [Calling Synchronous Methods Asynchronously](../Topic/Calling%20Synchronous%20Methods%20Asynchronously.md)。  
  
-   在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 類別庫中，事件會以 <xref:System.EventHandler> 委派和 <xref:System.EventArgs> 基底類別為基礎。  
  
## 相關章節  
 如需詳細資訊，請參閱:  
  
-   [如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [如何：在衍生類別中引發基底類別事件](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [執行緒同步處理](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [如何：使用字典儲存事件執行個體](../Topic/How%20to:%20Use%20a%20Dictionary%20to%20Store%20Event%20Instances%20\(C%23%20Programming%20Guide\).md)  
  
-   [如何：實作自訂事件存取子](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 精選書籍章節  
 [C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369) \(C\# 3.0 Cookbook 第三版：250 個以上 C\# 3.0 程式設計人員適用的方案\) 中的[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) \(委派、事件和 Lambda 運算式\)  
  
 [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412) \(了解 C\# 3.0：掌握 C\# 3.0 的基本概念\) 中的 [Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) \(委派及事件\)  
  
## 請參閱  
 <xref:System.EventHandler>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [委派](../../../visual-basic/reference/command-line-compiler/index.md)   
 [在 Windows Form 中建立事件處理常式](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../Topic/Multithreaded%20Programming%20with%20the%20Event-based%20Asynchronous%20Pattern.md)