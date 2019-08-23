---
title: Error 語句 (Visual Basic)
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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944449"
---
# <a name="error-statement"></a>Error 陳述式
模擬發生錯誤的次數。  
  
## <a name="syntax"></a>語法  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>組件  
 `errornumber`  
 必要項。 可以是任何有效的錯誤號碼。  
  
## <a name="remarks"></a>備註  
 `Error`語句支援回溯相容性。 在新程式碼中, 尤其是在建立物件`Err`時, `Raise`請使用物件的方法來產生執行階段錯誤。  
  
 如果`errornumber`已定義, 則`Error`語句會在`Err`物件的屬性被指派下列預設值之後, 呼叫錯誤處理常式:  
  
|屬性|值|  
|--------------|-----------|  
|`Number`|指定為`Error`語句之引數的值。 可以是任何有效的錯誤號碼。|  
|`Source`|目前 Visual Basic 專案的名稱。|  
|`Description`|對應至指定`Error` `Number`之函式傳回值的字串運算式 (如果這個字串存在)。 如果字串不存在, `Description`則包含長度為零的字串 ("")。|  
|`HelpFile`|適當 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。|  
|`HelpContext`|適當的 Visual Basic 說明檔內容識別碼, 用於對應于`Number`屬性的錯誤。|  
|`LastDLLError`|零.|  
  
 如果沒有錯誤處理常式存在, 或未啟用, 則會建立錯誤訊息, 並從`Err`物件屬性顯示。  
  
> [!NOTE]
> 某些 Visual Basic 主應用程式無法建立物件。 請參閱主機應用程式的檔, 以判斷它是否可以建立類別和物件。  
  
## <a name="example"></a>範例  
 這個範例會使用`Error`語句來產生錯誤號碼11。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)
- [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
