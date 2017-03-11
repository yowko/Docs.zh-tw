---
title: "Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "02/25/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "events [Visual Basic], about events"
  - "events [Visual Basic]"
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

雖然您可能會將 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] 專案以視覺化方式顯示為會依序執行的一系列程序，但實際上，大部分程式都是以事件驅動 \(表示執行流程是由稱為「*事件*」\(Event\) 的外部發生情況所決定\)。  
  
 事件是通知應用程式有重要事情發生的信號。  例如，當使用者按一下表單上的控制項時，表單會引發 `Click` 事件並呼叫處理事件的程序。  事件也允許個別工作進行通訊。  例如，假設您的應用程式在主應用程式外個別執行排序工作。  如果使用者取消排序，您的應用程式可傳送取消事件來指示排序過程停止執行。  
  
## 事件詞彙和概念  
 本章節將說明在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中事件所使用的詞彙和概念。  
  
### 宣告事件  
 您使用 `Event` 關鍵字在類別、結構、模組和介面內宣告事件，如以下範例所示：  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#24)]  
  
### 引發事件  
 事件就像是宣告發生重大事情的訊息。  播送訊息的動作稱為「*引發*」\(Raise\) 事件。  在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，您可以使用 `RaiseEvent` 陳述式 \(Statement\) 引發事件，如以下範例所示：  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#25)]  
  
 事件必須在宣告於其中的類別、模組或結構的範圍內引發。  例如，衍生類別無法引發繼承自基底類別的事件。  
  
### 事件傳送者  
 任何能夠引發事件的物件就是「*事件發送者*」\(Event Sender\)，也稱為「*事件來源*」\(Event Source\)。  表單、控制項和使用者定義物件是事件傳送者的幾個範例。  
  
### 事件處理常式  
 「*事件處理常式*」\(Event Handler\) 是在發生對應事件時所呼叫的程序。  您可以使用任何具有相符簽章 \(Signature\) 的有效副程式當做事件處理常式。  但您不能將函式當做事件處理常式來使用，因為它無法將值傳回事件的來源。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將標準命名慣例用於事件處理常式，此慣例結合事件發送者的名稱、底線和事件的名稱。  例如，名為 `button1` 之按鈕的 `Click` 事件會命名為 `Sub button1_Click`。  
  
> [!NOTE]
>  建議您在為自己的事件定義事件處理常式時，使用這種命名慣例，但這並非必要的，您可以使用任何有效的副程式名稱。  
  
## 建立事件與事件處理常式的關聯  
 在可使用事件處理常式之前，您必須先使用 `Handles` 或 `AddHandler` 陳述式，建立該事件處理常式與事件的關聯。  
  
### WithEvents 和 Handles 子句  
 `WithEvents` 陳述式和 `Handles` 子句讓您以宣告的方式來指定事件處理常式。  透過任何適用於該事件之具有 `Handles` 陳述式的程序，即可處理藉由 `WithEvents` 關鍵字所宣告之物件所引發的事件，如以下範例所示：  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#1)]  
  
 `WithEvents` 陳述式和 `Handles` 子句通常是事件處理常式的最佳選擇，原因在於它們所使用的宣告式語法能讓事件處理更容易編碼、讀取和偵錯。  但請注意下列使用 `WithEvents` 變數的限制：  
  
-   您無法將 `WithEvents` 變數當做物件變數使用。  也就是說，您無法將其宣告為 `Object`，而是當您宣告變數時，就必須指定類別名稱。  
  
-   因為未將共用事件 `` 繫結至類別執行個體，因此您不能以宣告方式使用 `WithEvents` 控制共用事件。  同樣地，您也不能使用 `WithEvents` 或 `Handles` 處理 `Structure` 中的事件。  在這兩種情況下，您都可以使用 `AddHandler` 陳述式控制這些事件。  
  
-   您無法建立 `WithEvents` 變數的陣列。  
  
 `WithEvents` 變數可讓單一事件處理常式處理一種或多種事件，或者是讓一個或以上的事件處理常式來處理相同的事件。  
  
 雖然 `Handles` 子句是讓事件與事件處理常式產生關聯的標準方法，但在編譯時間建立事件與事件處理常式的關聯卻有所限制。  
  
 在一些情況下 \(例如，與表單或控制項關聯的事件\)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動虛設空的事件處理常式，並使它與事件產生關聯。  例如，當您在設計模式中按兩下表單上的命令按鈕時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會為命令按鈕建立空的事件處理常式和 `WithEvents` 變數，如以下程式碼所示：  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#26)]  
  
### AddHandler 和 RemoveHandler  
 `AddHandler` 陳述式 \(Statement\) 與 `Handles` 子句類似，兩者都允許您指定事件處理常式。  不過，與 `RemoveHandler` 搭配使用之 `AddHandler` 所提供的彈性會比 `Handles` 子句還大，讓您能動態加入、移除和變更與事件相關聯的事件處理常式。  如果想要處理共用事件或結構中的事件，則必須使用 `AddHandler`。  
  
 `AddHandler` 使用兩引數：來自事件傳送者 \(例如控制項\) 的事件名稱，以及評估為委派 \(Delegate\) 的運算式。  當您使用 `AddHandler` 時，您不需要明確指定委派類別，因為 `AddressOf` 陳述式固定會傳回委派的參考。  以下範例讓事件處理常式與物件引發的事件產生關聯：  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#28)]  
  
 `RemoveHandler` 是用來中斷事件與事件處理常式的連接，它所使用的語法與 `AddHandler` 相同。  例如：  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#29)]  
  
 在下列範例中，會將事件處理常式關聯至事件，然後引發事件。  這個事件處理常式會攔截事件，顯示一則訊息。  
  
 接著移除第一個事件處理常式，並將另一個事件處理常式關聯至事件。  再次引發事件時，會顯示另一則訊息。  
  
 最後，移除第二個事件處理常式，第三次引發事件。  由於再也沒有事件處理常式關聯至事件，所以不會採取任何動作。  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class2.vb#38)]  
  
## 處理自基底類別繼承的事件  
 「*衍生類別*」\(Derived Class\) 是自基底類別 \(Base Class\) 繼承特性的類別，能夠使用 `Handles` `MyBase` 陳述式處理由基底類別所引發的事件。  
  
#### 若要處理來自於基底類別的事件  
  
-   在衍生類別中宣告事件處理常式，方式便是將 `Handles MyBase.`*eventname* 陳述式加入至事件處理常式程序的宣告列，其中 *eventname* 是基底類別中所要處理之事件的名稱。  例如：  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#12)]  
  
## 相關章節  
  
|標題|描述|  
|--------|--------|  
|[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|提供如何針對類別宣告與引發事件的逐步說明。|  
|[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|示範如何撰寫事件處理常式程序。|  
|[How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|示範如何定義允許非同步呼叫事件處理常式的自訂事件。|  
|[How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|示範如何定義只在處理事件時使用記憶體的自訂事件。|  
|[Troubleshooting Inherited Event Handlers in Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|列出繼承元件中事件處理常式會產生的常見問題。|  
|[事件](../Topic/Handling%20and%20Raising%20Events.md)|提供 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中事件模型的概觀。|  
|[在 Windows Form 中建立事件處理常式](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)|說明如何使用與 Windows Form 物件關聯的事件。|  
|[Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)|提供 Visual Basic 中的委派概觀。|