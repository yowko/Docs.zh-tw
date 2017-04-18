---
title: "RaiseEvent 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 059b1347c4a35b896f5aa19cadb28fbceb8b25c9
ms.lasthandoff: 03/13/2017

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
 選擇項。 以逗號分隔的變數、 陣列或運算式清單。 `argumentlist`引數必須括在括號括住。 如果不有任何引數，必須省略括號。  
  
## <a name="remarks"></a>備註  
 必要`eventname`在模組中宣告的事件名稱。 它會遵循 Visual Basic 變數命名慣例。  
  
 如果尚未在引發此模組中宣告事件，就會發生錯誤。 下列程式碼片段將說明事件宣告和引發事件的程序。  
  
 [!code-vb[VbVbalrEvents #&37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 您不能使用`RaiseEvent`引發模組中未明確宣告的事件。 例如，所有的表單繼承<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Form?displayProperty=fullName>，無法升級使用`RaiseEvent`衍生格式中。</xref:System.Windows.Forms.Form?displayProperty=fullName> </xref:System.Windows.Forms.Control.Click> 如果您宣告`Click`事件在表單的模組，它會遮蔽表單的自己<xref:System.Windows.Forms.Control.Click>事件。</xref:System.Windows.Forms.Control.Click> 您仍然可以叫用表單的<xref:System.Windows.Forms.Control.Click>事件，藉由呼叫<xref:System.Windows.Forms.Control.OnClick%2A>方法。</xref:System.Windows.Forms.Control.OnClick%2A> </xref:System.Windows.Forms.Control.Click>  
  
 根據預設，在 Visual Basic 中定義的事件會引發其事件處理常式，建立連接的順序。 因為事件可以有`ByRef`參數，較晚連接的處理程序可能會收到已由先前的事件處理常式的參數。 事件處理常式執行之後，控制權會傳回引發事件的副程式。  
  
> [!NOTE]
>  在宣告的類別的建構函式應該不會引發非共用的事件。 雖然這類事件不會造成執行階段錯誤，因此可能無法相關聯的事件處理常式攔截。 使用`Shared`修飾詞，以建立共用的事件，若要引發事件，從建構函式。  
  
> [!NOTE]
>  您可以定義自訂事件來變更事件的預設行為。 自訂事件，`RaiseEvent`陳述式會叫用此事件`RaiseEvent`存取子。 如需自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用事件以從 10 秒到 0 秒倒數計時。 程式碼將說明幾個事件相關的方法、 屬性和陳述式，包括`RaiseEvent`陳述式。  
  
 引發事件的類別是事件來源，處理事件的方法為事件處理常式。 事件來源對於它所產生的事件可以有多個處理常式。 當類別引發事件時，該事件是在每個類別 (已被選擇來處理該物件執行個體的事件) 上引發。  
  
 此範例也會使用表單 (`Form1`) 與按鈕 (`Button1`) 和文字方塊 (`TextBox1`)。 當您按一下按鈕時時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
 `Form1` 的程式碼會指定表單的初始和終止狀態。 它也包含引發事件時執行的程式碼。  
  
 若要使用此範例中，開啟新的 Windows 應用程式專案中，加入名為按鈕`Button1`和名為文字方塊`TextBox1`主表單中，名為`Form1`。 然後以滑鼠右鍵按一下表單，並按一下 **檢視程式碼**開啟程式碼編輯器。  
  
 新增`WithEvents`變數的宣告區段`Form1`類別。  
  
 [!code-vb[VbVbalrEvents #&14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>範例  
 將下列程式碼加入至 `Form1` 的程式碼。 取代重複的程序可能存在，例如`Form_Load`，或`Button_Click`。  
  
 [!code-vb[VbVbalrEvents #&15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 按 F5 以執行上述範例中，並按一下 按鈕**啟動**。 第一個文字方塊會開始倒數計時。 在經過完整時間 (10 秒) 之後，第一個文字方塊會顯示 [完成]。  
  
> [!NOTE]
>  `My.Application.DoEvents`方法不會處理事件的相同方式表單一樣。 若要讓表單直接處理事件，您可以使用多執行緒處理。 如需詳細資訊，請參閱[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)   
 [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md)
