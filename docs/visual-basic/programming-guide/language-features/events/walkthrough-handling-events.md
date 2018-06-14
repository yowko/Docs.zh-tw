---
title: 處理事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 0ac3514505ca42870d77317feec30a27e4384e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655110"
---
# <a name="walkthrough-handling-events-visual-basic"></a>逐步解說：處理事件 (Visual Basic)
這是兩個主題會示範如何使用事件的第二個。 第一個主題，[逐步解說： 宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)，示範如何宣告和引發事件。 本節會使用表單和類別，從該逐步解說顯示如何處理時就會發生的事件。  
  
 `Widget`類別範例會使用傳統的事件處理陳述式。 Visual Basic 提供其他技術使用的事件。 做為練習，您可以修改此範例中使用`AddHandler`和`Handles`陳述式。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>若要處理 PercentDone 類別之事件的小工具  
  
1.  將下列程式碼中的`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents`關鍵字指定變數`mWidget`用來處理物件的事件。 您可以提供要從中建立物件的類別名稱指定物件的類型。  
  
     變數`mWidget`中宣告`Form1`因為`WithEvents`變數必須是類別層級。 這是不論您放在類別的型別，則為 true。  
  
     變數`mblnCancel`用來取消`LongTask`方法。  
  
## <a name="writing-code-to-handle-an-event"></a>撰寫程式碼以處理事件  
 當您宣告變數使用`WithEvents`，變數的名稱會出現在左邊的下拉式清單，此類別的**程式碼編輯器**。 當您選取`mWidget`、`Widget`類別的事件會出現在右邊下拉式清單中。 選取的事件會顯示對應的事件程序，具有該前置詞`mWidget`和底線。 與相關聯的所有事件程序`WithEvents`變數指定變數的名稱，做為前置詞。  
  
#### <a name="to-handle-an-event"></a>若要處理的事件  
  
1.  選取`mWidget`左邊的下拉式清單中從**程式碼編輯器**。  
  
2.  選取`PercentDone`右邊下拉式清單中的事件。 **程式碼編輯器**開啟`mWidget_PercentDone`事件程序。  
  
    > [!NOTE]
    >  **程式碼編輯器**十分有用，但不是必要插入新的事件處理常式。 在本逐步解說中，它是更為直接的方式只複製直接插入程式碼的事件處理常式。  
  
3.  將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     每當`PercentDone`就會引發事件，將事件程序會顯示在完成百分比`Label`控制項。 `DoEvents`方法可讓重新繪製，標籤，也可讓使用者得以按一下**取消** 按鈕。  
  
4.  加入下列程式碼`Button2_Click`事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 如果使用者按一下**取消**按鈕時`LongTask`正在執行，`Button2_Click`事件執行儘速`DoEvents`陳述式可讓事件處理發生。 類別層級變數`mblnCancel`設`True`，而`mWidget_PercentDone`事件進行測試，然後設定`ByRef Cancel`引數`True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>連接 WithEvents 變數的物件  
 `Form1` 現在設定為處理`Widget`物件的事件。 若要尋找的剩下的只有`Widget`某處。  
  
 當您宣告變數`WithEvents`在設計階段物件不是有與其相關聯。 A`WithEvents`變數，就如同任何其他物件的變數。 您必須建立的物件，並將參考指派給它與`WithEvents`變數。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>若要建立的物件，並指派給它的參考  
  
1.  選取 **（Form1 事件）** 左邊的下拉式清單中從**程式碼編輯器**。  
  
2.  選取`Load`右邊下拉式清單中的事件。 **程式碼編輯器**開啟`Form1_Load`事件程序。  
  
3.  加入下列程式碼`Form1_Load`事件程序來建立`Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 此程式碼執行時，Visual Basic 建立`Widget`物件，並連接其事件相關聯的事件程序`mWidget`。 從該點上，每當`Widget`引發其`PercentDone`事件，`mWidget_PercentDone`執行事件程序。  
  
#### <a name="to-call-the-longtask-method"></a>若要呼叫 LongTask 方法  
  
-   將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 之前`LongTask`呼叫方法時，標籤，必須先初始化的顯示完成百分比，以及類別層級`Boolean`旗標的取消方法必須設為`False`。  
  
 `LongTask` 會呼叫工作持續時間為 12.2 秒。 `PercentDone`引發一次每三分之一的第二個。 引發事件時，每次`mWidget_PercentDone`執行事件程序。  
  
 當`LongTask`完畢後，`mblnCancel`測試是否`LongTask`正常，結束或它停止，因為如果`mblnCancel`已設為`True`。 前一個案例中只會更新以完成百分比表示。  
  
#### <a name="to-run-the-program"></a>執行程式  
  
1.  按 f5 鍵，將專案放在執行模式。  
  
2.  按一下**開始工作** 按鈕。 每次`PercentDone`就會引發事件，標籤已更新工作已完成的百分比。  
  
3.  按一下**取消**按鈕以停止工作。 請注意，外觀**取消**立即當您按一下按鈕不會變更。 `Click`事件發生之前`My.Application.DoEvents`陳述式可讓事件處理。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`方法不會處理事件中完全相同的方式與表單。 例如，在此逐步解說中，您必須按一下**取消**按鈕兩次。 若要允許表單以直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。  
  
 您可能會發現 F11 執行程式並逐步執行程式碼行一次會更有意義。 您可以清楚地查看如何執行輸入`LongTask`，又再簡短重新進入`Form1`每次`PercentDone`就會引發事件。  
  
 會發生什麼事如果上一步的程式碼中執行時`Form1`、`LongTask`方法所呼叫一次？ 最糟的情況，如果可能會發生堆疊溢位`LongTask`每次引發事件所呼叫。  
  
 您可以使變數`mWidget`來處理事件的不同`Widget`藉由指派新的參考物件`Widget`至`mWidget`。 事實上，您可以進行中的程式碼`Button1_Click`每次您按一下按鈕時執行這項操作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>若要處理不同的小工具事件  
  
-   加入下列一行程式碼`Button1_Click`程序中前讀取的行, `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 上述程式碼建立新`Widget`每次按下按鈕。 只要`LongTask`方法完成時，若要參考`Widget`已發行，而`Widget`終結。  
  
 A`WithEvents`變數可以包含只有一個物件參考一次，因此，如果您可以指派不同`Widget`物件`mWidget`，先前`Widget`將不會再處理物件的事件。 如果`mWidget`是唯一的物件變數包含參考舊`Widget`，就會終結物件。 如果您想要處理事件從幾個`Widget`物件，使用`AddHandler`陳述式來分別處理每個物件中的事件。  
  
> [!NOTE]
>  您可以宣告許多`WithEvents`變數做為您的需要但陣列`WithEvents`不支援變數。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
