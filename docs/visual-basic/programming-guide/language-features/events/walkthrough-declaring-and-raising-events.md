---
title: "Walkthrough: Declaring and Raising Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations, events"
  - "events [Visual Basic], walkthroughs"
  - "declaring events, walkthroughs"
  - "events [Visual Basic], declaring"
  - "events [Visual Basic], raising"
  - "raising events, walkthroughs"
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Walkthrough: Declaring and Raising Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本逐步解說會示範如何宣告和引發名為 `Widget` 之類別的事件。  在您完成步驟後，可能會想要閱讀相關主題，請參閱[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，這個主題會顯示如何使用 `Widget` 物件的事件，提供應用程式的狀態資訊。  
  
## Widget 類別  
 假設此刻您有一個 `Widget` 類別。  這個 `Widget` 類別具有需花長時間執行的方法，而您希望應用程式能夠建立某種完成指示器 \(Indicator\)。  
  
 當然可以讓 `Widget` 物件顯示完成百分比對話方塊，但之後在每個使用 `Widget` 類別的專案中，您都會停在那個對話方塊上動彈不得。  除非該物件的目的就是在管理表單或對話方塊，否則良好的物件設計原則應該要能夠讓使用物件的應用程式處理使用者介面。  
  
 `Widget` 的目的是要執行其他工作，所以最好加入 `PercentDone` 事件，讓呼叫 `Widget` 方法的程序處理該事件並顯示狀態更新。  `PercentDone` 事件也可以提供取消工作的機制。  
  
#### 若要建立此主題的程式碼範例  
  
1.  開啟新的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows 應用程式專案，並建立名為 `Form1` 的表單。  
  
2.  將兩個按鈕和一個標籤 \(Label\) 加入至 `Form1`。  
  
3.  如下表所示，為物件命名。  
  
    |物件|屬性|設定|  
    |--------|--------|--------|  
    |`Button1`|`Text`|開始工作|  
    |`Button2`|`Text`|Cancel|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  從 \[**專案**\] 功能表，選擇 \[**加入類別**\] 將名為 `Widget.vb` 的類別加入至專案。  
  
#### 若要宣告 Widget 類別的事件  
  
-   使用 `Event` 關鍵字宣告 `Widget` 類別中的事件。  請注意，事件可以具有 `ByVal` 和 `ByRef` 引數，如 `Widget` 的 `PercentDone` 事件所示：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Widget.vb#1)]  
  
 當呼叫物件收到 `PercentDone` 事件時，`Percent` 引數會包含已完成工作的百分比。  可以將 `Cancel` 引數設定為 `True`，取消引發事件的方法。  
  
> [!NOTE]
>  宣告事件引數的方式就如同您宣告程序的引數一樣，除了以下不同之外：事件不得有 `Optional` 或 `ParamArray` 引數，以及事件沒有傳回值。  
  
 `Widget` 類別的 `LongTask` 方法會引發 `PercentDone` 事件。  `LongTask` 採用兩個引數：方法假裝進行工作的時間長度，以及在 `LongTask` 停頓之前引發 `PercentDone` 事件的最短時間間隔。  
  
#### 若要引發 PercentDone 事件  
  
1.  若要簡化對此類別所使用之 `Timer` 屬性的存取，可以在 `Class Widget` 陳述式上方的類別模組宣告區段最上方，加入一個 `Imports` 陳述式。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Widget.vb#2)]  
  
2.  將下列程式碼加入至 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Widget.vb#3)]  
  
 當應用程式呼叫 `LongTask` 方法時，`Widget` 類別會每隔 `MinimumInterval` 秒引發 `PercentDone` 事件。  當事件傳回時，`LongTask` 會檢查 `Cancel` 引數是否設為 `True`。  
  
 此處需要提出一些免責聲明。  為容易了解，`LongTask` 程序假設您事先知道工作將花費的時間。  這種情況幾乎很少發生。  將工作分割為數個大小相同的區塊 \(Chunk\) 是相當困難的，且通常對使用者而言最重要的是他們獲知事情發生之前所經過的時間量。  
  
 您可能發現本範例還有另一個瑕疵。  `Timer` 屬性會傳回從午夜起算的秒數，因此，如果是在午夜之前啟動，應用程式就會停住不動。  較謹慎地計算時間的方法是設定界限條件，例如將這個情況納入考慮，或是使用像 `Now` 這類屬性以避免問題的發生。  
  
 現在 `Widget` 類別可以引發事件，您可以移到下一個逐步解說。  [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)會示範如何使用 `WithEvents`，建立事件處理常式與 `PercentDone` 事件的關聯。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)