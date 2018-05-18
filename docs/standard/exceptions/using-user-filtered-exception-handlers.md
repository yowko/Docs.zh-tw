---
title: 使用使用者篩選的例外狀況處理常式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e72f87bd4a33491df46576629971c60af4630ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-user-filtered-exception-handlers"></a>使用使用者篩選的例外狀況處理常式
目前，Visual Basic 支援使用者篩選的例外狀況。 使用者篩選例外狀況處理常式會依據您定義的例外狀況需求，攔截和處理例外狀況。 這些處理常式會使用 **Catch** 陳述式搭配 **When** 關鍵字。  
  
 當特定例外狀況物件對應至多個錯誤時，這個技術非常有用。 在此情況下，物件通常會有一個屬性，其中包含與錯誤相關聯的特定錯誤碼。 您可以在運算式中使用錯誤碼屬性，只選取您想要在該 **Catch**子句中處理的特定錯誤。  
  
 下列 Visual Basic 範例示範 **Catch/When**陳述式。  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 不會以任何方式限制使用者篩選子句的運算式。 如果在使用者篩選運算式執行期間發生例外狀況，會捨棄該例外狀況，且篩選運算式會被視為必須評估為 false。 在此情況下，通用語言執行平台會繼續搜尋目前例外狀況的處理常式。  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>結合特定例外狀況和使用者篩選的子句  
 Catch 陳述式可以包含特定例外狀況和使用者篩選的子句。 執行階段會先測試特定例外狀況。 如果特定例外狀況成功，則執行階段會執行使用者篩選。 一般篩選可以包含類別篩選中所宣告之變數的參考。 請注意，無法反轉兩個篩選子句的順序。  
  
 下列 Visual Basic 範例會顯示 **Catch** 陳述式中的特定例外狀況 `ClassLoadException`，以及使用 **When** 關鍵字的使用者篩選子句。  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>請參閱
[例外狀況](index.md)
