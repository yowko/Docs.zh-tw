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
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320687"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>逐步解說：宣告和引發事件 (Visual Basic)
本逐步解說示範如何宣告及引發事件的類別，名為`Widget`。 完成步驟後，您可能想要閱讀系列主題中，[逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)，但會示範如何使用事件`Widget`來提供應用程式中的狀態資訊的物件。  
  
## <a name="the-widget-class"></a>小工具類別  
 假設您有目前`Widget`類別。 您`Widget`類別具有的方法，可能需要很長的時間執行，而且您希望能夠架設完成指標的某種類型的應用程式。  
  
 當然，您可以製作`Widget`物件顯示完成百分比的對話方塊，但接著您會停在動彈不得該對話方塊，在您使用每個專案`Widget`類別。 物件設計的很好原則是讓使用的物件控制代碼的使用者介面的應用程式，除非物件的目的就是在表單或對話方塊的 管理。  
  
 目的`Widget`是執行其他工作，因此會將`PercentDone`事件，然後讓程序會呼叫`Widget`的方法會處理事件和顯示狀態更新。 `PercentDone`事件也可以提供一種機制，取消的工作。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要建立本主題的程式碼範例  
  
1. 開啟新的 Visual Basic Windows 應用程式專案，並建立表單名為`Form1`。  
  
2. 新增兩個按鈕和標籤以`Form1`。  
  
3. 依照下表所示的方式，命名物件。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|啟動工作|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`、 `Text`|lblPercentDone, 0|  
  
4. 在上**專案**功能表上，選擇**加入類別**類別，名為`Widget.vb`至專案。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>若要宣告事件，小工具類別  
  
-   使用`Event`關鍵字來宣告中的事件`Widget`類別。 請注意，事件可以有`ByVal`並`ByRef`引數，做為`Widget`的`PercentDone`事件示範：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 當呼叫物件收到`PercentDone`事件，`Percent`引數包含工作已完成的百分比。 `Cancel`引數可以設定為`True`取消引發事件的方法。  
  
> [!NOTE]
>  您可以宣告事件引數，就像您一樣的程序，但有下列例外狀況的引數：事件不可以有`Optional`或`ParamArray`引數，以及事件沒有傳回值。  
  
 `PercentDone`引發事件時`LongTask`方法`Widget`類別。 `LongTask` 採用兩個引數： 的時間長度偽裝成工作和之前的最短的時間間隔時要執行的方法`LongTask`引發暫停`PercentDone`事件。  
  
#### <a name="to-raise-the-percentdone-event"></a>若要引發 PercentDone 事件  
  
1. 若要簡化對存取`Timer`這個類別中，使用的屬性加入`Imports`陳述式的類別模組中，「 宣告 」 區段的上面`Class Widget`陳述式。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. 將下列程式碼加入 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 當您的應用程式呼叫`LongTask`方法中，`Widget`類別會引發`PercentDone`事件每`MinimumInterval`秒。 事件會傳回`LongTask`檢查是否`Cancel`引數設定為`True`。  
  
 以下幾個免責聲明是必要的。 為了簡單起見，`LongTask`程序假設您事先知道此工作將會花費多少時間。 這幾乎絕不會是大小寫。 將工作分割成區塊 （chunk） 的平均大小可能很困難，而且通常最關切的使用者只要他們取得的項目進行的指示之前，所經過的時間長度。  
  
 您可能會在此範例中發現另一個缺點。 `Timer`屬性會傳回自午夜以來已經過的秒數; 因此，應用程式當機午夜之前啟動。 更謹慎的方法，來測量時間會需要這類的界限條件納入考量，或完全避免使用它們，例如使用屬性`Now`。  
  
 既然`Widget`類別可以引發事件，您可以移至下一個逐步解說。 [逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用`WithEvents`產生關聯的事件處理常式和`PercentDone`事件。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
