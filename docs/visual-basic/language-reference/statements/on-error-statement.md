---
title: On Error 陳述式 (Visual Basic)
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
ms.openlocfilehash: 0a5a5261e6b71178adce02a5635c1f91a1469f3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834258"
---
# <a name="on-error-statement-visual-basic"></a>On Error 陳述式 (Visual Basic)
啟用錯誤處理常式，並指定位置的程序; 中的常式也可以用來停用錯誤處理常式。  
  
 沒有錯誤處理，是嚴重錯誤發生的任何執行階段錯誤： 會顯示錯誤訊息，並停止執行。  
  
 可能的話，我們建議您同時使用結構化例外狀況，在您的程式碼中處理，而不是使用非結構化例外狀況處理和`On Error`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  `Error`關鍵字也用於[Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)，這支援回溯相容性。  
  
## <a name="syntax"></a>語法  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`GoTo` `line`|啟用錯誤處理常式會指定在所需的那一行`line`引數。 `line`引數是任何行標籤或行號。 如果發生執行階段錯誤，控制權會移至指定的行，使錯誤處理常式處於作用中。 指定的行必須位於相同的程序，為`On Error`陳述式或在編譯階段錯誤發生。|  
|`GoTo` 0|停用目前的程序中的已啟用的錯誤處理常式，並將它以重設`Nothing`。|  
|`GoTo` -1|停用已啟用的例外狀況，在目前的程序，並將它以重設`Nothing`。|  
|`Resume Next`|指定執行階段錯誤時，緊接著此陳述式，發生錯誤，並從該點繼續執行的陳述式會控制。 使用這種形式而非`On Error GoTo`存取物件時。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  我們建議您改用可能的話，您的程式碼中的結構化例外狀況處理，而不是使用非結構化例外狀況處理和`On Error`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 「 已啟用 」 的錯誤處理常式是會開啟`On Error`陳述式。 「 作用中 」 的錯誤處理常式是啟用的處理常式，而且正在處理錯誤。  
  
 錯誤處理常式處於作用中時，如果發生錯誤 (錯誤的相符項目之間， `Resume`， `Exit Sub`， `Exit Function`，或`Exit Property`陳述式)，目前的程序錯誤處理常式無法處理錯誤。 控制權會傳回呼叫程序。  
  
 如果呼叫的程序已啟用的錯誤處理常式，它會啟動處理錯誤。 如果呼叫的程序錯誤處理常式也正在使用時，控制權會傳回到前一個呼叫的程序直到找到已啟用，但非作用中，錯誤處理常式。 如果不找到任何這類的錯誤處理常式，就是它實際發生的時候嚴重的錯誤。  
  
 錯誤處理常式會將控制項傳遞至呼叫的程序中，每次該程序會成為目前的程序。 在目前的程序中所指定的位置之後的任何程序中的錯誤處理常式已處理的錯誤，繼續執行`Resume`陳述式。  
  
> [!NOTE]
>  錯誤處理常式不是`Sub`程序或`Function`程序。 它是一段線條標籤或行號標示的程式碼。  
  
## <a name="number-property"></a>Number 屬性  
 錯誤處理常式依賴中的值`Number`屬性`Err`物件來判定錯誤的原因。 常式應該測試或儲存在相關的屬性值`Err`物件之前就會發生任何其他錯誤，或呼叫之前的程序，可能會導致錯誤。 中的屬性值`Err`物件會反映最近的錯誤。 錯誤訊息相關聯`Err.Number`包含在`Err.Description`。  
  
## <a name="throw-statement"></a>Throw 陳述式  
 引發的錯誤`Err.Raise`方法會設定`Exception`新建立的執行個體的內容<xref:System.Exception>類別。 若要支援引發的例外狀況衍生的例外狀況類型，`Throw`語言支援陳述式。 這會是擲回的例外狀況執行個體的單一參數。 下列範例顯示如何使用這些功能，與現有的例外狀況處理支援：  
  
 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 請注意，`On Error GoTo`陳述式的設陷不論例外狀況類別的所有錯誤。  
  
## <a name="on-error-resume-next"></a>On Error Resume 下一步  
 `On Error Resume Next` 導致執行動作繼續緊接造成執行階段錯誤的陳述式的陳述式，或緊接最新的陳述式中，呼叫從程序包含`On Error Resume Next`陳述式。 此陳述式可讓執行階段錯誤忽略並繼續執行的執行。 您可以將錯誤處理常式就會發生錯誤，而不是將控制權傳輸至另一個程序內的位置。 `On Error Resume Next`陳述式變成非作用中呼叫另一個程序時，所以您應該執行`On Error Resume Next`中每個陳述式呼叫的常式，如果您想要內嵌的錯誤，該常式內處理。  
  
> [!NOTE]
>  `On Error Resume Next`建構，可能會偏好以`On Error GoTo`處理其他物件的存取權期間所產生的錯誤時。 檢查`Err`之後每個互動的物件中移除哪些程式碼存取物件的模稜兩可。 您可以確定哪些物件放置在中的錯誤碼`Err.Number`，以及哪個物件最初產生錯誤 (指定的物件`Err.Source`)。  
  
## <a name="on-error-goto-0"></a>在 Error GoTo 0  
 `On Error GoTo 0` 停用目前的程序中的錯誤處理。 它不做為起點的錯誤處理程式碼中，指定第 0 行，即使程序包含行編號為 0。 不含`On Error GoTo 0`陳述式中，錯誤處理常式的程序結束時自動停用。  
  
## <a name="on-error-goto--1"></a>在 Error GoTo-1  
 `On Error GoTo -1` 停用目前的程序中的例外狀況。 它未指定-1 的列開頭的錯誤處理程式碼中，即使程序包含行號為-1。 不含`On Error GoTo -1`陳述式中，例外狀況的程序結束時自動停用。  
  
 若要防止錯誤處理程式碼執行時沒有發生任何錯誤，請將`Exit Sub`， `Exit Function`，或`Exit Property`陳述式之前的錯誤處理常式，如下列片段所示：  
  
 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]  
  
 在這裡，錯誤處理程式碼會遵循`Exit Sub`陳述式，而且前面出現`End Sub`將資料流程的程序的陳述式。 您可以在程序的任意位置放置錯誤處理程式碼。  
  
## <a name="untrapped-errors"></a>未設陷的錯誤  
 當物件以可執行檔執行時，物件中的設陷的錯誤會傳回控制的應用程式。 在開發環境中，未設陷的錯誤會傳回要控制的應用程式，設定適當的選項，才。 參閱主應用程式的描述，其中選項應在偵錯期間的設定、 如何設定它們，且主機是否可以建立類別的文件。  
  
 如果您建立存取其他物件的物件時，您應該嘗試處理它們將傳回的任何未處理的錯誤。 如果您不能對應中的錯誤碼`Err.Number`其中一個您自己的錯誤，然後傳遞送回呼叫端的物件。 您應該藉由加入您的錯誤程式碼，以指定您的錯誤`VbObjectError`常數。 例如，如果您的錯誤碼是 1052年，將它指派，如下所示：  
  
 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]  
  
> [!CAUTION]
>  在 Windows 動態連結程式庫 (Dll) 的呼叫期間的系統錯誤不會引發例外狀況，並不能與 Visual Basic 錯誤截取截取。 在呼叫 DLL 函式時，您應該檢查每個傳回的值為成功或失敗 （根據 API 規格中），並發生問題時，請檢查值`Err`物件的`LastDLLError`屬性。  
  
## <a name="example"></a>範例  
 此範例會先使用`On Error GoTo`陳述式來指定錯誤處理常式的程序內的位置。 在範例中，嘗試除以零會產生錯誤代碼 6。 在錯誤處理常式中，已處理此錯誤，然後將控制項傳回給造成錯誤的陳述式。 `On Error GoTo 0`陳述式會關閉錯誤捕捉。 則`On Error Resume Next`陳述式用來延遲錯誤捕捉，以便可以針對特定已知的內容下一個陳述式所產生的錯誤。 請注意，`Err.Clear`用來清除`Err`之後已處理此錯誤的物件的屬性。  
  
 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]  
  
## <a name="requirements"></a>需求  
 **命名空間：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件：** Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)
- [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
