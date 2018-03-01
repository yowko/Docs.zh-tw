---
title: "On Error 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96baa5d91d0a600b84ed832fb1e3b1ed71a9d89d
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="on-error-statement-visual-basic"></a>On Error 陳述式 (Visual Basic)
啟用錯誤處理常式，並指定位置的程序; 內的常式也可以用來停用錯誤處理常式。  
  
 不需要錯誤處理發生的任何執行階段錯誤是嚴重錯誤： 會顯示錯誤訊息，並停止執行。  
  
 可能的話，我們建議您在使用結構化例外狀況處理程式碼中，而不是使用非結構化例外狀況處理和`On Error`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  `Error`關鍵字也用於[Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)，這支援回溯相容性。  
  
## <a name="syntax"></a>語法  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`GoTo` `line`|可讓啟動指定在所需的那一行的錯誤處理常式`line`引數。 `line`引數是任何行標籤或行號。 如果發生執行階段錯誤，控制移至指定的行，進行錯誤處理常式的使用中。 指定的行必須位於相同的程序`On Error`陳述式或編譯時期錯誤發生。|  
|`GoTo` 0|停用目前的程序中已啟用的錯誤處理常式，並將它重設`Nothing`。|  
|`GoTo` -1|停用目前的程序中啟用例外狀況，並將它重設`Nothing`。|  
|`Resume Next`|指定執行階段錯誤發生時，緊接著此陳述式位置發生錯誤，並從該時間點繼續執行的陳述式會控制。 使用此表單而非`On Error GoTo`存取物件時。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  我們建議您使用結構化例外狀況處理，可能的話，程式碼中的，而不是使用非結構化例外狀況處理和`On Error`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 "Enabled"的錯誤處理常式是會開啟`On Error`陳述式。 「 作用中 」 的錯誤處理常式是啟用的處理常式，而且正在處理錯誤。  
  
 錯誤處理常式時，如果發生錯誤 (之間發生錯誤而`Resume`， `Exit Sub`， `Exit Function`，或`Exit Property`陳述式)，目前的程序錯誤處理常式無法處理錯誤。 控制權會傳回呼叫程序。  
  
 如果呼叫的程序已啟用的錯誤處理常式，則會啟動以處理錯誤。 如果呼叫的程序錯誤處理常式也是使用中，控制權會傳回到先前的呼叫程序找到已啟用，但非作用中，錯誤處理常式之前。 如果找到這類錯誤處理常式，就是它實際發生的點嚴重的錯誤。  
  
 錯誤處理常式會將控制項傳遞至呼叫的程序中，每次該程序會成為目前的程序。 一旦處理錯誤，錯誤處理常式中的任何程序，在目前的程序中所指定的點就會繼續執行`Resume`陳述式。  
  
> [!NOTE]
>  錯誤處理常式不是`Sub`程序或`Function`程序。 它是一段程式碼所標記的行標籤或行號。  
  
## <a name="number-property"></a>Number 屬性  
 錯誤處理常式依賴中的值`Number`屬性`Err`物件，以判斷錯誤的原因。 此常式應該測試或儲存在相關的屬性值`Err`物件就會發生任何其他錯誤，或可能會導致程序之前的錯誤稱為之前。 屬性值在`Err`物件會反映最近的錯誤。 錯誤訊息相關聯`Err.Number`包含於`Err.Description`。  
  
## <a name="throw-statement"></a>Throw 陳述式  
 引發錯誤`Err.Raise`方法會設定`Exception`新建立的執行個體的屬性<xref:System.Exception>類別。 為了支援在引發例外狀況的衍生的例外狀況類型、`Throw`語言支援陳述式。 這會採用單一參數，會擲回的例外狀況執行個體。 下列範例會示範如何使用這些功能，與現有的例外狀況處理支援：  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 請注意，`On Error GoTo`陳述式的設陷不論例外狀況類別的所有錯誤。  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next`導致執行動作繼續緊接造成執行階段錯誤的陳述式的陳述式，或緊接的最新的陳述式呼叫從程序包含`On Error Resume Next`陳述式。 這個陳述式可讓您忽略執行階段錯誤繼續執行。 您可以將錯誤處理常式就會發生錯誤，而不會將控制權傳輸至另一個程序內的位置。 `On Error Resume Next`陳述式變成非作用中呼叫另一個程序時，因此，您應該執行`On Error Resume Next`中每個陳述式呼叫常式，如果您想要內嵌錯誤處理該常式內。  
  
> [!NOTE]
>  `On Error Resume Next`建構可能會比`On Error GoTo`處理其他物件的存取權期間所產生的錯誤時。 檢查`Err`之後每個互動的物件移除的物件存取的程式碼的模稜兩可。 您可以確定哪一個物件放在錯誤碼`Err.Number`，以及哪些物件最初產生的錯誤 (中指定的物件`Err.Source`)。  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0`停用目前的程序中的錯誤處理。 它不會作為的錯誤處理程式碼中，指定第 0 行，即使程序包含行號 0。 不含`On Error GoTo 0`陳述式中，錯誤處理常式會自動停用程序結束時。  
  
## <a name="on-error-goto--1"></a>On Error GoTo-1  
 `On Error GoTo -1`停用目前的程序中的例外狀況。 它未指定行-1 開始的錯誤處理程式碼，即使此程序包含行號-1。 不含`On Error GoTo -1`陳述式中，例外狀況會自動停用程序結束時。  
  
 若要防止錯誤處理程式碼執行時沒有發生任何錯誤，加上`Exit Sub`， `Exit Function`，或`Exit Property`陳述式之前的錯誤處理常式，如下列片段所示：  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 錯誤處理程式碼會遵循此處`Exit Sub`陳述式，而且前面出現`End Sub`分開的程序流程的陳述式。 您可以在程序的任意位置放置錯誤處理程式碼。  
  
## <a name="untrapped-errors"></a>設陷的錯誤  
 物件的可執行檔以執行時，物件中的設陷的錯誤會傳回控制的應用程式。 在開發環境中，未設陷的錯誤會傳回控制應用程式必須設定適當的選項。 參閱主應用程式的文件選項都應該是設定在偵錯、 如何設定它們，和主機是否可以建立類別的描述。  
  
 如果您建立存取其他物件的物件，您應該嘗試處理傳遞回任何未處理的錯誤。 如果您不能對應中的錯誤代碼`Err.Number`您自己的錯誤，然後階段的其中一個送回給呼叫者的物件。 您應該加入您錯誤的程式碼，以指定您的錯誤`VbObjectError`常數。 例如，如果您的錯誤代碼是 1052年，將它指派，如下所示：  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  系統 Windows 動態連結程式庫 (Dll) 的呼叫期間發生的錯誤不會引發例外狀況，並不能與 Visual Basic 錯誤截取截取。 在呼叫 DLL 函式時，您應該檢查成功或失敗 （根據應用程式開發介面規格），每個傳回值，萬一故障，請檢查值`Err`物件的`LastDLLError`屬性。  
  
## <a name="example"></a>範例  
 這個範例會先使用`On Error GoTo`陳述式來指定的錯誤處理常式的程序內的位置。 在範例中，嘗試除以零會產生錯誤的數字 6。 在錯誤處理常式中，處理錯誤，然後將控制權傳回給造成錯誤的陳述式。 `On Error GoTo 0`陳述式會關閉錯誤設陷。 然後在`On Error Resume Next`陳述式用來延遲錯誤捕捉使某些已知的內容下一個陳述式所產生的錯誤。 請注意，`Err.Clear`用來清除`Err`錯誤處理之後，物件的屬性。  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
