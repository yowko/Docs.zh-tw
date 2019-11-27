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
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345075"
---
# <a name="walkthrough-handling-events-visual-basic"></a>逐步解說：處理事件 (Visual Basic)
這是示範如何處理事件的兩個主題的第二個。 第一個主題「[逐步解說：宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)」會顯示如何宣告和引發事件。 本節使用該逐步解說中的表單和類別，以示範如何在事件發生時加以處理。  
  
 `Widget` 類別範例會使用傳統的事件處理語句。 Visual Basic 提供處理事件的其他技術。 在練習中，您可以修改此範例，以使用 `AddHandler` 和 `Handles` 語句。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>若要處理 Widget 類別的 PercentDone 事件  
  
1. 將下列程式碼放在 `Form1`：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents` 關鍵字會指定使用變數 `mWidget` 來處理物件的事件。 您可以藉由提供要從中建立物件之類別的名稱，來指定物件的種類。  
  
     變數 `mWidget` 會在 `Form1` 中宣告，因為 `WithEvents` 變數必須是類別層級。 無論您將它們放置在哪一種類別，都是如此。  
  
     變數 `mblnCancel` 用來取消 `LongTask` 方法。  
  
## <a name="writing-code-to-handle-an-event"></a>撰寫程式碼來處理事件  
 當您使用 `WithEvents`宣告變數時，變數名稱就會出現在類別程式**代碼編輯器**的左側下拉式清單中。 當您選取 [`mWidget`] 時，`Widget` 類別的事件就會顯示在右邊的下拉式清單中。 選取事件會顯示對應的事件程式，其中前置詞 `mWidget` 和底線。 與 `WithEvents` 變數相關聯的所有事件程式都會被指定變數名稱做為前置詞。  
  
#### <a name="to-handle-an-event"></a>若要處理事件  
  
1. 從 [程式**代碼編輯器**] 的左側下拉式清單中選取 [`mWidget`]。  
  
2. 從右邊的下拉式清單中選取 [`PercentDone`] 事件。 [程式**代碼編輯器**] 會開啟 `mWidget_PercentDone` 事件程式。  
  
    > [!NOTE]
    > [程式**代碼編輯器**] 在插入新的事件處理常式時很有用，但並不是必要的。 在本逐步解說中，您可以直接將事件處理常式直接複製到程式碼中。  
  
3. 將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     每當引發 `PercentDone` 事件時，事件程式就會在 `Label` 控制項中顯示完成百分比。 `DoEvents` 方法允許重新繪製標籤，也會讓使用者有機會按一下 [**取消**] 按鈕。  
  
4. 為 `Button2_Click` 事件處理常式新增下列程式碼：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 當 `LongTask` 執行時，如果使用者按一下 [**取消**] 按鈕，`Button2_Click` 事件就會在 `DoEvents` 語句允許事件處理發生時立即執行。 類別層級變數 `mblnCancel` 設定為 `True`，然後 `mWidget_PercentDone` 事件會進行測試，並將 `ByRef Cancel` 引數設定為 `True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>將 WithEvents 變數連接至物件  
 `Form1` 現在已設定為可處理 `Widget` 物件的事件。 剩下的就是在某處尋找 `Widget`。  
  
 當您在設計階段 `WithEvents` 宣告變數時，不會有任何物件與其相關聯。 `WithEvents` 變數就像任何其他物件變數一樣。 您必須建立物件，並使用 `WithEvents` 變數來指派它的參考。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>建立物件並指派其參考  
  
1. 從 [程式**代碼編輯器**] 的左側下拉式清單中，選取 [ **（Form1 事件）** ]。  
  
2. 從右邊的下拉式清單中選取 [`Load`] 事件。 [程式**代碼編輯器**] 會開啟 `Form1_Load` 事件程式。  
  
3. 為 `Form1_Load` 事件程式新增下列程式碼，以建立 `Widget`：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 當此程式碼執行時，Visual Basic 會建立 `Widget` 物件，並將其事件連接到與 `mWidget`相關聯的事件程式。 從該時間點開始，每當 `Widget` 引發其 `PercentDone` 事件時，就會執行 `mWidget_PercentDone` 事件程式。  
  
#### <a name="to-call-the-longtask-method"></a>呼叫 LongTask 方法  
  
- 將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 在呼叫 `LongTask` 方法之前，必須先初始化顯示完成百分比的標籤，而取消方法的類別層級 `Boolean` 旗標必須設定為 [`False`]。  
  
 呼叫 `LongTask` 的工作持續時間為12.2 秒。 `PercentDone` 事件會每隔一秒引發一次。 每次引發事件時，就會執行 `mWidget_PercentDone` 事件程式。  
  
 當 `LongTask` 完成時，`mblnCancel` 會進行測試，以查看 `LongTask` 是否正常結束，或是否因為 `mblnCancel` 設定為 [`True`] 而停止。 完成的百分比只會在先前的情況下更新。  
  
#### <a name="to-run-the-program"></a>執行程式  
  
1. 按 F5 將專案置於執行模式。  
  
2. 按一下 [**啟動**工作] 按鈕。 每次引發 `PercentDone` 事件時，就會以完成工作的百分比來更新標籤。  
  
3. 按一下 [**取消**] 按鈕以停止工作。 請注意，當您按一下 [**取消**] 按鈕時，其外觀不會立即變更。 `Click` 事件直到 `My.Application.DoEvents` 語句允許事件處理為止才會發生。  
  
    > [!NOTE]
    > `My.Application.DoEvents` 方法不會以與表單相同的方式來處理事件。 例如，在此逐步解說中，您必須按兩次 [**取消**] 按鈕。 若要允許表單直接處理事件，您可以使用多執行緒。 如需詳細資訊，請參閱[Managed 執行緒](../../../../standard/threading/index.md)。
  
 您可能會發現使用 F11 來執行程式，以及一次逐步執行一行程式碼，會有其意義。 您可以清楚地查看執行如何進入 `LongTask`，然後在每次引發 `PercentDone` 事件時，短暫重新進入 `Form1`。  
  
 如果在 `Form1`的程式碼中回到執行中，`LongTask` 方法再次呼叫了，會發生什麼事？ 在最糟的情況下，如果每次引發事件都會呼叫 `LongTask`，就會發生堆疊溢位。  
  
 您可以藉由將新 `Widget` 的參考指派給 `mWidget`，讓變數 `mWidget` 處理不同 `Widget` 物件的事件。 事實上，您可以將程式碼 `Button1_Click` 在每次按一下按鈕時執行此動作。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>處理不同 widget 的事件  
  
- 將下列程式程式碼新增至 `Button1_Click` 程式，緊接在讀取 `mWidget.LongTask(12.2, 0.33)`的那一行前面：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上述程式碼會在每次按一下按鈕時建立新的 `Widget`。 一旦 `LongTask` 方法完成，就會釋放 `Widget` 的參考，並終結 `Widget`。  
  
 `WithEvents` 變數一次只能包含一個物件參考，因此，如果您將不同的 `Widget` 物件指派給 `mWidget`，就不會再處理先前 `Widget` 物件的事件。 如果 `mWidget` 是唯一包含舊 `Widget`參考的物件變數，則會終結物件。 如果您想要處理來自數個 `Widget` 物件的事件，請使用 `AddHandler` 語句，分別處理每個物件的事件。  
  
> [!NOTE]
> 您可以視需要宣告多個 `WithEvents` 變數，但不支援 `WithEvents` 變數的陣列。  
  
## <a name="see-also"></a>請參閱

- [逐步解說：宣告和引發事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
