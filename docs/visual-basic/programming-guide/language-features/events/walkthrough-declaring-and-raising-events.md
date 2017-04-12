---
title: "宣告和引發事件 (Visual Basic) |Microsoft 文件"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
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
ms.openlocfilehash: 233673c1d42684b7caa9042d18fb341a1043a31b
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>逐步解說：宣告和引發事件 (Visual Basic)
本逐步解說示範如何宣告和引發事件的類別，名為`Widget`。 完成的步驟之後，您可能要讀取的系列主題，[逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，以了解如何使用事件`Widget`來提供應用程式中的狀態資訊的物件。  
  
## <a name="the-widget-class"></a>Widget 類別  
 假設您有時間`Widget`類別。 您`Widget`類別具有一種方法，可能需要很長的時間執行，以及您希望能夠建立某種類型的指標完成的應用程式。  
  
 當然，您可以建立`Widget`物件顯示完成百分比的對話方塊，但之後您就會停在每個專案中使用該對話方塊`Widget`類別。 良好的物件設計原則就是讓使用物件控制代碼的使用者介面的應用程式，除非物件的目的就是在管理表單或對話方塊。  
  
 目的`Widget`是執行其他工作，因此最好是將`PercentDone`事件，然後讓呼叫的程序`Widget`的方法會處理事件和顯示狀態更新。 `PercentDone`事件也可以提供一個機制來取消工作。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要建立本主題的程式碼範例  
  
1.  開啟新[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案，並建立名為的表單`Form1`。  
  
2.  加入兩個按鈕和標籤`Form1`。  
  
3.  下表所示，為物件命名。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|啟動工作|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`, `Text`|lblPercentDone 0|  
  
4.  在**專案** 功能表上，選擇**加入類別**加入類別，名為`Widget.vb`至專案。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>若要宣告事件，以供 Widget 類別  
  
-   使用`Event`關鍵字來宣告中的事件`Widget`類別。 請注意，事件可以有`ByVal`和`ByRef`引數，做為`Widget`的`PercentDone`事件示範︰  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 當呼叫物件收到`PercentDone`事件`Percent`引數包含已完成工作的百分比。 `Cancel`引數可以設定為`True`取消引發事件的方法。  
  
> [!NOTE]
>  您可以宣告事件引數，就如同引數的程序，但有下列例外狀況︰ 事件不可以有`Optional`或`ParamArray`引數，以及事件不會有傳回值。  
  
 `PercentDone`引發事件`LongTask`方法`Widget`類別。 `LongTask`會採用兩個引數︰ 工作 （work) 和之前的最小時間間隔的時間長度方法偽裝`LongTask`暫停引發`PercentDone`事件。  
  
#### <a name="to-raise-the-percentdone-event"></a>若要引發 PercentDone 事件  
  
1.  若要簡化對存取`Timer`這個類別所使用的屬性加入`Imports`陳述式的類別模組中，「 宣告 」 區段頂端上方`Class Widget`陳述式。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  將下列程式碼加入 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents #&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 當您的應用程式呼叫`LongTask`方法，`Widget`類別會引發`PercentDone`事件每`MinimumInterval`秒。 此事件會傳回`LongTask`檢查，看看是否`Cancel`引數設為`True`。  
  
 以下幾個免責聲明是必要的。 為了簡單起見，`LongTask`程序假設您事先知道工作將會花多少時間。 這通常不是如此。 工作分割成多個區塊的大小可能很困難，而且通常最重要的使用者所取得表示項目發生之前經過的時間量。  
  
 您可以在此範例中發現另一個缺點。 `Timer`屬性會傳回從午夜的秒數，因此，應用程式一直顯示如果午夜之前啟動。 以更仔細的方法來測量時間會列入考量，這類的界限條件或完全避免使用它們，例如使用屬性`Now`。  
  
 既然`Widget`類別可以引發事件，您可以移至下一個逐步解說。 [逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`與事件處理常式關聯`PercentDone`事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [逐步解說︰ 處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
