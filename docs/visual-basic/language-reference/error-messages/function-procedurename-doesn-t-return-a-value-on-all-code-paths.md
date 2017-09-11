---
title: "函式 &quot;&lt;m e&gt;&quot; 並未傳回有關所有程式碼路徑的值 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
dev_langs:
- VB
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cec047644bfbf82c5c3c206b23af6b0fc37f834d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="93dee-102">函式 '&lt;m e&gt;' 並未傳回有關所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="93dee-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="93dee-103">函式 '\<m e >' 並未傳回有關所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="93dee-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="93dee-104">您是否遺漏 'Return' 陳述式？</span><span class="sxs-lookup"><span data-stu-id="93dee-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="93dee-105">A`Function`程序將不會傳回值，其程式碼透過至少一個可能的路徑。</span><span class="sxs-lookup"><span data-stu-id="93dee-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="93dee-106">您可以傳回值，以從`Function`程序中任何以下列方式︰</span><span class="sxs-lookup"><span data-stu-id="93dee-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="93dee-107">包含的值在[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="93dee-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="93dee-108">指派值`Function`程序名稱，然後執行`Exit Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93dee-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="93dee-109">指派值`Function`程序名稱，然後執行`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93dee-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="93dee-110">控制權會傳遞給`Exit Function`或`End Function`您尚未指派任何值的程序名稱、 程序傳回的傳回資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="93dee-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="93dee-111">如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="93dee-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="93dee-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="93dee-112">By default, this message is a warning.</span></span> <span data-ttu-id="93dee-113">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="93dee-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="93dee-114">**錯誤識別碼︰** BC42105</span><span class="sxs-lookup"><span data-stu-id="93dee-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93dee-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="93dee-115">To correct this error</span></span>  
  
-   <span data-ttu-id="93dee-116">檢查控制項流程邏輯，並確定您指定的值，傳回每個陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="93dee-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="93dee-117">很容易就能保證每一次從程序傳回傳回值，如果您總是使用`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93dee-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="93dee-118">如果您這麼做之前, 的最後一個陳述式`End Function`應該`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93dee-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dee-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93dee-119">See Also</span></span>  
 <span data-ttu-id="93dee-120">[Function 程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="93dee-120">[Function Procedures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span></span>  
<span data-ttu-id="93dee-121"> [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="93dee-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="93dee-122"> [專案設計工具、編譯頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="93dee-122"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>
