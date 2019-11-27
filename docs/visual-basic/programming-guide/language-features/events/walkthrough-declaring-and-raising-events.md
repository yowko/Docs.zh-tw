---
title: 宣告和引發事件
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345093"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>逐步解說：宣告和引發事件 (Visual Basic)
本逐步解說示範如何針對名為 `Widget`的類別，宣告和引發事件。 完成這些步驟之後，您可能會想要閱讀「[逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)」主題，其中會顯示如何使用來自 `Widget` 物件的事件，在應用程式中提供狀態資訊。  
  
## <a name="the-widget-class"></a>Widget 類別  
 假設您有 `Widget` 類別。 您的 `Widget` 類別有一個可能需要很長時間才能執行的方法，而且您想要讓應用程式能夠放置某種類型的完成指標。  
  
 當然，您可以讓 `Widget` 物件顯示 [完成百分比] 對話方塊，但是您會在使用 `Widget` 類別的每個專案中，停滯該對話方塊。 物件設計的一個良好原則是讓使用物件的應用程式處理使用者介面，除非物件的整個目的是要管理表單或對話方塊。  
  
 `Widget` 的目的是要執行其他工作，因此最好加入 `PercentDone` 事件，然後讓呼叫 `Widget`的方法的程式處理該事件並顯示狀態更新。 `PercentDone` 事件也可以提供取消工作的機制。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要建立本主題的程式碼範例  
  
1. 開啟新的 Visual Basic Windows 應用程式專案，並建立名為 `Form1`的表單。  
  
2. 將兩個按鈕和標籤新增至 `Form1`。  
  
3. 依照下表所示的方式，命名物件。  
  
    |物件|屬性|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|啟動工作|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`, `Text`|lblPercentDone，0|  
  
4. 在 [**專案**] 功能表上，選擇 [**加入類別**]，將名為 `Widget.vb` 的類別加入至專案。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>若要宣告 Widget 類別的事件  
  
- 使用 `Event` 關鍵字來宣告 `Widget` 類別中的事件。 請注意，事件可以有 `ByVal` 和 `ByRef` 引數，如 `Widget`的 `PercentDone` 事件所示：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 當呼叫物件收到 `PercentDone` 事件時，`Percent` 引數會包含已完成之工作的百分比。 `Cancel` 引數可以設定為 `True` 取消引發事件的方法。  
  
> [!NOTE]
> 您可以宣告事件引數，就如同執行程式的引數一樣，但下列例外狀況除外：事件不能有 `Optional` 或 `ParamArray` 引數，而且事件沒有傳回值。  
  
 `PercentDone` 事件是由 `Widget` 類別的 `LongTask` 方法所引發。 `LongTask` 接受兩個引數：方法假裝為執行工作的時間長度，以及 `LongTask` 暫停之前的最小時間間隔，以引發 `PercentDone` 事件。  
  
#### <a name="to-raise-the-percentdone-event"></a>若要引發 PercentDone 事件  
  
1. 若要簡化這個類別所使用之 `Timer` 屬性的存取，請將 `Imports` 語句加入至類別模組之宣告區段的頂端（在 `Class Widget` 語句上方）。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. 將下列程式碼加入 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 當您的應用程式呼叫 `LongTask` 方法時，`Widget` 類別每隔 `MinimumInterval` 秒就會引發 `PercentDone` 事件。 當事件傳回時，`LongTask` 檢查 `Cancel` 引數是否設定為 `True`。  
  
 這裡有幾個必要的免責聲明。 為了簡單起見，`LongTask` 程式會假設您事先知道工作會花多少時間。 幾乎不會發生這種情況。 將工作劃分成甚至大小的區塊可能會很難，而對使用者而言，最重要的就是在收到某個專案的指示之前傳遞的時間量。  
  
 您可能已在此範例中發現另一個缺陷。 `Timer` 屬性會傳回從午夜以來已過的秒數;因此，如果應用程式在午夜之前就啟動，就會停滯。 更小心測量時間的方法會將界限條件（例如這種情況）納入考慮，或使用 `Now`之類的屬性加以避免。  
  
 現在 `Widget` 類別可以引發事件，您可以移至下一個逐步解說。 [逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)示範如何使用 `WithEvents`，將事件處理常式與 `PercentDone` 事件產生關聯。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
