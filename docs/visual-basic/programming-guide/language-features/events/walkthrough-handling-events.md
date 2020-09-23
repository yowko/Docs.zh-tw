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
ms.openlocfilehash: 4489f75e50a783a9b1acfb9c30568fdec6614488
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057906"
---
# <a name="walkthrough-handling-events-visual-basic"></a>逐步解說：處理事件 (Visual Basic)

這是示範如何使用事件的兩個主題中的第二個。 逐步解說：宣告 [和引發事件](walkthrough-declaring-and-raising-events.md)的第一個主題會顯示如何宣告和引發事件。 本節使用該逐步解說中的表單和類別，來示範如何在事件發生時處理事件。  
  
 `Widget`類別範例使用傳統事件處理語句。 Visual Basic 提供使用事件的其他技術。 在練習中，您可以修改此範例以使用 `AddHandler` 和 `Handles` 語句。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>處理 Widget 類別的 PercentDone 事件  
  
1. 將下列程式碼放入 `Form1` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`關鍵字會指定變數 `mWidget` 用來處理物件的事件。 您可以藉由提供將建立物件的類別名稱，來指定物件的種類。  
  
     變數 `mWidget` 是在中宣告， `Form1` 因為 `WithEvents` 變數必須是類別層級。 無論您放置它們的類別類型為何，都是如此。  
  
     變數 `mblnCancel` 是用來取消 `LongTask` 方法。  
  
## <a name="writing-code-to-handle-an-event"></a>撰寫程式碼來處理事件  

 當您使用宣告變數時 `WithEvents` ，變數名稱就會顯示在類別之程式 **代碼編輯器**的左側下拉式清單中。 當您選取時 `mWidget` ， `Widget` 類別的事件會出現在右邊的下拉式清單中。 選取事件會顯示對應的事件程式，其中包含前置詞 `mWidget` 和底線。 所有與變數相關聯的事件程式 `WithEvents` 都會提供變數名稱做為前置詞。  
  
#### <a name="to-handle-an-event"></a>若要處理事件  
  
1. `mWidget`從程式**代碼編輯器**的左側下拉式清單中選取。  
  
2. `PercentDone`從右邊的下拉式清單中選取事件。 程式 **代碼編輯器** 會開啟 `mWidget_PercentDone` 事件程式。  
  
    > [!NOTE]
    > 程式 **代碼編輯器** 很有用，但不是必要的，無法插入新的事件處理常式。 在這個逐步解說中，最好直接將事件處理常式複製到您的程式碼中。  
  
3. 將下列程式碼加入至 `mWidget_PercentDone` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     每當 `PercentDone` 引發事件時，事件程式就會在控制項中顯示完成百分比 `Label` 。 `DoEvents`方法允許重新繪製標籤，也讓使用者有機會按一下 [**取消**] 按鈕。  
  
4. 為 `Button2_Click` 事件處理常式新增下列程式碼：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 如果使用者在執行時按下 [ **取消** ] 按鈕，則會在 `LongTask` `Button2_Click` `DoEvents` 語句允許事件處理時立即執行事件。 類別層級變數 `mblnCancel` 設定為，然後 `True` 事件會進行 `mWidget_PercentDone` 測試，並將 `ByRef Cancel` 引數設定為 `True` 。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>將 WithEvents 變數連接至物件  

 `Form1` 現在已設定為處理 `Widget` 物件的事件。 剩下的就是尋找某個 `Widget` 地方。  
  
 當您 `WithEvents` 在設計階段宣告變數時，沒有任何物件與其相關聯。 `WithEvents`變數就像任何其他物件變數一樣。 您必須使用變數來建立物件並指派其參考 `WithEvents` 。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>建立物件並指派其參考  
  
1. 從程式**代碼編輯器**的左側下拉式清單中，選取 [ ** (Form1 事件]) ** 。  
  
2. `Load`從右邊的下拉式清單中選取事件。 程式 **代碼編輯器** 會開啟 `Form1_Load` 事件程式。  
  
3. 為事件程式新增下列程式碼 `Form1_Load` ，以建立 `Widget` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 當此程式碼執行時，Visual Basic 會建立 `Widget` 物件，並將其事件連接到與相關聯的事件程式 `mWidget` 。 從該時間點開始，每當 `Widget` 引發 `PercentDone` 事件時， `mWidget_PercentDone` 就會執行事件程式。  
  
#### <a name="to-call-the-longtask-method"></a>若要呼叫 LongTask 方法  
  
- 將下列程式碼加入至 `Button1_Click` 事件處理常式：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 在 `LongTask` 呼叫方法之前，必須初始化顯示完成百分比的標籤，而取消方法的類別層級 `Boolean` 旗標必須設定為 `False` 。  
  
 `LongTask` 使用工作持續時間12.2 秒來呼叫。 `PercentDone`事件會每隔一秒引發一次。 每次引發事件時， `mWidget_PercentDone` 就會執行事件程式。  
  
 `LongTask`完成時， `mblnCancel` 會測試以查看是否 `LongTask` 正常結束，或是否因為 `mblnCancel` 已設定為而停止 `True` 。 完成的百分比只會在先前的情況下更新。  
  
#### <a name="to-run-the-program"></a>執行程式  
  
1. 按 F5 將專案置於執行模式。  
  
2. 按一下 [ **啟動** 工作] 按鈕。 每次 `PercentDone` 引發事件時，都會以完成的工作百分比來更新標籤。  
  
3. 按一下 [ **取消** ] 按鈕以停止工作。 請注意，當您按一下 [ **取消** ] 按鈕時，它的外觀不會立即變更。 在 `Click` 語句允許事件處理之前，不會發生此事件 `My.Application.DoEvents` 。  
  
    > [!NOTE]
    > `My.Application.DoEvents`方法不會以與表單完全相同的方式來處理事件。 例如，在這個逐步解說中，您必須按一下 [ **取消** ] 按鈕兩次。 若要允許表單直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱 [Managed 執行緒](../../../../standard/threading/index.md)。
  
 您可能會發現使用 F11 來執行程式，並一次逐步執行程式碼。 您可以清楚地查看執行的輸入方式 `LongTask` ，然後 `Form1` 在每次引發事件時短暫重新輸入 `PercentDone` 。  
  
 如果在的程式碼中執行時，會發生什麼事 `Form1` ， `LongTask` 再次呼叫方法？ 在最糟的情況下，如果 `LongTask` 在每次引發事件時呼叫，就會發生堆疊溢位。  
  
 您可以藉由將 `mWidget` `Widget` 新的參考指派給，讓變數處理不同物件的事件 `Widget` `mWidget` 。 事實上，您可以在每次按下按鈕時，讓程式碼 `Button1_Click` 完成這項作業。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>處理不同 widget 的事件  
  
- 將下列程式程式碼加入 `Button1_Click` 程式中，緊接在讀取的行前面 `mWidget.LongTask(12.2, 0.33)` ：  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上述程式碼 `Widget` 會在每次按一下按鈕時建立新的。 當 `LongTask` 方法完成時，的參考就會釋出 `Widget` ，並終結 `Widget` 。  
  
 一個 `WithEvents` 變數一次只能包含一個物件參考，所以如果您將不同的物件指派 `Widget` 給 `mWidget` ，就不會 `Widget` 再處理之前的物件事件。 如果 `mWidget` 是唯一包含舊物件參考的物件變數 `Widget` ，則會終結物件。 如果您想要處理來自數個 `Widget` 物件的事件，請使用 `AddHandler` 語句分別處理每個物件的事件。  
  
> [!NOTE]
> 您可以宣告所 `WithEvents` 需數量的變數，但 `WithEvents` 不支援變數的陣列。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：宣告和引發事件](walkthrough-declaring-and-raising-events.md)
- [事件](index.md)
