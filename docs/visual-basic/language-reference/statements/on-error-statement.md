---
title: On Error 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: d62c2ba1849b7015ed877d503220026a2dfeff57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353811"
---
# <a name="on-error-statement-visual-basic"></a>On Error 陳述式 (Visual Basic)
啟用錯誤處理常式，並在程式中指定常式的位置;也可以用來停用錯誤處理常式。 `On Error` 語句用於非結構化錯誤處理中，而且可以用來取代結構化例外狀況處理。 [結構化例外狀況處理](../../../standard/exceptions/index.md)內建于 .net 中，通常更有效率，而且在處理應用程式中的執行階段錯誤時建議使用。

 如果沒有錯誤處理或例外狀況處理，則發生的任何執行階段錯誤都是嚴重的：會顯示錯誤訊息，並停止執行。

> [!NOTE]
> `Error` 關鍵字也用於[Error 語句](../../../visual-basic/language-reference/statements/error-statement.md)，這是為了回溯相容性所支援。

## <a name="syntax"></a>語法

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`GoTo`*行*|啟用在必要*行*引數中指定的行開始的錯誤處理常式。 *Line*引數是任何行標籤或行號。 如果發生執行階段錯誤，請將分支控制到指定的行，使錯誤處理常式變成作用中。 指定的行必須與 `On Error` 語句位於相同的程式中，否則會發生編譯時期錯誤。|
|`GoTo 0`|停用目前程式中已啟用的錯誤處理常式，並將它重設為 `Nothing`。|
|`GoTo -1`|停用目前程式中已啟用的例外狀況，並將它重設為 `Nothing`。|
|`Resume Next`|指定發生執行階段錯誤時，控制權會移至緊接在發生錯誤的語句之後的語句，並從該點繼續執行。 存取物件時，請使用此表單，而不是 `On Error GoTo`。|

## <a name="remarks"></a>備註

> [!NOTE]
> 我們建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外狀況處理和 `On Error` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。

 「已啟用」錯誤處理常式是由 `On Error` 語句開啟的。 「作用中」錯誤處理常式是已啟用的處理常式，正在處理錯誤。

 如果錯誤處理常式處於作用中狀態時發生錯誤（發生錯誤和 `Resume`、`Exit Sub`、`Exit Function`或 `Exit Property` 語句），則目前程式的錯誤處理常式無法處理錯誤。 控制項會回到呼叫程式。
  
 如果呼叫程式具有已啟用的錯誤處理常式，就會啟動以處理錯誤。 如果呼叫程式的錯誤處理常式也是作用中，則控制權會透過先前的呼叫程式回傳，直到找到已啟用但非使用中的錯誤處理常式為止。 如果找不到這類錯誤處理常式，則錯誤在實際發生的時間點是嚴重的。
  
 每次錯誤處理常式將控制權回傳給呼叫的進程時，該程式就會成為目前的程式。 一旦任何程式中的錯誤處理常式處理錯誤，就會在 `Resume` 語句所指定之點的目前程式中繼續執行。
  
> [!NOTE]
> 錯誤處理常式不是 `Sub` 程式或 `Function` 的程式。 它是以線條標籤或行號標記的程式碼區段。
  
## <a name="number-property"></a>Number 屬性
 錯誤處理常式會依賴 `Err` 物件的 `Number` 屬性中的值，以判斷錯誤的原因。 常式應該先測試或儲存 `Err` 物件中的相關屬性值，然後才會發生任何其他錯誤，或呼叫可能造成錯誤的程式之前。 `Err` 物件中的屬性值只會反映最近的錯誤。 與 `Err.Number` 相關聯的錯誤訊息包含在 `Err.Description`中。  
  
## <a name="throw-statement"></a>Throw 陳述式  
 `Err.Raise` 方法引發的錯誤會將 `Exception` 屬性設定為 <xref:System.Exception> 類別的新建立實例。 為了支援引發衍生的例外狀況類型的例外狀況，語言中支援 `Throw` 語句。 這會採用單一參數，也就是要擲回的例外狀況實例。 下列範例顯示如何將這些功能與現有的例外狀況處理支援搭配使用：

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 請注意，不論例外狀況類別為何，`On Error GoTo` 語句都會捕捉所有錯誤。
  
## <a name="on-error-resume-next"></a>On Error Resume Next
 `On Error Resume Next` 會導致執行緊接在導致執行階段錯誤的語句之後的語句後面，或是緊接在包含 `On Error Resume Next` 語句的程式之後的最後一個呼叫後面的語句繼續進行。 即使執行階段錯誤，此語句仍可繼續執行。 您可以將錯誤處理常式放在發生錯誤的位置，而不是將控制權轉移到程式內的另一個位置。 呼叫另一個程式時，`On Error Resume Next` 語句會變成非作用中，因此，如果您想要在該常式內進行內嵌錯誤處理，則應該在每個呼叫的常式中執行 `On Error Resume Next` 語句。
  
> [!NOTE]
> 在處理存取其他物件期間所產生的錯誤時，最好能夠 `On Error GoTo` `On Error Resume Next` 結構。 在每次與物件互動後檢查 `Err`，會移除程式碼所存取的物件不明確。 您可以確定哪個物件將錯誤碼放在 `Err.Number`中，以及最初產生錯誤的物件（在 `Err.Source`中指定的物件）。

## <a name="on-error-goto-0"></a>On Error GoTo 0
 `On Error GoTo 0` 會停用目前程式中的錯誤處理。 它不會將第0行指定為錯誤處理常式代碼的開頭，即使套裝程式含編號為0的行。 如果沒有 `On Error GoTo 0` 語句，當程式結束時，就會自動停用錯誤處理常式。

## <a name="on-error-goto--1"></a>發生錯誤時為-1
 `On Error GoTo -1` 停用目前程式中的例外狀況。 它不會指定行-1 做為錯誤處理常式代碼的開頭，即使套裝程式含編號為-1 的行。 如果沒有 `On Error GoTo -1` 語句，當程式結束時，就會自動停用例外狀況。

 若要防止錯誤處理常式代碼在未發生錯誤時執行，請將 `Exit Sub`、`Exit Function`或 `Exit Property` 語句立即放在錯誤處理常式之前，如下列片段所示：

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 在這裡，錯誤處理常式代碼會遵循 `Exit Sub` 語句，並在 `End Sub` 語句之前，將它與程式流程分開。 您可以將錯誤處理常式代碼放在程式中的任何位置。

## <a name="untrapped-errors"></a>Untrapped 錯誤
 當物件當做可執行檔執行時，物件中的 Untrapped 錯誤會傳回給控制應用程式。 在開發環境中，只有在設定適當的選項時，才會將 untrapped 錯誤傳回給控制應用程式。 請參閱主應用程式的檔，以瞭解在調試過程中應該設定哪些選項、如何設定它們，以及主機是否可以建立類別的描述。

 如果您建立的物件會存取其他物件，您應該嘗試處理其傳回的任何未處理錯誤。 如果您無法這樣做，請將 `Err.Number` 中的錯誤碼對應至您自己的其中一個錯誤，然後將它們傳回給物件的呼叫者。 您應該將錯誤碼新增至 `VbObjectError` 常數來指定錯誤。 例如，如果您的錯誤碼為1052，請將其指派如下：

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> 呼叫 Windows 動態連結程式庫（Dll）期間發生系統錯誤，並不會引發例外狀況，也無法在 Visual Basic 錯誤捕捉時加以攔截。 呼叫 DLL 函式時，您應該檢查每個傳回值是否成功或失敗（根據 API 規格），如果發生失敗，請檢查 `Err` 物件的 `LastDLLError` 屬性中的值。

## <a name="example"></a>範例
 這個範例會先使用 `On Error GoTo` 語句來指定程式中的錯誤處理常式位置。 在此範例中，嘗試零除會產生錯誤號碼6。 錯誤會在錯誤處理常式中處理，然後再將控制權傳回給造成錯誤的語句。 `On Error GoTo 0` 語句會關閉錯誤捕捉。 然後，使用 `On Error Resume Next` 語句來延遲錯誤捕捉，讓下一個語句所產生之錯誤的內容可以知道特定。 請注意，在處理錯誤之後，`Err.Clear` 用來清除 `Err` 物件的屬性。

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>需求
 **命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)

 **元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)
- [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
