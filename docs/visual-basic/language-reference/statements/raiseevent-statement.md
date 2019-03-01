---
title: RaiseEvent 陳述式 (Visual Basic)
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
ms.openlocfilehash: ffe08dc8aeef9498d2e9f4c973c5ccbc31fec0b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973297"
---
# <a name="raiseevent-statement"></a>RaiseEvent 陳述式
觸發程序在類別、 表單或文件中的模組層級宣告的事件。  
  
## <a name="syntax"></a>語法  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>組件  
 `eventname`  
 必要項。 若要觸發事件的名稱。  
  
 `argumentlist`  
 選擇性。 以逗號分隔的變數、 陣列或運算式清單。 `argumentlist`引數必須以括號括住。 如果不有任何引數，必須省略括弧。  
  
## <a name="remarks"></a>備註  
 所需`eventname`模組內宣告的事件名稱。 它會遵循 Visual Basic 變數的命名慣例。  
  
 如果事件尚未宣告就會引發在模組內，就會發生錯誤。 下列程式碼片段說明事件宣告和引發事件的程序。  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 您無法使用`RaiseEvent`引發模組中未明確宣告的事件。 例如，所有的表單繼承<xref:System.Windows.Forms.Control.Click>從事件<xref:System.Windows.Forms.Form?displayProperty=nameWithType>，無法升級使用`RaiseEvent`衍生表單中。 如果您宣告`Click`事件在表單的模組中，它會遮蔽表單的自己<xref:System.Windows.Forms.Control.Click>事件。 您仍然可以叫用的表單<xref:System.Windows.Forms.Control.Click>藉由呼叫的事件<xref:System.Windows.Forms.Control.OnClick%2A>方法。  
  
 根據預設，在 Visual Basic 中定義的事件會引發其事件處理常式，會建立 連線的順序。 因為可能會有事件`ByRef`參數，較晚連接的程序可能會收到已由先前的事件處理常式的參數。 事件處理常式執行之後，控制權會引發事件的副程式。  
  
> [!NOTE]
>  在宣告類別的建構函式內，應該不會引發非共用的事件。 雖然這類事件不會造成執行階段錯誤，因此可能無法由相關聯的事件處理常式攔截。 使用`Shared`修飾詞來建立共用的事件，如果您需要從建構函式引發事件。  
  
> [!NOTE]
>  您可以定義自訂事件，以變更事件的預設行為。 自訂事件，如`RaiseEvent`陳述式會叫用事件的`RaiseEvent`存取子。 如需有關自訂事件的詳細資訊，請參閱 < [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用事件以從 10 秒到 0 秒倒數計時。 程式碼將說明數個事件相關的方法、 屬性和陳述式，包括`RaiseEvent`陳述式。  
  
 引發事件的類別是事件來源，處理事件的方法為事件處理常式。 事件來源對於它所產生的事件可以有多個處理常式。 當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。  
  
 此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。 當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
 
  `Form1` 的程式碼會指定表單的初始和終止狀態。 它也包含引發事件時執行的程式碼。  
  
 若要使用此範例中，開啟新的 Windows 應用程式專案中，加入名為按鈕`Button1`和名為文字方塊`TextBox1`主要表單名為`Form1`。 然後以滑鼠右鍵按一下表單，並按一下**檢視程式碼**程式碼編輯器開啟。  
  
 新增`WithEvents`變數的宣告區段`Form1`類別。  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  
 將下列程式碼加入至 `Form1` 的程式碼。 取代任何重複的程序可能會存在，這類`Form_Load`，或`Button_Click`。  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 按 F5 以執行上述範例中，並按一下 [] 按鈕**啟動**。 第一個文字方塊會開始倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
> [!NOTE]
>  `My.Application.DoEvents`方法不會處理事件中完全相同的方式像表單一樣。 若要允許表單以直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱 < [Managed 執行緒處理](../../../standard/threading/index.md)。  
  
## <a name="see-also"></a>另請參閱
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
