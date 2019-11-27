---
title: Error 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351241"
---
# <a name="error-statement"></a>Error 陳述式
模擬發生錯誤的次數。  
  
## <a name="syntax"></a>語法  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>組件  
 `errornumber`  
 必要。 可以是任何有效的錯誤號碼。  
  
## <a name="remarks"></a>備註  
 支援 `Error` 語句以提供回溯相容性。 在新程式碼中，尤其是在建立物件時，請使用 `Err` 物件的 `Raise` 方法來產生執行階段錯誤。  
  
 如果定義了 `errornumber`，`Error` 語句會在將下列預設值指派給 `Err` 物件的屬性之後，呼叫錯誤處理常式：  
  
|屬性|值|  
|--------------|-----------|  
|`Number`|指定為 `Error` 語句之引數的值。 可以是任何有效的錯誤號碼。|  
|`Source`|目前 Visual Basic 專案的名稱。|  
|`Description`|對應至指定 `Number`之 `Error` 函數傳回值的字串運算式（如果這個字串存在）。 如果字串不存在，`Description` 會包含長度為零的字串（""）。|  
|`HelpFile`|適當 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。|  
|`HelpContext`|適當的 Visual Basic 說明 `Number` 屬性對應之錯誤的說明檔內容識別碼。|  
|`LastDLLError`|零.|  
  
 如果沒有錯誤處理常式存在，或未啟用，則會建立錯誤訊息，並顯示在 `Err` 物件屬性中。  
  
> [!NOTE]
> 某些 Visual Basic 主應用程式無法建立物件。 請參閱主機應用程式的檔，以判斷它是否可以建立類別和物件。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Error` 語句來產生錯誤號碼11。  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)
- [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
