---
title: "Error Statement | Microsoft Docs"
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
  - "vb.error"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Error statement, syntax"
  - "Error statement"
  - "Error keyword"
  - "run-time errors, codes"
  - "errors [Visual Basic], simulating"
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

模擬錯誤的發生。  
  
## 語法  
  
```  
Error errornumber  
```  
  
## 組件  
 `errornumber`  
 必要項。  可以是任何有效的錯誤代碼。  
  
## 備註  
 回溯相容性 \(Backward Compatibility\) 支援 `Error` 陳述式。  在新的程式碼中，尤其在建立物件時，請使用 `Err` 物件的 `Raise` 方法產生執行階段錯誤。  
  
 如果定義 `errornumber`，則在將下列預設值指派給 `Err` 物件的屬性之後，`Error` 陳述式會呼叫錯誤處理常式：  
  
|屬性|值|  
|--------|-------|  
|`Number`|指定給 `Error` 陳述式做為引數的值。  可以是任何有效的錯誤代碼。|  
|`Source`|目前 Visual Basic 專案的名稱。|  
|`Description`|針對指定的 `Number`，對應到 `Error` 函式傳回值的字串運算式 \(如果這個字串存在的話\)。  如果字串不存在，`Description` 會是長度為零的字串 \(""\)。|  
|`HelpFile`|適當的 Visual Basic 說明檔完整的磁碟、路徑及檔名。|  
|`HelpContext`|對應到 `Number` 屬性之錯誤的適當 Visual Basic 說明檔主題代碼。|  
|`LastDLLError`|零|  
  
 如果錯誤處理常式不存在或沒有啟用，則會在 `Err` 物件屬性中建立並顯示錯誤訊息。  
  
> [!NOTE]
>  某些 Visual Basic 主應用程式 \(Host Application\) 無法建立物件。  請參閱您的主應用程式文件，以便判定它是否可以建立類別及物件。  
  
## 範例  
 這個範例使用 `Error` 陳述式產生錯誤代碼 11。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## 需求  
 **命名空間**：[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件**：Visual Basic 執行階段程式庫 \(在 Microsoft.VisualBasic.dll 中\)  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>   
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/reference/command-line-compiler/index.md)