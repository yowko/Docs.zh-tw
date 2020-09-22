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
ms.openlocfilehash: f3f9f5ecb96686fe525e98cf64672d81a3145796
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873278"
---
# <a name="error-statement"></a>Error 陳述式

模擬錯誤的發生。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>組件  

 `errornumber`  
 必要。 可以是任何有效的錯誤號碼。  
  
## <a name="remarks"></a>備註  

 `Error`為了回溯相容性，支援語句。 在新的程式碼中，特別是在建立物件時，請使用 `Err` 物件的 `Raise` 方法來產生執行階段錯誤。  
  
 如果已 `errornumber` 定義， `Error` 語句會在物件的屬性 `Err` 指派下列預設值之後，呼叫錯誤處理常式：  
  
|屬性|值|  
|--------------|-----------|  
|`Number`|將值指定為語句的引數 `Error` 。 可以是任何有效的錯誤號碼。|  
|`Source`|目前 Visual Basic 專案的名稱。|  
|`Description`|字串運算式，對應至指定之函數的傳回值 `Error` `Number` （如果這個字串存在的話）。 如果字串不存在，則會 `Description` 包含長度為零的字串 ( "" ) 。|  
|`HelpFile`|適當的 Visual Basic 說明檔的完整磁片磁碟機、路徑和檔案名。|  
|`HelpContext`|適當的 Visual Basic 說明檔內容識別碼，適用于對應于屬性的錯誤 `Number` 。|  
|`LastDLLError`|零個。|  
  
 如果沒有錯誤處理常式，或未啟用任何錯誤處理常式，則會從物件屬性建立並顯示錯誤訊息 `Err` 。  
  
> [!NOTE]
> 某些 Visual Basic 主機應用程式無法建立物件。 請參閱主機應用程式的檔，以判斷它是否可以建立類別和物件。  
  
## <a name="example"></a>範例  

 這個範例會使用 `Error` 語句來產生錯誤號碼11。  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>規格需求  

 **命名空間：** [Microsoft.](../runtime-library-members.md)  
  
 **元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error 陳述式](on-error-statement.md)
- [Resume 陳述式](resume-statement.md)
- [錯誤訊息](../error-messages/index.md)
