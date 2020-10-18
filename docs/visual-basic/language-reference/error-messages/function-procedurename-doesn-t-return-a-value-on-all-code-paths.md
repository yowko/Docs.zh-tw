---
title: 函式 '<procedurename>' 並未傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 19b305e337767dfb34718aed7b665f142851bd36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163359"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="380b5-102">BC42105：函式 ' \<procedurename> ' 未傳回所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="380b5-102">BC42105: Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="380b5-103">函數 ' \<procedurename> ' 不會傳回所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="380b5-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="380b5-104">您是否遺漏了 ' Return ' 語句？</span><span class="sxs-lookup"><span data-stu-id="380b5-104">Are you missing a 'Return' statement?</span></span>

 <span data-ttu-id="380b5-105">`Function`程式在其程式碼中至少有一個可能的路徑不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="380b5-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="380b5-106">您可以使用下列任何一種方式，從程式傳回值 `Function` ：</span><span class="sxs-lookup"><span data-stu-id="380b5-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>

- <span data-ttu-id="380b5-107">在 [Return 語句](../statements/return-statement.md)中包含值。</span><span class="sxs-lookup"><span data-stu-id="380b5-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

- <span data-ttu-id="380b5-108">將值指派給程式 `Function` 名稱，然後執行 `Exit Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="380b5-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>

- <span data-ttu-id="380b5-109">將值指派給程式 `Function` 名稱，然後執行 `End Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="380b5-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>

 <span data-ttu-id="380b5-110">如果控制權傳遞給 `Exit Function` 或， `End Function` 而且您沒有將任何值指派給程式名稱，則程式會傳回傳回資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="380b5-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="380b5-111">如需詳細資訊，請參閱 [Function 語句](../statements/function-statement.md)中的「行為」。</span><span class="sxs-lookup"><span data-stu-id="380b5-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

 <span data-ttu-id="380b5-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="380b5-112">By default, this message is a warning.</span></span> <span data-ttu-id="380b5-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="380b5-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="380b5-114">**錯誤識別碼：** BC42105</span><span class="sxs-lookup"><span data-stu-id="380b5-114">**Error ID:** BC42105</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="380b5-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="380b5-115">To correct this error</span></span>

- <span data-ttu-id="380b5-116">檢查您的控制流程邏輯，並確定您在每個導致傳回的語句之前指派一個值。</span><span class="sxs-lookup"><span data-stu-id="380b5-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

     <span data-ttu-id="380b5-117">如果您一律使用語句，則可更輕鬆地確保從程式傳回的每個傳回值 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="380b5-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="380b5-118">如果您這樣做，之前的最後一個語句 `End Function` 應該是 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="380b5-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="380b5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="380b5-119">See also</span></span>

- [<span data-ttu-id="380b5-120">Function 程序</span><span class="sxs-lookup"><span data-stu-id="380b5-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="380b5-121">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="380b5-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="380b5-122">專案設計工具、編譯頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="380b5-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
