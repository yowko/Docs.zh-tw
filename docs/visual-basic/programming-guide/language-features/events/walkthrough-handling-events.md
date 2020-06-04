---
title: 處理事件
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 29d878afbe3669fc88e62b1fec98b306918c303d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405076"
---
# <a name="walkthrough-handling-events-visual-basic"></a>逐步解說：處理事件 (Visual Basic)
這是示範如何處理事件的兩個主題的第二個。 第一個主題「[逐步解說：宣告和引發事件](walkthrough-declaring-and-raising-events.md)」會顯示如何宣告和引發事件。 本節使用該逐步解說中的表單和類別，以示範如何在事件發生時加以處理。  
  
 `Widget`類別範例會使用傳統的事件處理語句。 Visual Basic 提供處理事件的其他技術。 在練習中，您可以修改此範例以使用 `AddHandler` 和 `Handles` 語句。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>若要處理 Widget 類別的 PercentDone 事件  
  
1. 將下列程式碼放入 `Form1` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`關鍵字 `mWidget` 會指定使用變數來處理物件的事件。 您可以藉由提供要從中建立物件之類別的名稱，來指定物件的種類。  
  
     變數 `mWidget` 會在中宣告， `Form1` 因為 `WithEvents` 變數必須是類別層級。 無論您將它們放置在哪一種類別，都是如此。  
  
     變數 `mblnCancel` 是用來取消 `LongTask` 方法。  
  
## <a name="writing-code-to-handle-an-event"></a>撰寫程式碼來處理事件  
 一旦您使用來宣告變數 `WithEvents` ，變數名稱就會出現在類別程式**代碼編輯器**的左側下拉式清單中。 當您選取時 `mWidget` ， `Widget` 類別的事件會顯示在右邊的下拉式清單中。 選取事件會顯示對應的事件程式，並加上前置詞 `mWidget` 和底線。 與變數相關聯的所有事件程式 `WithEvents` 都會被指定變數名稱做為前置詞。  
  
#### <a name="to-handle-an-event"></a>若要處理事件  
  
1. 從 [程式 `mWidget` **代碼編輯器**] 的左側下拉式清單中選取。  
  
2. `PercentDone`從右邊的下拉式清單中選取事件。 [程式**代碼編輯器**] 會開啟 `mWidget_PercentDone` 事件程式。  
  
    > [!NOTE]
    > [程式**代碼編輯器**] 在插入新的事件處理常式時很有用，但並不是必要的。 在本逐步解說中，您可以直接將事件處理常式直接複製到程式碼中。  
  
3. 將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     每當 `PercentDone` 引發事件時，事件程式就會在控制項中顯示完成百分比 `Label` 。 `DoEvents`方法允許重新繪製標籤，也會讓使用者有機會按一下 [**取消**] 按鈕。  
  
4. 為 `Button2_Click` 事件處理常式新增下列程式碼：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 如果使用者在執行時按一下 [**取消**] 按鈕 `LongTask` ，當 `Button2_Click` `DoEvents` 語句允許事件處理發生時，就會立即執行事件。 類別層級變數 `mblnCancel` 會設定為 `True` ，然後 `mWidget_PercentDone` 事件會進行測試，並將 `ByRef Cancel` 引數設定為 `True` 。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>將 WithEvents 變數連接至物件  
 `Form1`現在已設定為可處理 `Widget` 物件的事件。 剩下的就是尋找一個 `Widget` 地方。  
  
 當您 `WithEvents` 在設計階段宣告變數時，不會有任何物件與其相關聯。 `WithEvents`變數就像任何其他物件變數一樣。 您必須建立物件，並使用變數來指派它的參考 `WithEvents` 。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>建立物件並指派其參考  
  
1. 從 [程式**代碼編輯器**] 的左側下拉式清單中，選取 [ **（Form1 事件）** ]。  
  
2. `Load`從右邊的下拉式清單中選取事件。 [程式**代碼編輯器**] 會開啟 `Form1_Load` 事件程式。  
  
3. 新增下列程式碼， `Form1_Load` 以供事件程式建立 `Widget` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 當此程式碼執行時，Visual Basic 會建立 `Widget` 物件，並將其事件連接至與相關聯的事件程式 `mWidget` 。 從該時間點開始，每當 `Widget` 引發其 `PercentDone` 事件時， `mWidget_PercentDone` 就會執行事件程式。  
  
#### <a name="to-call-the-longtask-method"></a>呼叫 LongTask 方法  
  
- 將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 在 `LongTask` 呼叫方法之前，必須先初始化顯示完成百分比的標籤，而且取消方法的類別層級 `Boolean` 旗標必須設定為 `False` 。  
  
 `LongTask`呼叫的工作持續時間為12.2 秒。 `PercentDone`事件每隔一秒引發一次。 每次引發事件時， `mWidget_PercentDone` 就會執行事件程式。  
  
 `LongTask`完成時， `mblnCancel` 會測試以查看是否 `LongTask` 正常結束，或是否因為 `mblnCancel` 已設定為而停止 `True` 。 完成的百分比只會在先前的情況下更新。  
  
#### <a name="to-run-the-program"></a>執行程式  
  
1. 按 F5 將專案置於執行模式。  
  
2. 按一下 [**啟動**工作] 按鈕。 每次 `PercentDone` 引發事件時，就會以完成工作的百分比來更新標籤。  
  
3. 按一下 [**取消**] 按鈕以停止工作。 請注意，當您按一下 [**取消**] 按鈕時，其外觀不會立即變更。 `Click`直到 `My.Application.DoEvents` 語句允許事件處理時，才會發生此事件。  
  
    > [!NOTE]
    > `My.Application.DoEvents`方法不會以與表單相同的方式來處理事件。 例如，在此逐步解說中，您必須按兩次 [**取消**] 按鈕。 若要允許表單直接處理事件，您可以使用多執行緒。 如需詳細資訊，請參閱[Managed 執行緒](../../../../standard/threading/index.md)。
  
 您可能會發現使用 F11 來執行程式，以及一次逐步執行一行程式碼，會有其意義。 您可以清楚地看到執行如何進入 `LongTask` ，然後 `Form1` 在每次引發事件時短暫重新進入 `PercentDone` 。  
  
 如果在的程式碼中執行時，會發生什麼情況 `Form1` ， `LongTask` 再次呼叫方法？ 在最糟的情況下，如果 `LongTask` 在每次引發事件時呼叫，則可能會發生堆疊溢位。  
  
 您可以藉由將 `mWidget` `Widget` 新的參考指派給，讓變數處理不同物件的事件 `Widget` `mWidget` 。 事實上，您可以在 `Button1_Click` 每次按一下按鈕時，讓程式碼執行此動作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>處理不同 widget 的事件  
  
- 將下列程式程式碼新增至 `Button1_Click` 程式，緊接在讀取的那一行前面 `mWidget.LongTask(12.2, 0.33)` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上述 `Widget` 程式碼會在每次按一下按鈕時建立新的。 一旦 `LongTask` 方法完成，就會釋放的參考， `Widget` 並終結 `Widget` 。  
  
 一個 `WithEvents` 變數一次只能包含一個物件參考，因此，如果您將不同的 `Widget` 物件指派給 `mWidget` ，就不會 `Widget` 再處理上一個物件的事件。 如果 `mWidget` 是唯一包含舊的參考的物件變數 `Widget` ，則會終結物件。 如果您想要處理來自數個 `Widget` 物件的事件，請使用 `AddHandler` 語句，分別處理每個物件的事件。  
  
> [!NOTE]
> 您可以視需要宣告多個 `WithEvents` 變數，但 `WithEvents` 不支援變數陣列。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：宣告和引發事件](walkthrough-declaring-and-raising-events.md)
- [事件](index.md)
