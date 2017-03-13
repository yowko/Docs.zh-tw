---
title: "Walkthrough: Handling Events (Visual Basic) | Microsoft Docs"
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
  - "event handling [Visual Basic], walkthroughs"
  - "walkthroughs [Visual Basic], event handling"
  - "variables [Visual Basic], WithEvents"
  - "events [Visual Basic], walkthroughs"
  - "WithEvents keyword, walkthroughs"
  - "event handlers [Visual Basic], walkthroughs"
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Walkthrough: Handling Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本文是示範如何使用事件的兩個主題中的第二部分。  第一個主題[逐步解說：宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)會顯示如何宣告和引發事件。  本節則是利用第一個逐步解說中的表單和類別，說明事件發生時要如何處理。  
  
 `Widget` 類別範例會使用傳統的事件處理陳述式。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供用於處理事件的其他技術。  您可將這個範例修改為使用 `AddHandler` 和 `Handles` 陳述式來做為練習。  
  
### 若要處理 Widget 類別的 PercentDone 事件  
  
1.  將下列程式碼置於 `Form1` 中：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents` 關鍵字指定使用變數 `mWidget` 來處理物件的事件。  藉由提供即將建立之物件的類別名稱，您可以指定物件類型。  
  
     因為 `WithEvents` 變數必須是類別層級，所以要在 `Form1` 中宣告變數 `mWidget`。  不論您將它們置於何種類別型別中都是如此。  
  
     使用 `mblnCancel` 變數來取消 `LongTask` 方法。  
  
## 撰寫處理事件的程式碼  
 一旦使用 `WithEvents` 宣告變數，變數名稱就會出現在類別之 \[**程式碼編輯器**\] 左邊的下拉式清單中。  當您選擇 `mWidget` 時，`Widget` 類別的事件會出現在右邊的下拉式清單中。  如果選擇事件，就會顯示帶有前置詞 `mWidget` 和底線的對應事件程序。  所有與 `WithEvents` 變數有關的事件程序都會以變數名稱做為前置詞。  
  
#### 若要處理事件  
  
1.  從 \[**程式碼編輯器**\] 左邊的下拉式清單中選取 `mWidget`。  
  
2.  從右邊的下拉式清單中選取 `PercentDone` 事件。  \[**程式碼編輯器**\] 會開啟 `mWidget_PercentDone` 事件程序。  
  
    > [!NOTE]
    >  \[**程式碼編輯器**\] 對於插入新事件處理常式而言十分有用，但不是必要項。  在這個逐步解說中，更為直接的方式是將事件處理常式直接複製到程式碼中。  
  
3.  將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     每次引發 `PercentDone` 事件時，事件程序就會在 `Label` 控制項中顯示完成百分比。  `DoEvents` 方法允許重新繪製標籤，並且還提供機會讓使用者按一下 \[**取消**\] 按鈕。  
  
4.  將下列程式碼加入 `Button2_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 如果使用者在 `LongTask` 執行時按一下 \[**取消**\] 按鈕，一旦 `DoEvents` 陳述式允許發生事件處理，就會執行 `Button2_Click` 事件。  將類別層級變數 `mblnCancel` 設為 `True`，然後 `mWidget_PercentDone` 事件會進行測試，並將 `ByRef Cancel` 引數設為 `True`。  
  
## 將 WithEvents 變數連接至物件  
 `Form1` 已經設定完成，而能處理 `Widget` 物件的事件。  現在還需要找出其他的 `Widget`。  
  
 當您在設計階段宣告 `WithEvents` 變數時，沒有任何物件與它有關。  `WithEvents` 變數就像其他物件變數一樣。  您必須建立物件並利用 `WithEvents` 變數為物件指派參考。  
  
#### 若要建立物件並為物件指派參考  
  
1.  從 \[**程式碼編輯器**\] 左邊的下拉式清單中選取 \[**\(Form1 事件\)**\]。  
  
2.  從右邊的下拉式清單中選取 `Load` 事件。  \[**程式碼編輯器**\] 會開啟 `Form1_Load` 事件程序。  
  
3.  將下列程式碼加入 `Form1_Load` 事件程序，即可建立 `Widget`：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 在執行這個程式碼時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會建立 `Widget` 物件，並將它的事件連接到與 `mWidget` 相關聯的事件程序。  從此以後，每當 `Widget` 引發它的 `PercentDone` 事件時，就會執行 `mWidget_PercentDone` 事件程序。  
  
#### 若要呼叫 LongTask 方法  
  
-   將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 在呼叫 `LongTask` 方法之前，必須先初始化顯示完成百分比的標籤，而且用於取消方法的類別層級 `Boolean` 旗標必須設為 `False`。  
  
 呼叫 `LongTask` 的工作持續時間為 12.2 秒。  每三分之一秒的時間會引發 `PercentDone` 事件一次。  每次引發事件時，就會執行 `mWidget_PercentDone` 事件程序。  
  
 當 `LongTask` 完成時，因為 `mblnCancel` 設為 `True`，因此會測試 `mblnCancel`，查看 `LongTask` 是否正常結束，或它是否停止。  只有在之前的情況下，完成百分比才會更新。  
  
#### 若要執行程式  
  
1.  按 F5 使專案進入執行模式。  
  
2.  按一下 \[**開始工作**\] 按鈕。  每次引發 `PercentDone` 事件時，就會以工作完成百分比來更新標籤。  
  
3.  按一下 \[**取消**\] 按鈕，停止工作。  請注意，當您按一下 \[**取消**\] 按鈕時，此按鈕的外觀不會立刻改變。  必須等到 `My.Application.DoEvents` 陳述式允許處理事件，才會發生 `Click` 事件。  
  
    > [!NOTE]
    >  `My.Application.DoEvents` 方法處理事件的方式和表單的方式不太一樣。  例如，在此逐步解說中，您必須按兩下 \[**取消**\] 按鈕。  若要讓表單直接處理事件，您可以使用多執行緒處理。  如需詳細資訊，請參閱 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 您會發現利用 F11 執行程式是很有用的，它會逐行解說程式碼。  您可以清楚地看到執行是如何進入 `LongTask`，而且每次引發 `PercentDone` 事件時是如何短暫地重新進入 `Form1`。  
  
 如果執行回到 `Form1` 程式碼時又再度呼叫 `LongTask` 方法，會發生什麼事呢？  如果每次引發事件時都呼叫 `LongTask`，最壞的情況是可能會發生堆疊溢位 \(Stack Overflow\)。  
  
 您可以將參考指派給 `mWidget` 的新 `Widget`，使 `mWidget` 變數能針對不同的 `Widget` 物件處理事件。  事實上，您可以每次按這個按鈕時就讓 `Button1_Click` 中的程式碼作這個動作。  
  
#### 若要處理不同的 Widget 事件  
  
-   將下一行的程式碼加入 `Button1_Click` 程序中，而且要放在 `mWidget.LongTask(12.2, 0.33)` 的前一行：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 上述程式碼會在每次按一下按鈕時建立新的 `Widget`。  一旦 `LongTask` 方法完成後，就會釋放 `Widget` 的參考，然後終結 `Widget`。  
  
 `WithEvents` 變數一次只能包含一個物件參考，所以如果將不同的 `Widget` 物件指派給 `mWidget`，就不再處理前一個 `Widget` 物件的事件。  如果 `mWidget` 是唯一包含舊 `Widget` 參考的物件變數，則會終結物件。  如果您希望處理不同 `Widget` 物件的事件，請使用 `AddHandler` 陳述式，個別處理每個物件的事件。  
  
> [!NOTE]
>  您可以視需要宣告所需數量的 `WithEvents` 變數，但不支援 `WithEvents` 變數陣列。  
  
## 請參閱  
 [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)