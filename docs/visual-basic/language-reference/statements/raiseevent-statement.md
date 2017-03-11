---
title: "RaiseEvent Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RaiseEventMethod"
  - "vb.RaiseEvent"
  - "RaiseEvent"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising events, RaiseEvent statement"
  - "RaiseEvent statement"
  - "event handlers, connecting events to"
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# RaiseEvent Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在模組層次觸發 \(Trigger\) 類別、表單或文件內所宣告的事件。  
  
## 語法  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## 組件  
 `eventname`  
 必要項。  要觸發事件的名稱。  
  
 `argumentlist`  
 選擇項。  變數、陣列或運算式的清單，項目之間以逗號 \( , \) 分隔。  `argumentlist` 引數必須加上括號。  如果沒有引數的話，就必須省略括號。  
  
## 備註  
 必要項 `eventname` 是在模組內宣告之事件的名稱。  這是依照 Visual Basic 變數命名規範來命名的。  
  
 如果事件不是在引發它的模組內宣告的話，則會發生錯誤。  下列程式碼片段會說明事件宣告和引發事件的程序。  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#37)]  
  
 不能使用 `RaiseEvent` 引發未於模組中明確宣告的事件。  例如，如果所有表單都是從 <xref:System.Windows.Forms.Form?displayProperty=fullName> 繼承 <xref:System.Windows.Forms.Control.Click> 事件，就不能在衍生表單中使用 `RaiseEvent` 引發該事件。  如果您在表單模組中宣告 `Click` 事件，則會遮蔽表單本身的 <xref:System.Windows.Forms.Control.Click> 事件。  您仍舊可以呼叫 <xref:System.Windows.Forms.Control.OnClick%2A> 方法，以便叫用 \(Invoke\) 表單的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
 根據預設，Visual Basic 中定義的事件會以連接的建立順序，引發本身的事件處理常式。  由於事件可以包含 `ByRef` 參數，因此較晚連接的處理序 \(Process\) 可能會收到由先前的事件處理常式變更後的參數。  在執行事件處理常式後，控制項就會回到引發事件的副程式。  
  
> [!NOTE]
>  非共用的事件不應在宣告它的類別建構函式 \(Constructor\) 中引發。  雖然此類事件不會造成執行階段錯誤，但可能無法由相關聯的事件處理常式攔截。  若需從建構函式中引發事件，請用 `Shared` 修飾詞 \(Modifier\) 建立共用事件。  
  
> [!NOTE]
>  您可以定義自訂事件，藉以變更事件的預設行為。  使用自訂事件時，`RaiseEvent` 陳述式會叫用事件的 `RaiseEvent` 存取子。  如需自訂事件的詳細資訊，請參閱[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## 範例  
 下列範例會使用事件從 10 秒到 0 倒數讀秒。  此程式碼說明數個事件相關的方法、屬性和陳述式，其中包括 `RaiseEvent` 陳述式。  
  
 引發事件的類別是事件來源 \(Event Source\)，而處理事件的方法則是事件處理常式。  一個事件來源可有多個處理常式來處理產生的事件。  當類別引發事件時，這個事件便會在每個選定為物件執行個體處理事件的類別上引發。  
  
 這個範例也會使用包含一個按鈕 \(`Button1`\) 和一個文字方塊 \(`TextBox1`\) 的表單 \(`Form1`\)。  當您按一下按鈕時，第一個文字方塊會顯示從 10 秒到 0 秒的倒數計時。  整段時間 \(10 秒\) 結束時，第一個文字方塊會顯示「完成」。  
  
 `Form1` 的程式碼會指定表單的初始和終結狀態。  其中也包含引發事件時執行的程式碼。  
  
 若要使用這個範例，請開啟新的 Windows 應用程式專案，將一個按鈕 \(名為 `Button1`\) 和一個文字方塊 \(名為 `TextBox1`\) 加入至主要表單 \(名為 `Form1`\)。  然後以滑鼠右鍵按一下表單，再按 \[**檢視程式碼**\] 開啟程式碼編輯器。  
  
 將 `WithEvents` 變數加入至 `Form1` 類別的宣告區段中。  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#14)]  
  
## 範例  
 將下列程式碼加入至 `Form1` 的程式碼中：  取代任何可能存在的重複程序，例如 `Form_Load` 或 `Button_Click`。  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#15)]  
  
 按 F5 執行上述範例，再按標記為 \[**Start**\] 的按鈕。  第一個文字方塊會開始倒數計時。  整段時間 \(10 秒\) 結束時，第一個文字方塊會顯示「完成」。  
  
> [!NOTE]
>  `My.Application.DoEvents` 方法處理事件的方式和表單的方式不太一樣。  若要讓表單直接處理事件，您可以使用多執行緒處理。  如需詳細資訊，請參閱 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 請參閱  
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)