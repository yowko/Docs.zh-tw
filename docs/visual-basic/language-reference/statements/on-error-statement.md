---
title: "On Error Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.OnError"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, control flow"
  - "Resume Next statement"
  - "errors [Visual Basic], trapping"
  - "error handling, On Error statement"
  - "Next statement, On Error"
  - "control flow, branching"
  - "Error keyword"
  - "execution, conditional"
  - "Resume statement, and On Error statement"
  - "Error statement, and On Error statement"
  - "GoTo statement, and On Error statement"
  - "branching, on error"
  - "conditional statements, On Error"
  - "On Error statement, syntax"
  - "On keyword"
  - "run-time errors, handling"
  - "On Error statement"
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# On Error Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

啟用錯誤處理常式，並指定常式在程序中的位置；此外，也可用來停用錯誤處理常式。  
  
 如果不使用 `On Error` 陳述式，則所發生的任何執行階段錯誤都是嚴重錯誤，也就是說會顯示錯誤訊息並停止執行。  
  
 可能的話，我們建議您使用結構化的例外處理程式碼中，而不是使用非結構化的例外處理和`On Error`陳述式。  如需詳細資訊，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  `Error` 關鍵字也用於 [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)，支援回溯相容性 \(Backward Compatibility\)。  
  
## 語法  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`GoTo` `line`|啟用錯誤處理常式，並於必要項 `line` 引數中指定的程式行開始。  `line` 引數就是任何的行標籤 \(Label\) 或行號。  如果發生執行階段錯誤，則控制權會移至指定的程式行，使錯誤處理常式啟動。  指定的程式行必須在與 `On Error` 陳述式相同的程序中，否則將發生編譯時期錯誤。|  
|`GoTo` 0|停用目前程序中啟用的錯誤處理常式，並將之重設為 `Nothing`。|  
|`GoTo` \-1|停用目前程序中啟用的例外狀況，並將之重設為 `Nothing`。|  
|`Resume Next`|指定發生執行階段錯誤時，控制權立即移至接在發生錯誤的陳述式之後的陳述式，並從該點繼續執行。  存取物件時，請使用這個格式，而不是 `On Error GoTo`。|  
  
## 備註  
  
> [!NOTE]
>  我們建議您使用結構化的例外處理，可能的話，程式碼中，而不是使用非結構化的例外處理和`On Error`陳述式。  如需詳細資訊，請參閱 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 「啟用的」錯誤處理常式是指由 `On Error` 陳述式所開啟的錯誤處理常式。  「使用中的」錯誤處理常式則是指正在處理錯誤之啟用的處理常式。  
  
 如果錯誤處理常式在使用中時發生錯誤 \(介於錯誤發生點與 `Resume`、`Exit Sub`、`Exit Function` 或 `Exit Property` 陳述式之間\)，則目前程序的錯誤處理常式無法處理這個錯誤。  控制權便回到呼叫程序。  
  
 如果呼叫程序含有啟用的錯誤處理常式，則會啟動處理這個錯誤。  此外，如果呼叫程序的錯誤處理常式也是在使用中，則控制權會傳回到先前的呼叫程序，直到找到啟用而非使用中的錯誤處理常式為止。  如果找不到上述的錯誤處理常式，則確實發生錯誤時，會是非常嚴重的錯誤。  
  
 每當錯誤處理常式傳回控制權到呼叫程序時，該程序會成為目前的程序。  在任何程序中，錯誤處理常式一旦處理錯誤，便會從 `Resume` 陳述式指定點的目前程序繼續執行。  
  
> [!NOTE]
>  錯誤處理常式並非是 `Sub` 程序或 `Function` 程序。  它是由行標籤或行號所標示的程式碼區段。  
  
## Number 屬性  
 錯誤處理常式會依據 `Err` 物件的 `Number` 屬性值，判斷造成錯誤的原因。  在任何其他錯誤發生之前，或在呼叫可能造成錯誤的程序之前，這個常式應會測試或儲存 `Err` 物件中的相關屬性值。  `Err` 物件中的屬性值僅反應最近的錯誤。  與 `Err.Number` 相關聯的錯誤訊息則包含在 `Err.Description` 中。  
  
## Throw 陳述式  
 以 `Err.Raise` 方法引發的錯誤會將 `Exception` 屬性設為新建立之 <xref:System.Exception> 類別的執行個體。  為能支援引發之衍生例外狀況類型的例外狀況，這個語言中支援 `Throw` 陳述式。  如此，會採用所擲回之例外狀況執行個體的單一參數。  下列範例顯示這些功能如何配合現存的例外狀況處理支援使用：  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 請注意，無論例外狀況類別為何，`On Error GoTo` 陳述式都會截獲所有錯誤。  
  
## On Error Resume Next  
 `On Error Resume Next` 從發生執行階段錯誤陳述式之後的陳述式繼續執行，或是從含有 `On Error Resume Next` 陳述式而最近才呼叫之程序後面的陳述式繼續執行。  這樣就可以不管執行階段錯誤而繼續執行。  您可以存放將會發生錯誤的錯誤處理常式，而不用將控制權轉移到程序內的其他位置。  呼叫另一個程序時，`On Error Resume Next` 陳述式將會停止使用，因此如果您想要使用常式中的內嵌 \(Inline\) 錯誤處理，則必須在每一個呼叫常式中執行 `On Error Resume Next` 陳述式。  
  
> [!NOTE]
>  處理存取其他物件時所產生的錯誤時，`On Error Resume Next` 建構可能比 `On Error GoTo` 更好用。  每次與一個物件互動後對 `Err` 進行檢查，可以剔除程式碼究竟是存取哪個物件所造成的語意模糊。  您可以確定將錯誤碼放到 `Err.Number` 中的物件，以及原本產生這個錯誤的物件 \(`Err.Source` 中指定的物件\)。  
  
## On Error GoTo 0  
 `On Error GoTo 0` 會停用目前程序中的錯誤處理。  它沒有將 0 行指定為錯誤處理程式碼的起始，即使程序含有編號為 0 的行也一樣。  若不使用 `On Error GoTo 0` 陳述式，程序結束時會自動停用錯誤處理常式。  
  
## On Error GoTo \-1  
 `On Error GoTo -1` 會停用目前程序中的例外狀況。  它並不是要將 \-1 行指定為錯誤處理程式碼的起始，即使程序含有編號為 \-1 的行也一樣。  如果沒有 `On Error GoTo -1` 陳述式，例外狀況會在程序結束時自動停用。  
  
 若要在沒有發生錯誤時，避免執行錯誤處理程式碼，請將 `Exit Sub`、`Exit Function` 或 `Exit Property` 陳述式放在錯誤處理常式前面，如下列片段：  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 此處的錯誤處理代碼接在 `Exit Sub` 陳述式之後，並在 `End Sub` 陳述式之前，以便將其與程序流程分開。  您可以將錯誤處理代碼放到程序中的任何位置。  
  
## 未截獲的錯誤  
 當該物件以執行檔的方式執行時，物件中的未設陷錯誤會回傳到進行控制的應用程式。  而在開發環境下，唯有設定了正確的選項，未設陷的錯誤才會回傳到控制應用程式。  如需偵錯時應設定的選項、選項的設定方式及主機是否可建立類別的詳細資訊，請參閱主應用程式的文件。  
  
 如果您建立存取其他物件的物件，則應設法處理這些物件回傳的任何未處理錯誤。  如果無法處理，請將 `Err.Number` 中的錯誤碼對應到您所擁有錯誤中的一項，然後將它們傳回給物件的呼叫端。  您應該將錯誤碼加入至 `VbObjectError` 常數，以便指定您的錯誤。  例如，如果您的錯誤代碼是 1052，請依下述進行指派：  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  呼叫 Windows 動態連結程式庫 \(DLL\) 時的系統錯誤並不會引發例外狀況發生，也無法隨著 Visual Basic 錯誤擷取被截獲。  呼叫 DLL 函式時，您應檢查每一個傳回值為成功或失敗 \(根據 API 規格\)，檢查結果若是失敗，請檢查 `Err` 物件的 `LastDLLError` 屬性值。  
  
## 範例  
 這個範例會先使用 `On Error GoTo` 陳述式指定錯誤處理常式在程序內的位置。  在範例中，除以零的嘗試會產生錯誤代碼 6。  會在錯誤處理常式中處理錯誤，再將控制項傳回造成錯誤的陳述式。  `On Error GoTo 0` 陳述式會關閉錯誤擷取。  接著使用 `On Error Resume Next` 陳述式來延遲錯誤設陷，如此可確定得知下一個陳述式產生的錯誤內容。  請注意，`Err.Clear` 是用於在處理錯誤之後清除 `Err` 物件的屬性。  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## 需求  
 **命名空間**：[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件**：Visual Basic 執行階段程式庫 \(在 Microsoft.VisualBasic.dll 中\)  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)