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
ms.openlocfilehash: d1e771a95542153dfad0981d3198e6b4c31cdeb9
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264255"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="99678-102">使用使用者篩選的例外狀況處理常式</span><span class="sxs-lookup"><span data-stu-id="99678-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="99678-103">目前，Visual Basic 支援使用者篩選的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99678-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="99678-104">使用者篩選例外狀況處理常式會依據您定義的例外狀況需求，攔截和處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99678-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="99678-105">這些處理常式會使用 **Catch** 陳述式搭配 **When** 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="99678-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="99678-106">當特定例外狀況物件對應至多個錯誤時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="99678-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="99678-107">在此情況下，物件通常會有一個屬性，其中包含與錯誤相關聯的特定錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="99678-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="99678-108">您可以在運算式中使用錯誤碼屬性，只選取您想要在該 **Catch**子句中處理的特定錯誤。</span><span class="sxs-lookup"><span data-stu-id="99678-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="99678-109">下列 Visual Basic 範例示範 **Catch/When**陳述式。</span><span class="sxs-lookup"><span data-stu-id="99678-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="99678-110">不會以任何方式限制使用者篩選子句的運算式。</span><span class="sxs-lookup"><span data-stu-id="99678-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="99678-111">如果在使用者篩選運算式執行期間發生例外狀況，會捨棄該例外狀況，且篩選運算式會被視為必須評估為 false。</span><span class="sxs-lookup"><span data-stu-id="99678-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="99678-112">在此情況下，通用語言執行平台會繼續搜尋目前例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="99678-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="99678-113">結合特定例外狀況和使用者篩選的子句</span><span class="sxs-lookup"><span data-stu-id="99678-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="99678-114">Catch 陳述式可以包含特定例外狀況和使用者篩選的子句。</span><span class="sxs-lookup"><span data-stu-id="99678-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="99678-115">執行階段會先測試特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99678-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="99678-116">如果特定例外狀況成功，則執行階段會執行使用者篩選。</span><span class="sxs-lookup"><span data-stu-id="99678-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="99678-117">一般篩選可以包含類別篩選中所宣告之變數的參考。</span><span class="sxs-lookup"><span data-stu-id="99678-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="99678-118">請注意，無法反轉兩個篩選子句的順序。</span><span class="sxs-lookup"><span data-stu-id="99678-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="99678-119">下列 Visual Basic 範例會顯示 **Catch** 陳述式中的特定例外狀況 `ClassLoadException`，以及使用 **When** 關鍵字的使用者篩選子句。</span><span class="sxs-lookup"><span data-stu-id="99678-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="99678-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99678-120">See also</span></span>

- [<span data-ttu-id="99678-121">例外狀況</span><span class="sxs-lookup"><span data-stu-id="99678-121">Exceptions</span></span>](index.md)
