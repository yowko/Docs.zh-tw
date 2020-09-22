---
title: RaiseEvent 陳述式
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
ms.openlocfilehash: 13d86aad8b68391f7effe2f6637adc68d8a3b59a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872020"
---
# <a name="raiseevent-statement"></a>RaiseEvent 陳述式

觸發在類別、表單或檔內的模組層級宣告的事件。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>組件  

 `eventname`  
 必要。 要觸發的事件名稱。  
  
 `argumentlist`  
 選擇性。 變數、陣列或運算式的逗號分隔清單。 `argumentlist`引數必須以括弧括住。 如果沒有引數，則必須省略括弧。  
  
## <a name="remarks"></a>備註  

 所需的 `eventname` 是在模組內宣告的事件名稱。 它會遵循 Visual Basic 變數命名慣例。  
  
 如果事件尚未在引發的模組內宣告，就會發生錯誤。 下列程式碼片段說明事件宣告和引發事件的程式。  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 您無法使用 `RaiseEvent` 來引發未在模組中明確宣告的事件。 例如，所有表單都繼承的 <xref:System.Windows.Forms.Control.Click> 事件 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> ，無法使用 `RaiseEvent` 衍生的表單來引發。 如果您 `Click` 在表單模組中宣告事件，它會遮蔽表單本身的 <xref:System.Windows.Forms.Control.Click> 事件。 您仍然可以藉 <xref:System.Windows.Forms.Control.Click> 由呼叫方法來叫用表單的事件 <xref:System.Windows.Forms.Control.OnClick%2A> 。  
  
 根據預設，Visual Basic 中定義的事件會依照建立連接的順序引發其事件處理常式。 因為事件可以有 `ByRef` 參數，所以晚期連接的進程可能會接收先前的事件處理常式已變更的參數。 在事件處理常式執行之後，控制權會傳回給引發事件的副程式。  
  
> [!NOTE]
> 非共用事件不應該在宣告它們的類別的函式內引發。 雖然這類事件不會造成執行階段錯誤，但它們可能無法由相關聯的事件處理常式捕捉。 `Shared`如果您需要從函式引發事件，請使用修飾詞來建立共用事件。  
  
> [!NOTE]
> 您可以藉由定義自訂事件來變更事件的預設行為。 針對自訂事件，語句會叫用 `RaiseEvent` 事件的 `RaiseEvent` 存取子。 如需有關自訂事件的詳細資訊，請參閱 [事件語句](event-statement.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用事件以從 10 秒到 0 秒倒數計時。 此程式碼說明數個事件相關的方法、屬性和語句，包括 `RaiseEvent` 語句。  
  
 引發事件的類別是事件來源，處理事件的方法為事件處理常式。 事件來源對於它所產生的事件可以有多個處理常式。 當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。  
  
 此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。 當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
 `Form1` 的程式碼會指定表單的初始和終止狀態。 它也包含引發事件時執行的程式碼。  
  
 若要使用此範例，請開啟新的 Windows 應用程式專案，並將名為 `Button1` 的按鈕和名為的文字方塊，加入名 `TextBox1` 為的主表單 `Form1` 。 然後以滑鼠右鍵按一下表單，然後按一下 [ **流覽程式碼** ] 以開啟程式碼編輯器。  
  
 將 `WithEvents` 變數加入至類別的宣告區段 `Form1` 。  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>範例  

 將下列程式碼加入至 `Form1` 的程式碼。 取代可能存在的任何重複程式，例如 `Form_Load` 或 `Button_Click` 。  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 按 F5 執行上述範例，然後按一下標示為 [ **開始**] 的按鈕。 第一個文字方塊會開始倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
> [!NOTE]
> `My.Application.DoEvents`方法不會以與表單完全相同的方式來處理事件。 若要允許表單直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱 [Managed 執行緒](../../../standard/threading/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [事件](../../programming-guide/language-features/events/index.md)
- [Event 陳述式](event-statement.md)
- [AddHandler 陳述式](addhandler-statement.md)
- [RemoveHandler 陳述式](removehandler-statement.md)
- [處理](handles-clause.md)
