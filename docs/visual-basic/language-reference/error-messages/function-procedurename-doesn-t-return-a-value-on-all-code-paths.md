---
title: 函式 &#39;&lt;程序名稱&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="51863-102">函式 &#39;&lt;程序名稱&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="51863-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="51863-103">函式 '\<程序名稱 >' 並未傳回有關所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="51863-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="51863-104">您是否遺漏了 'Return' 陳述式？</span><span class="sxs-lookup"><span data-stu-id="51863-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="51863-105">A`Function`程序有至少一個通過程式碼不會傳回值的可能路徑。</span><span class="sxs-lookup"><span data-stu-id="51863-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="51863-106">您可以傳回值，以從`Function`任何下列方式的程序：</span><span class="sxs-lookup"><span data-stu-id="51863-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="51863-107">包含中的值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="51863-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="51863-108">將值指定給`Function`程序名稱，然後執行`Exit Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51863-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="51863-109">將值指定給`Function`程序名稱，然後執行`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51863-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="51863-110">如果控制權傳遞給`Exit Function`或`End Function`和您沒有指派任何值的程序名稱、 程序傳回的傳回資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="51863-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="51863-111">如需詳細資訊，請參閱 「 行為 」 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="51863-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="51863-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="51863-112">By default, this message is a warning.</span></span> <span data-ttu-id="51863-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="51863-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="51863-114">**錯誤 ID:** BC42105</span><span class="sxs-lookup"><span data-stu-id="51863-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51863-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="51863-115">To correct this error</span></span>  
  
-   <span data-ttu-id="51863-116">請檢查控制項流程邏輯，並確定您指派值之前傳回每個陳述式。</span><span class="sxs-lookup"><span data-stu-id="51863-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="51863-117">若要保證每一次從程序傳回將傳回值，如果您總是使用更容易`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51863-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="51863-118">如果您這麼做之前, 的最後一個陳述式`End Function`應該`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="51863-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51863-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51863-119">See Also</span></span>  
 [<span data-ttu-id="51863-120">函式程序</span><span class="sxs-lookup"><span data-stu-id="51863-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="51863-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="51863-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="51863-122">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51863-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
