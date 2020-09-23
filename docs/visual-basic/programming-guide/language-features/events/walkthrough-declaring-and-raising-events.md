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
ms.openlocfilehash: 07ef611b50cfa13f77fa168d58dd3b43e97eeec6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057984"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>逐步解說：宣告和引發事件 (Visual Basic)

本逐步解說示範如何針對名為的類別宣告和引發事件 `Widget` 。 完成這些步驟之後，您可能想要閱讀「 [逐步解說：處理事件](walkthrough-handling-events.md)」等主題，其中顯示如何使用 `Widget` 物件中的事件來提供應用程式中的狀態資訊。  
  
## <a name="the-widget-class"></a>Widget 類別  

 假設您有一個 `Widget` 類別。 您的 `Widget` 類別具有可能需要很長時間才能執行的方法，而且您想要讓應用程式能夠產生某種類型的完成指標。  
  
 當然，您可以將 `Widget` 物件顯示為 [百分比-完成] 對話方塊，但是在您使用類別的每個專案中，您會在該對話方塊中停滯 `Widget` 。 物件設計的好準則是讓使用物件的應用程式處理使用者介面，除非物件的整個目的是要管理表單或對話方塊。  
  
 的目的 `Widget` 是要執行其他工作，因此最好加入 `PercentDone` 事件，然後讓呼叫 `Widget` 的方法的程式處理該事件，並顯示狀態更新。 此 `PercentDone` 事件也可以提供取消工作的機制。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>若要建立本主題的程式碼範例  
  
1. 開啟新的 Visual Basic Windows 應用程式專案，並建立名為的表單 `Form1` 。  
  
2. 將兩個按鈕和標籤新增至 `Form1` 。  
  
3. 依照下表所示的方式，命名物件。  
  
    |Object|屬性|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|啟動工作|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`, `Text`|lblPercentDone，0|  
  
4. 在 [ **專案** ] 功能表上，選擇 [ **加入類別** ]，將名為的類別加入 `Widget.vb` 至專案。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>宣告 Widget 類別的事件  
  
- 使用 `Event` 關鍵字來宣告類別中的事件 `Widget` 。 請注意，事件可以有 `ByVal` 和 `ByRef` 引數，如事件所示 `Widget` `PercentDone` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 當呼叫物件接收事件時 `PercentDone` ， `Percent` 引數會包含已完成工作的百分比。 `Cancel`引數可以設定為， `True` 以取消引發事件的方法。  
  
> [!NOTE]
> 您可以像處理常式的引數一樣宣告事件引數，但有下列例外狀況：事件不能有 `Optional` 或 `ParamArray` 引數，而且事件沒有傳回值。  
  
 此 `PercentDone` 事件是由類別的 `LongTask` 方法所引發 `Widget` 。 `LongTask` 採用兩個引數：方法經過偽裝來執行工作的時間長度，以及 `LongTask` 暫停以引發事件的最小時間間隔 `PercentDone` 。  
  
#### <a name="to-raise-the-percentdone-event"></a>引發 PercentDone 事件  
  
1. 若要簡化 `Timer` 這個類別所使用之屬性的存取，請將 `Imports` 語句加入至類別模組的宣告區段頂端的 `Class Widget` 語句上方。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. 將下列程式碼新增至 `Widget` 類別：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 當您的應用程式呼叫 `LongTask` 方法時， `Widget` 類別每秒會引發 `PercentDone` 事件 `MinimumInterval` 。 當事件傳回時，會 `LongTask` 檢查是否 `Cancel` 已將引數設定為 `True` 。  
  
 這裡有幾個免責聲明。 為了簡單起見，此程式 `LongTask` 會假設您事先知道工作將花費多少時間。 這幾乎不會發生這種情況。 將工作分割成偶數的區塊可能會很困難，而且最重要的是，使用者最重要的是，這只是讓使用者知道發生問題的時間量。  
  
 在此範例中，您可能已發現另一個瑕疵。 `Timer`屬性會傳回從午夜開始經過的秒數，因此，如果應用程式是在午夜前啟動，就會停滯。 更謹慎的測量時間方法會將界限條件（如這項考慮）納入考慮，或使用等屬性來完全避免 `Now` 。  
  
 現在 `Widget` 類別可以引發事件，接下來您可以移至下一個逐步解說。 [逐步解說：處理事件](walkthrough-handling-events.md) 示範如何使用 `WithEvents` ，將事件處理常式與事件產生關聯 `PercentDone` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [逐步解說：處理事件](walkthrough-handling-events.md)
- [事件](index.md)
