---
title: 使用使用者篩選的例外處理常式
description: '瞭解如何在 c # 和 Visual Basic 中使用使用者篩選的例外狀況處理常式。'
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512667"
---
# <a name="use-user-filtered-exception-handlers"></a>使用使用者篩選的例外處理常式

使用者篩選例外狀況處理常式會依據您定義的例外狀況需求，攔截和處理例外狀況。 這些處理常式會使用 `catch` 語句搭配 `when` 關鍵字 (`Catch` 和 `When` Visual Basic) 。  
  
 當特定例外狀況物件對應至多個錯誤時，這個技術非常有用。 在此情況下，物件通常會有一個屬性，其中包含與錯誤相關聯的特定錯誤碼。 您可以使用運算式中的錯誤碼屬性，只選取您想要在該子句中處理的特定錯誤 `catch` 。  
  
 下列範例說明 `catch` / `when` 語句。

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 不會以任何方式限制使用者篩選子句的運算式。 如果在使用者篩選運算式執行期間發生例外狀況，會捨棄該例外狀況，且篩選運算式會被視為必須評估為 false。 在此情況下，通用語言執行平台會繼續搜尋目前例外狀況的處理常式。  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a>結合特定的例外狀況和使用者篩選的子句  

 `catch`語句可以同時包含特定的例外狀況和使用者篩選的子句。 執行階段會先測試特定例外狀況。 如果特定例外狀況成功，則執行階段會執行使用者篩選。 一般篩選可以包含類別篩選中所宣告之變數的參考。 請注意，無法反轉兩個篩選子句的順序。  
  
 下列範例顯示 **catch** 語句中的特定例外狀況，以及使用 **when** 關鍵字的使用者篩選子句。  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>請參閱

- [例外狀況](index.md)
