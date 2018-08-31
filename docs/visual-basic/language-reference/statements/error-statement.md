---
title: Error 陳述式 (Visual Basic)
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
ms.openlocfilehash: 84fce92183228cbfa5554a3ba45770a86e83bff5
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253512"
---
# <a name="error-statement"></a>Error 陳述式
模擬錯誤的相符項目。  
  
## <a name="syntax"></a>語法  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>組件  
 `errornumber`  
 必要。 可以是任何有效的錯誤號碼。  
  
## <a name="remarks"></a>備註  
 `Error`回溯相容性支援陳述式。 在新的程式碼，尤其是在建立物件時，使用`Err`物件的`Raise`方法來產生執行階段錯誤。  
  
 如果`errornumber`定義，則`Error`陳述式會呼叫錯誤處理常式的屬性之後`Err`物件會指派預設值如下：  
  
|屬性|值|  
|--------------|-----------|  
|`Number`|指定為引數的值`Error`陳述式。 可以是任何有效的錯誤號碼。|  
|`Source`|目前的 Visual Basic 專案的名稱。|  
|`Description`|字串對應至的傳回值的運算式`Error`函式指定`Number`，如果這個字串已存在。 如果字串不存在，`Description`包含零長度字串 ("")。|  
|`HelpFile`|完整格式的磁碟機、 路徑和適當的 Visual Basic 說明檔的檔案名稱。|  
|`HelpContext`|適當的 Visual Basic 說明檔內容識別碼對應至錯誤`Number`屬性。|  
|`LastDLLError`|為零。|  
  
 如果沒有錯誤處理常式存在，或如果沒有任何已啟用，建立並從顯示的錯誤訊息`Err`物件屬性。  
  
> [!NOTE]
>  某些 Visual Basic 主應用程式無法建立物件。 請參閱主應用程式的文件，以判斷它是否可以建立類別和物件。  
  
## <a name="example"></a>範例  
 這個範例會使用`Error`陳述式產生錯誤代碼 11。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件：** Visual Basic 執行階段程式庫 （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
