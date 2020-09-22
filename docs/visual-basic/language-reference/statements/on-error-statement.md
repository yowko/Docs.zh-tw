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
ms.openlocfilehash: 7e007d59292fc577c0c8927766423ba6f7896a71
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873185"
---
# <a name="on-error-statement-visual-basic"></a>On Error 陳述式 (Visual Basic)

啟用錯誤處理常式，並在程式內指定常式的位置;也可以用來停用錯誤處理常式。 `On Error`語句用於非結構化錯誤處理中，而且可以用來取代結構化例外狀況處理。 [結構化例外狀況處理](../../../standard/exceptions/index.md) 內建于 .net 中，通常更有效率，而且在處理應用程式中的執行時間錯誤時，建議使用此方式。

 如果沒有錯誤處理或例外狀況處理，任何發生的執行階段錯誤都是嚴重的：顯示錯誤訊息，並停止執行。

> [!NOTE]
> `Error`關鍵字也會用於[錯誤語句](error-statement.md)，以提供回溯相容性支援。

## <a name="syntax"></a>Syntax

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>組件

|詞彙|定義|
|---|---|
|`GoTo`*行*|啟用在必要 *行* 引數中指定的行開始的錯誤處理常式。 *Line*引數是任何行標籤或行號。 如果發生執行階段錯誤，請將分支控制到指定的行，使錯誤處理常式成為使用中狀態。 指定的行必須與語句位於相同的程式中， `On Error` 否則會發生編譯時期錯誤。|
|`GoTo 0`|在目前程式中停用已啟用的錯誤處理常式，並將它重設為 `Nothing` 。|
|`GoTo -1`|在目前的程式中停用已啟用的例外狀況，並將其重設為 `Nothing` 。|
|`Resume Next`|指定當執行階段錯誤發生時，控制權會移至緊接在發生錯誤的語句之後的語句，並從該點繼續執行。 `On Error GoTo`當您存取物件時，請使用此表單而不是。|

## <a name="remarks"></a>備註

> [!NOTE]
> 建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外狀況處理和 `On Error` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。

 「已啟用」錯誤處理常式是由語句開啟的錯誤處理常式 `On Error` 。 「作用中」錯誤處理常式是在處理錯誤的處理常式中啟用的處理常式。

 如果錯誤處理常式在發生錯誤時 (發生錯誤，以及) 發生的 `Resume` 、、 `Exit Sub` `Exit Function` 或 `Exit Property` 語句之間，則目前的程式錯誤處理常式無法處理此錯誤。 控制權會返回呼叫程式。
  
 如果呼叫的程式有已啟用的錯誤處理常式，則會啟用它來處理錯誤。 如果呼叫程式的錯誤處理常式也在使用中，控制權會透過先前的呼叫程式回傳，直到找到已啟用但非使用中的錯誤處理常式為止。 如果找不到這類錯誤處理常式，則錯誤會在實際發生的位置發生嚴重錯誤。
  
 每當錯誤處理常式將控制權傳遞回呼叫程式時，該程式就會變成目前的程式。 一旦任何程式中的錯誤處理常式處理錯誤，就會在語句指定的點，于目前的程式中繼續執行 `Resume` 。
  
> [!NOTE]
> 錯誤處理常式不是程式或程式 `Sub` `Function` 。 它是以行標籤或行號標記的程式碼區段。
  
## <a name="number-property"></a>Number 屬性

 錯誤處理常式依賴 `Number` 物件的屬性值 `Err` 來判斷錯誤的原因。 常式應該先測試或儲存物件中的相關屬性值， `Err` 然後再發生任何其他錯誤，或呼叫可能造成錯誤的程式之前。 物件中的屬性值 `Err` 只會反映最新的錯誤。 與相關聯的錯誤訊息 `Err.Number` 包含在中 `Err.Description` 。  
  
## <a name="throw-statement"></a>Throw 陳述式  

 以方法引發的錯誤，會 `Err.Raise` 將屬性設定 `Exception` 為類別的新建立實例 <xref:System.Exception> 。 為了支援引發衍生例外狀況類型的例外狀況， `Throw` 語言支援語句。 這會採用單一參數，此參數是要擲回的例外狀況實例。 下列範例顯示如何搭配現有的例外狀況處理支援來使用這些功能：

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 請注意， `On Error GoTo` 不論例外狀況類別為何，語句都會捕捉所有錯誤。
  
## <a name="on-error-resume-next"></a>On Error Resume Next

 `On Error Resume Next` 使執行繼續使用緊接在引發執行階段錯誤的語句後面的語句，或使用緊接在包含語句之程式的最新呼叫之後的語句 `On Error Resume Next` 。 這個語句可讓您在執行階段錯誤時繼續執行。 您可以將錯誤處理常式放在發生錯誤的位置，而不是將控制項傳送至程式內的另一個位置。 `On Error Resume Next`當呼叫另一個程式時，語句會變成非使用中狀態，因此， `On Error Resume Next` 如果您想要在該常式內內嵌錯誤處理，請在每個呼叫的常式中執行語句。
  
> [!NOTE]
> 在 `On Error Resume Next` `On Error GoTo` 處理存取其他物件時所產生的錯誤時，最好使用此結構。 `Err`在每次與物件互動之後進行檢查，都不會對程式碼所存取的物件造成混淆。 您可以確定哪個物件放入錯誤碼 `Err.Number` ，以及哪個物件最初產生的錯誤 () 中指定的物件 `Err.Source` 。

## <a name="on-error-goto-0"></a>On Error GoTo 0

 `On Error GoTo 0` 停用目前程式中的錯誤處理。 它不會將第0行指定為錯誤處理常式代碼的開頭，即使套裝程式含編號為0的行。 如果沒有 `On Error GoTo 0` 語句，則會在程式結束時自動停用錯誤處理常式。

## <a name="on-error-goto--1"></a>錯誤 GoTo-1

 `On Error GoTo -1` 停用目前程式中的例外狀況。 它不會指定行1做為錯誤處理常式代碼的開頭，即使套裝程式含編號1的行。 如果沒有 `On Error GoTo -1` 語句，則會在程式結束時自動停用例外狀況。

 若要避免在未發生錯誤時執行錯誤處理常式代碼，請 `Exit Sub` `Exit Function` `Exit Property` 在錯誤處理常式之前放置、或語句，如下列片段所示：

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 在此，錯誤處理常式代碼會遵循 `Exit Sub` 語句，並在 `End Sub` 語句之前，將它與程式流程分開。 您可以將錯誤處理常式代碼放在程式中的任何位置。

## <a name="untrapped-errors"></a>未被截取錯誤

 當物件做為可執行檔執行時，物件中的未被截取錯誤會傳回至控制應用程式。 在開發環境內，只有在設定適當的選項時，才會將未被截取錯誤傳回給控制應用程式。 請參閱您的主應用程式檔，以取得在偵錯工具期間應設定哪些選項、如何設定它們，以及主機是否可以建立類別的說明。

 如果您建立可存取其他物件的物件，您應該嘗試處理傳回的任何未處理錯誤。 如果您無法這樣做，請將錯誤碼對應 `Err.Number` 至您自己的其中一個錯誤，然後將它們傳遞回物件的呼叫端。 您應該將您的錯誤碼新增至常數來指定錯誤 `VbObjectError` 。 例如，如果您的錯誤碼為1052，請將其指派如下：

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> 呼叫 Windows 動態連結程式庫時的系統錯誤 (Dll) 不會引發例外狀況，而且無法在 Visual Basic 錯誤捕捉時加以攔截。 呼叫 DLL 函式時，您應該根據) 的 API 規格來檢查每個成功或失敗 (的傳回值，而在發生失敗的情況下，請檢查 `Err` 物件的 `LastDLLError` 屬性值。

## <a name="example"></a>範例

 此範例會先使用 `On Error GoTo` 語句來指定程式中錯誤處理常式的位置。 在此範例中，零除的嘗試會產生錯誤號碼6。 錯誤會在錯誤處理常式中處理，然後控制權會傳回給造成錯誤的語句。 `On Error GoTo 0`語句會關閉錯誤捕捉。 然後 `On Error Resume Next` 語句會用來延遲錯誤捕捉，讓下一個語句所產生之錯誤的內容可以知道。 請注意，這 `Err.Clear` 是在 `Err` 處理錯誤之後用來清除物件的屬性。

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>規格需求

 **命名空間：** [Microsoft.](../runtime-library-members.md)

 **元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End 陳述式](end-statement.md)
- [Exit 陳述式](exit-statement.md)
- [Resume 陳述式](resume-statement.md)
- [錯誤訊息](../error-messages/index.md)
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
