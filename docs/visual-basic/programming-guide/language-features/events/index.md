---
title: 事件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 65b4f5633e589ae02e9ed495074000181864428a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956363"
---
# <a name="events-visual-basic"></a>事件 (Visual Basic)
雖然您可能會將 Visual Studio 專案視覺化成一系列以序列方式執行的程式, 但實際上, 大部分的程式都是事件驅動的, 這表示執行流程是由稱為*事件*的外部出現專案所決定。  
  
 事件是通知應用程式發生重要事件的信號。 例如，當使用者按一下表單上的控制項時，表單可以引發 `Click` 事件，並呼叫處理事件的程序。 事件也允許個別工作進行通訊。 例如，假設您的應用程式與主應用程式個別執行排序工作。 如果使用者取消排序，則您的應用程式可以傳送取消事件，以指示排序處理序停止。  
  
## <a name="event-terms-and-concepts"></a>事件詞彙和概念  
 本節說明 Visual Basic 中的事件所使用的詞彙和概念。  
  
### <a name="declaring-events"></a>宣告事件  
 您可以在類別、結構、模組和介面內，使用 `Event` 關鍵字宣告事件，如下列範例所示：  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>引發事件  
 事件就像是訊息，會告知發生了重要事件。 廣播訊息的動作稱為「引發」事件。 在 Visual Basic 中, 您會使用`RaiseEvent`語句引發事件, 如下列範例所示:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 事件必須在其宣告所在的類別、模組或結構範圍內引發。 例如，衍生的類別無法引發繼承自基底類別的事件。  
  
### <a name="event-senders"></a>事件傳送者  
 任何可引發事件的物件都是「事件傳送者」，亦稱為「事件來源」。 表單、控制項和使用者定義的物件都是事件傳送者的範例。  
  
### <a name="event-handlers"></a>事件處理常式  
 「事件處理常式」是在發生相對應事件時所呼叫的程序。 您可以使用具有相符簽章的任何有效副程式，做為事件處理常式。 不過，您無法使用函式做為事件處理常式，因為它無法將值傳回事件來源。  
  
 Visual Basic 針對事件處理常式 (結合事件傳送者的名稱、底線和事件名稱) 使用標準命名慣例。 例如，將名為 `button1` 的按鈕 `Click` 事件命名為 `Sub button1_Click`。  
  
> [!NOTE]
> 我們建議您在為自己的事件定義事件處理常式時，使用此命名慣例，但這並非必要；您可以使用任何有效的副程式名稱。  
  
## <a name="associating-events-with-event-handlers"></a>建立事件與事件處理常式的關聯  
 讓事件處理常式變成可用之前，您必須先使用 `Handles` 或 `AddHandler` 陳述式來建立它與事件的關聯。  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents 和 Handles 子句  
 `WithEvents` 陳述式和 `Handles` 子句提供一種宣告式方式來指定事件處理常式。 使用 `WithEvents` 關鍵字宣告之物件所引發的事件可以透過任何具有 `Handles` 陳述式的程序來處理，如下列範例所示：  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 `WithEvents` 陳述式和 `Handles` 子句通常是事件處理常式的最佳選擇，因為它們使用的宣告式語法讓事件能夠更容易處理程式碼、讀取及偵錯。 不過，請注意下列有關使用 `WithEvents` 變數的限制：  
  
- 您不能使用 `WithEvents` 變數做為物件變數。 也就是說，您無法將它宣告為 `Object` - 當您宣告變數時，必須指定類別名稱。  
  
- 由於共用事件不會系結至類別實例, 因此您`WithEvents`無法使用以宣告方式處理共用事件。 同樣地，您不能使用 `WithEvents` 或 `Handles`，處理來自 `Structure` 的事件。 在這兩種情況下，您可以使用 `AddHandler` 陳述式來處理這些事件。  
  
- 您無法建立 `WithEvents` 變數的陣列。  
  
 `WithEvents` 變數可讓單一事件處理常式處理一或多種事件，或者讓一或多個事件處理常式處理相同種類的事件。  
  
 雖然 `Handles` 子句是建立事件與事件處理常式之關聯的標準方式，但它只能在編譯時期建立事件與事件處理常式的關聯。  
  
 在某些情況下, 例如使用與表單或控制項相關聯的事件, Visual Basic 會自動將空的事件處理常式存根, 並將其與事件產生關聯。 例如, 當您在設計模式中按兩下表單上的命令按鈕時, Visual Basic 會建立空的事件處理常式和`WithEvents`命令按鈕的變數, 如下列程式碼所示:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler 和 RemoveHandler  
 `AddHandler` 陳述式類似 `Handles` 子句，這兩者都能讓您指定事件處理常式。 不過，與 `RemoveHandler` 搭配使用的 `AddHandler` 所提供的彈性比 `Handles` 子句更大，可讓您以動態方式加入、移除及變更與事件相關聯的事件處理常式。 如果您想要處理共用的事件或來自結構的事件，就必須使用 `AddHandler`。  
  
 `AddHandler` 會採用兩個引數︰來自事件傳送者的事件名稱 (例如控制項)，以及評估委派的運算式。 使用 `AddHandler` 時，您不需明確指定委派類別，因為 `AddressOf` 陳述式一律會傳回對委派的參考。 下列範例會建立事件處理常式與物件所引發之事件的關聯：  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler` (其會中斷事件與事件處理常式的關聯) 會使用與 `AddHandler` 相同的語法。 例如：  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 在下列範例中，事件處理常式會與事件相關聯，並引發事件。 事件處理常式會攔截事件，並顯示一則訊息。  
  
 接著，移除第一個事件處理常式，並將不同的事件處理常式關聯至該事件。 再次引發事件時，即會顯示不同的訊息。  
  
 最後，移除第二個事件處理常式，然後第三次引發事件。 由於不再有與事件相關聯的事件處理常式，因此不會採取任何動作。  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>處理繼承自基底類別的事件  
 「衍生類別」(繼承基底類別特性的類別) 可以使用 `Handles MyBase` 陳述式，來處理其基底類別所引發的事件。  
  
### <a name="to-handle-events-from-a-base-class"></a>處理來自基底類別的事件  
  
- 在衍生類別中宣告事件處理常式，方法是將 `Handles MyBase.`*eventname* 陳述式加入至事件處理常式程序的宣告行中，其中 *eventname* 為您要處理之基底類別中的事件名稱。 例如：  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>相關章節  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|提供如何宣告和引發類別事件的逐步說明。|  
|[逐步解說：處理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|示範如何撰寫事件處理常式的程序。|  
|[如何：宣告自訂事件以避免封鎖](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|示範如何定義自訂事件，以非同步方式呼叫它的事件處理常式。|  
|[如何：宣告自訂事件以節省記憶體](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|示範如何定義只有在處理事件時才會使用記憶體的自訂事件。|  
|[Visual Basic 中的繼承事件處理常式疑難排解](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|列出繼承元件中的事件處理常式所引發的常見問題。|  
|[事件](../../../../standard/events/index.md)|提供 .NET Framework 中事件模型的概觀。|  
|[在 Windows Forms 中建立事件處理常式](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|描述如何使用與 Windows Form 物件相關聯的事件。|  
|[委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|提供 Visual Basic 中的委派概觀。|
