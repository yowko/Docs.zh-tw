---
title: RaiseEvent 語句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ee52b4adf893ea0926c4016fcb6a89d0010ee6ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957773"
---
# <a name="raiseevent-statement"></a>RaiseEvent 陳述式
觸發在類別、表單或檔中, 于模組層級宣告的事件。  
  
## <a name="syntax"></a>語法  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>組件  
 `eventname`  
 必要項。 要觸發的事件名稱。  
  
 `argumentlist`  
 選擇性。 以逗號分隔的變數、陣列或運算式清單。 `argumentlist`引數必須以括弧括住。 如果沒有引數, 則必須省略括弧。  
  
## <a name="remarks"></a>備註  
 必要`eventname`的是在模組內宣告的事件名稱。 它會遵循 Visual Basic 變數命名慣例。  
  
 如果事件尚未在引發它的模組內宣告, 就會發生錯誤。 下列程式碼片段說明事件宣告, 以及引發事件的程式。  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 您不能`RaiseEvent`使用來引發未在模組中明確宣告的事件。 例如, 所有表單都會繼承<xref:System.Windows.Forms.Control.Click>來自<xref:System.Windows.Forms.Form?displayProperty=nameWithType>的事件, 而無法使用`RaiseEvent`衍生表單中的來引發。 如果您`Click`在表單模組中宣告事件, 它會遮蔽表單本身<xref:System.Windows.Forms.Control.Click>的事件。 您仍然可以藉由<xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Control.OnClick%2A>呼叫方法來叫用表單的事件。  
  
 根據預設, 在 Visual Basic 中定義的事件會依照建立連接的順序, 引發其事件處理常式。 由於事件可以有`ByRef`參數, 因此連接延遲的進程可能會接收先前事件處理常式已變更的參數。 在事件處理常式執行之後, 控制權會傳回給引發事件的副程式。  
  
> [!NOTE]
> 非共用事件不應在宣告它們的類別的函式中引發。 雖然這類事件不會造成執行階段錯誤, 但關聯的事件處理常式可能無法攔截它們。 如果您需要從函數引發事件, 請使用修飾詞來建立共用事件。`Shared`  
  
> [!NOTE]
> 您可以藉由定義自訂事件來變更事件的預設行為。 若為自訂事件`RaiseEvent` , 語句會叫用`RaiseEvent`事件的存取子。 如需自訂事件的詳細資訊, 請參閱[Event 語句](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用事件以從 10 秒到 0 秒倒數計時。 此程式碼說明數個事件相關的方法、屬性和語句, 包括`RaiseEvent`語句。  
  
 引發事件的類別是事件來源，處理事件的方法為事件處理常式。 事件來源對於它所產生的事件可以有多個處理常式。 當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。  
  
 此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。 當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
 `Form1` 的程式碼會指定表單的初始和終止狀態。 它也包含引發事件時執行的程式碼。  
  
 若要使用此範例, 請開啟新的 Windows 應用程式專案, 將`Button1`名為的按鈕和`TextBox1`名為的文字方塊新增至`Form1`主要表單, 名稱為。 然後以滑鼠右鍵按一下表單, 再按一下 [**查看程式碼**] 以開啟程式碼編輯器。  
  
 將變數新增至`Form1`類別的宣告區段。 `WithEvents`  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  
 將下列程式碼加入至 `Form1` 的程式碼。 取代可能存在的任何重複的程式, 例如`Form_Load`或。 `Button_Click`  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 按 F5 執行上述範例, 然後按一下標示為 [**開始**] 的按鈕。 第一個文字方塊會開始倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
> [!NOTE]
> `My.Application.DoEvents`方法不會以與表單相同的方式來處理事件。 若要允許表單直接處理事件, 您可以使用多執行緒。 如需詳細資訊, 請參閱[Managed 執行緒](../../../standard/threading/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
