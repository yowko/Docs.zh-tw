---
title: "處理事件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17cd0bddbe8c89cf60e19f3f2af6f448ad465d70
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a>逐步解說：處理事件 (Visual Basic)
這是示範如何使用事件的兩個主題的第二個。 第一個主題，[逐步解說︰ 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，示範如何宣告和引發事件。 本節會使用表單和類別，從該逐步解說顯示如何處理事件發生時它們。  
  
 `Widget`類別範例會使用傳統的事件處理陳述式。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供處理事件的其他技術。 做為練習，您可以修改此範例中使用`AddHandler`和`Handles`陳述式。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>要處理的 Widget 類別 PercentDone 事件  
  
1.  將下列程式碼中的`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents`關鍵字指定變數`mWidget`用來處理物件的事件。 您可以提供的類別建立物件的名稱指定物件的類型。  
  
     變數`mWidget`中宣告`Form1`因為`WithEvents`變數必須是類別層級。 這是不論您置入類別的型別，則為 true。  
  
     變數`mblnCancel`用來取消`LongTask`方法。  
  
## <a name="writing-code-to-handle-an-event"></a>撰寫程式碼來處理事件  
 當您宣告變數使用`WithEvents`，變數的名稱會出現在左邊的下拉式清單，此類別的**程式碼編輯器**。 當您選取`mWidget`、`Widget`類別的事件會出現在右邊下拉式清單中。 選取事件會顯示對應的事件程序，具有前置詞`mWidget`和底線。 相關聯的事件程序`WithEvents`變數指定變數的名稱，做為前置詞。  
  
#### <a name="to-handle-an-event"></a>若要處理的事件  
  
1.  選取`mWidget`從左邊的下拉式清單中**程式碼編輯器**。  
  
2.  選取`PercentDone`右邊下拉式清單中的事件。 **程式碼編輯器**開啟`mWidget_PercentDone`事件程序。  
  
    > [!NOTE]
    >  **程式碼編輯器**很有用，但非必要，適用於插入新的事件處理常式。 在本逐步解說中，它是更為直接的方式只是事件處理常式將直接複製到您的程式碼。  
  
3.  將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     每當`PercentDone`就會引發事件時，事件程序會顯示在完成百分比`Label`控制項。 `DoEvents`方法可讓重新繪製標籤，並也讓使用者按一下**取消** 按鈕。  
  
4.  加入下列程式碼`Button2_Click`事件處理常式︰  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 如果使用者按一下**取消**按鈕時`LongTask`正在執行，`Button2_Click`事件執行儘速`DoEvents`陳述式允許發生的事件處理。 類別層級變數`mblnCancel`設為`True`，而`mWidget_PercentDone`事件然後進行測試，並將`ByRef Cancel`引數`True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>連接 WithEvents 變數的物件  
 `Form1`現在來處理設定`Widget`物件的事件。 剩下的就尋找是`Widget`某處。  
  
 當您宣告變數`WithEvents`在設計階段沒有物件則有與其相關聯。 A`WithEvents`變數，就如同任何其他物件的變數。 您必須建立物件，並指定它的參考`WithEvents`變數。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>建立物件，並指派給它的參考  
  
1.  選取**（Form1 事件）**從左邊的下拉式清單中**程式碼編輯器**。  
  
2.  選取`Load`右邊下拉式清單中的事件。 **程式碼編輯器**開啟`Form1_Load`事件程序。  
  
3.  加入下列程式碼`Form1_Load`建立的事件程序`Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 此程式碼執行時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立`Widget`物件，並連接事件相關聯的事件程序`mWidget`。 從該點上，每當`Widget`引發其`PercentDone`事件`mWidget_PercentDone`執行事件程序。  
  
#### <a name="to-call-the-longtask-method"></a>若要呼叫 LongTask 方法  
  
-   將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 之前`LongTask`呼叫方法時，標籤，必須先初始化完成的百分比顯示，並在類別層級`Boolean`旗標的取消方法必須設為`False`。  
  
 `LongTask`稱為工作持續時間為 12.2 的秒數。 `PercentDone`事件引發一次每三分之一的第二個。 引發事件時，每次`mWidget_PercentDone`執行事件程序。  
  
 當`LongTask`完畢後，`mblnCancel`測試是否`LongTask`結束一般來說，或如果它停止，因為`mblnCancel`設為`True`。 前一個案例中只會更新以完成百分比表示。  
  
#### <a name="to-run-the-program"></a>執行程式  
  
1.  按 f5 鍵，將專案放置在執行模式。  
  
2.  按一下 [**開始工作**] 按鈕。 每次`PercentDone`就會引發事件，標籤會更新已完成工作的百分比。  
  
3.  按一下 [**取消**] 按鈕以停止工作。 請注意，外觀**取消**按鈕不會變更，請立即按一下它。 `Click`事件不會發生直到`My.Application.DoEvents`陳述式可讓事件處理。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`方法不會處理事件的相同方式表單一樣。 例如，在此逐步解說中，您必須按一下**取消**按鈕兩次。 若要讓表單直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。  
  
 您可能會發現使用 F11 執行程式，並逐步執行程式碼行一次會更有意義。 您可以清楚看到如何執行進入`LongTask`，又再簡短重新進入`Form1`每次`PercentDone`就會引發事件。  
  
 會發生什麼事如果上一步中的程式碼執行時`Form1`、`LongTask`再次呼叫方法？ 最糟的情況，如果可能會發生堆疊溢位`LongTask`每次引發事件所呼叫。  
  
 您可以使變數`mWidget`來處理事件的不同`Widget`物件的參考指派給新`Widget`到`mWidget`。 事實上，您可以進行中的程式碼`Button1_Click`每次您按一下按鈕，執行這項操作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>若要處理不同的 widget 的事件  
  
-   加入下列這一行程式碼`Button1_Click`程序，那一行的前置`mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 上述程式碼會建立新`Widget`每次按一下按鈕時。 只要`LongTask`方法完成時，若要參考`Widget`已釋放，而`Widget`終結。  
  
 A`WithEvents`變數可以包含只有一個物件參考一次，因此，如果您可以指派不同`Widget`物件傳遞給`mWidget`，先前`Widget`將不會再處理物件的事件。 如果`mWidget`是唯一的物件變數包含參考舊`Widget`，終結物件。 如果您想要處理來自數個事件`Widget`物件，使用`AddHandler`陳述式來個別處理每個物件的事件。  
  
> [!NOTE]
>  您可以宣告為許多`WithEvents`變數做為您的需要但陣列`WithEvents`不支援變數。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
