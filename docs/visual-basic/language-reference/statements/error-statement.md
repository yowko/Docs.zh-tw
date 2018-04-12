---
title: Error 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a>Error 陳述式
模擬的錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>組件  
 `errornumber`  
 必要項。 可以是任何有效的錯誤號碼。  
  
## <a name="remarks"></a>備註  
 `Error`回溯相容性支援陳述式。 在新的程式碼，特別是在建立物件時，使用`Err`物件的`Raise`方法來產生執行階段錯誤。  
  
 如果`errornumber`定義，`Error`陳述式之後的內容會呼叫錯誤處理常式`Err`物件會指定下列的預設值：  
  
|屬性|值|  
|--------------|-----------|  
|`Number`|指定為引數的值`Error`陳述式。 可以是任何有效的錯誤號碼。|  
|`Source`|目前的 Visual Basic 專案的名稱。|  
|`Description`|字串對應至傳回值的運算式`Error`函式指定`Number`，如果這個字串已存在。 如果字串不存在，`Description`包含零長度字串 ("")。|  
|`HelpFile`|完整的磁碟機、 路徑和檔案名稱的適當的 Visual Basic 說明檔案。|  
|`HelpContext`|適當的 Visual Basic 說明檔案內容識別碼對應至錯誤`Number`屬性。|  
|`LastDLLError`|是零。|  
  
 如果錯誤處理常式不存在，或如果沒有啟用，建立並從顯示的錯誤訊息`Err`物件屬性。  
  
> [!NOTE]
>  某些 Visual Basic 主機應用程式無法建立物件。 請參閱主應用程式的文件，以判斷它是否可以建立類別和物件。  
  
## <a name="example"></a>範例  
 這個範例會使用`Error`陳述式產生錯誤代碼 11。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [錯誤訊息](../../../visual-basic/language-reference/error-messages/index.md)
