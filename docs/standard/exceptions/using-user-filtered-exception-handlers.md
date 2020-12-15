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
# <a name="use-user-filtered-exception-handlers"></a><span data-ttu-id="338ca-103">使用使用者篩選的例外處理常式</span><span class="sxs-lookup"><span data-stu-id="338ca-103">Use user-filtered exception handlers</span></span>

<span data-ttu-id="338ca-104">使用者篩選例外狀況處理常式會依據您定義的例外狀況需求，攔截和處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="338ca-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="338ca-105">這些處理常式會使用 `catch` 語句搭配 `when` 關鍵字 (`Catch` 和 `When` Visual Basic) 。</span><span class="sxs-lookup"><span data-stu-id="338ca-105">These handlers use the `catch` statement with the `when` keyword (`Catch` and `When` in Visual Basic).</span></span>  
  
 <span data-ttu-id="338ca-106">當特定例外狀況物件對應至多個錯誤時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="338ca-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="338ca-107">在此情況下，物件通常會有一個屬性，其中包含與錯誤相關聯的特定錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="338ca-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="338ca-108">您可以使用運算式中的錯誤碼屬性，只選取您想要在該子句中處理的特定錯誤 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="338ca-108">You can use the error code property in the expression to select only the particular error you want to handle in that `catch` clause.</span></span>  
  
 <span data-ttu-id="338ca-109">下列範例說明 `catch` / `when` 語句。</span><span class="sxs-lookup"><span data-stu-id="338ca-109">The following example illustrates the `catch`/`when` statement.</span></span>

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
  
 <span data-ttu-id="338ca-110">不會以任何方式限制使用者篩選子句的運算式。</span><span class="sxs-lookup"><span data-stu-id="338ca-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="338ca-111">如果在使用者篩選運算式執行期間發生例外狀況，會捨棄該例外狀況，且篩選運算式會被視為必須評估為 false。</span><span class="sxs-lookup"><span data-stu-id="338ca-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="338ca-112">在此情況下，通用語言執行平台會繼續搜尋目前例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="338ca-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="338ca-113">結合特定的例外狀況和使用者篩選的子句</span><span class="sxs-lookup"><span data-stu-id="338ca-113">Combine the specific exception and the user-filtered clauses</span></span>  

 <span data-ttu-id="338ca-114">`catch`語句可以同時包含特定的例外狀況和使用者篩選的子句。</span><span class="sxs-lookup"><span data-stu-id="338ca-114">A `catch` statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="338ca-115">執行階段會先測試特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="338ca-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="338ca-116">如果特定例外狀況成功，則執行階段會執行使用者篩選。</span><span class="sxs-lookup"><span data-stu-id="338ca-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="338ca-117">一般篩選可以包含類別篩選中所宣告之變數的參考。</span><span class="sxs-lookup"><span data-stu-id="338ca-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="338ca-118">請注意，無法反轉兩個篩選子句的順序。</span><span class="sxs-lookup"><span data-stu-id="338ca-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="338ca-119">下列範例顯示 **catch** 語句中的特定例外狀況，以及使用 **when** 關鍵字的使用者篩選子句。</span><span class="sxs-lookup"><span data-stu-id="338ca-119">The following example shows a specific exception in the **catch** statement as well as the user-filtered clause using the **when** keyword.</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="338ca-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="338ca-120">See also</span></span>

- [<span data-ttu-id="338ca-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="338ca-121">Exceptions</span></span>](index.md)
