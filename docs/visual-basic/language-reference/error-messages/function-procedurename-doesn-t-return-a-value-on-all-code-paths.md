---
title: 函式 '<procedurename>' 並未傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: badcfea4f24ba3858071e02ba47b8f77ab557f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802371"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="05b79-102">函式 '\<程序名稱 >' 並未傳回有關所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="05b79-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="05b79-103">函式 '\<程序名稱 >' 並未傳回有關所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="05b79-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="05b79-104">您是否遺漏了 'Return' 陳述式？</span><span class="sxs-lookup"><span data-stu-id="05b79-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="05b79-105">A`Function`程序中的至少一個通過程式碼不會傳回值的可能的路徑。</span><span class="sxs-lookup"><span data-stu-id="05b79-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="05b79-106">您可以傳回值，以從`Function`程序，在下列任一方式：</span><span class="sxs-lookup"><span data-stu-id="05b79-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="05b79-107">包含值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="05b79-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="05b79-108">將值指派給`Function`程序名稱，然後再執行`Exit Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="05b79-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="05b79-109">將值指派給`Function`程序名稱，然後再執行`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="05b79-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="05b79-110">如果控制權傳遞給`Exit Function`或`End Function`和您不指派任何值給程序名稱、 程序傳回的傳回資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="05b79-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="05b79-111">如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="05b79-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="05b79-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="05b79-112">By default, this message is a warning.</span></span> <span data-ttu-id="05b79-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="05b79-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="05b79-114">**錯誤 ID:** BC42105</span><span class="sxs-lookup"><span data-stu-id="05b79-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05b79-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="05b79-115">To correct this error</span></span>  
  
- <span data-ttu-id="05b79-116">檢查控制項流程邏輯，並確定您指定的值會導致傳回每個陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="05b79-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="05b79-117">很容易就能保證每一次從程序傳回將傳回值，如果您總是使用`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="05b79-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="05b79-118">如果您這麼做，最後一個陳述式前面`End Function`應該是`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="05b79-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b79-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05b79-119">See also</span></span>

- [<span data-ttu-id="05b79-120">函式程序</span><span class="sxs-lookup"><span data-stu-id="05b79-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="05b79-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="05b79-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="05b79-122">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05b79-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
