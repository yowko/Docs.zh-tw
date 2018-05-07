---
title: 宣告和引發事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 67bbf7bc95a0fe1ee8e9c2a6cf07d850d30bb028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>逐步解說：宣告和引發事件 (Visual Basic)
本逐步解說示範如何宣告和引發事件的類別，名為`Widget`。 完成步驟之後，您可能想要閱讀附屬主題: <<c0> [ 逐步解說： 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，其示範如何使用事件`Widget`來提供應用程式中的狀態資訊的物件。  
  
## <a name="the-widget-class"></a>Widget 類別  
 假設您有目前`Widget`類別。 您`Widget`類別具有的方法，可能需要很長的時間執行，而且您希望能夠將某種類型的指標完成建立應用程式。  
  
 當然，您可以進行`Widget`物件顯示完成百分比的對話方塊，但接著您會當機與該對話方塊在您使用每個專案`Widget`類別。 物件設計好原則就是讓使用的物件控制代碼的使用者介面的應用程式，除非該物件的目的是為了管理表單或對話方塊方塊。  
  
 目的`Widget`是執行其他工作，因此最好是將`PercentDone`事件，然後讓呼叫的程序`Widget`的方法會處理事件和顯示狀態更新。 `PercentDone`事件也可以提供機制來取消工作。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要建立本主題的程式碼範例  
  
1.  開啟新的 Visual Basic Windows 應用程式專案，並建立名為表單`Form1`。  
  
2.  加入兩個按鈕和標籤以`Form1`。  
  
3.  依照下表所示的方式，命名物件。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|啟動工作|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`, `Text`|lblPercentDone 0|  
  
4.  在**專案**功能表上，選擇**加入類別**將類別命名為`Widget.vb`至專案。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>宣告事件，以供 Widget 類別  
  
-   使用`Event`關鍵字來宣告中的事件`Widget`類別。 請注意，事件可以有`ByVal`和`ByRef`引數，做為`Widget`的`PercentDone`事件示範：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 當呼叫的物件接收`PercentDone`事件，`Percent`引數包含已完成工作的百分比。 `Cancel`引數可以設定為`True`取消引發事件的方法。  
  
> [!NOTE]
>  您可以宣告事件引數，就像您一樣引數的程序，但有下列例外狀況： 事件不可以有`Optional`或`ParamArray`引數和事件不會有傳回值。  
  
 `PercentDone`就會引發事件`LongTask`方法`Widget`類別。 `LongTask` 會採用兩個引數： 做的動作 （work) 和之前的最小時間間隔的時間長度方法偽裝`LongTask`引發暫停`PercentDone`事件。  
  
#### <a name="to-raise-the-percentdone-event"></a>若要引發 PercentDone 事件  
  
1.  若要簡化存取`Timer`此類別中，所使用的屬性加入`Imports`陳述式加入您的類別模組中的宣告區段頂端上方`Class Widget`陳述式。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  將下列程式碼加入 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 當您的應用程式呼叫`LongTask`方法，`Widget`類別所引發`PercentDone`事件每`MinimumInterval`秒。 事件會傳回`LongTask`檢查`Cancel`引數設定為`True`。  
  
 以下幾個免責聲明是必要的。 為了簡單起見，`LongTask`程序假設您事先知道工作大約需要多久。 這幾乎是大小寫。 將工作分割成區塊的大小可能很困難，而且通常最重要的使用者只要他們取得表示項目發生之前，所經過的時間量。  
  
 您可能在此範例中發現其他缺陷。 `Timer`屬性會傳回自午夜以來已經過的秒數，因此，應用程式時遇如果午夜之前啟動。 測量時間更謹慎地方法會列入考量，這類的界限條件或避免發生，請使用下列屬性`Now`。  
  
 既然`Widget`類別可以引發事件，您可以移至下一個逐步解說。 [逐步解說： 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`相關聯的事件處理常式和`PercentDone`事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
