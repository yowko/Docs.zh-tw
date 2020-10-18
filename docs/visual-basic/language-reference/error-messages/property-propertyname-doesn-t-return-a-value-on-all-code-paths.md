---
title: 屬性 '<propertyname>' 不會在所有程式碼路徑上傳回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 0736e2cbcdea1422d40161c88f898d487f72e3bc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162384"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="e0ffc-102">BC42107：屬性 ' \<propertyname> ' 未傳回所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="e0ffc-102">BC42107: Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="e0ffc-103">屬性 ' \<propertyname> ' 在所有程式碼路徑上都不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="e0ffc-104">使用結果時，Null 參考例外狀況可能在執行階段時發生。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-104">A null reference exception could occur at run time when the result is used.</span></span>

<span data-ttu-id="e0ffc-105">屬性 `Get` 程式在其程式碼中至少有一個可能的路徑不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="e0ffc-106">您可以使用下列任何一種方式，從屬性程式傳回值 `Get` ：</span><span class="sxs-lookup"><span data-stu-id="e0ffc-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>

- <span data-ttu-id="e0ffc-107">將值指派給屬性名稱，然後執行 `Exit Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>

- <span data-ttu-id="e0ffc-108">將值指派給屬性名稱，然後執行 `End Get` 語句。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>

- <span data-ttu-id="e0ffc-109">在 [Return 語句](../statements/return-statement.md)中包含值。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

<span data-ttu-id="e0ffc-110">如果控制權傳遞給 `Exit Property` 或， `End Get` 而且您尚未指派任何值給屬性名稱，則程式會傳回 `Get` 屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="e0ffc-111">如需詳細資訊，請參閱 [Function 語句](../statements/function-statement.md)中的「行為」。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

<span data-ttu-id="e0ffc-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-112">By default, this message is a warning.</span></span> <span data-ttu-id="e0ffc-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="e0ffc-114">**錯誤識別碼：** BC42107</span><span class="sxs-lookup"><span data-stu-id="e0ffc-114">**Error ID:** BC42107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e0ffc-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e0ffc-115">To correct this error</span></span>

- <span data-ttu-id="e0ffc-116">檢查您的控制流程邏輯，並確定您在每個導致傳回的語句之前指派一個值。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

  <span data-ttu-id="e0ffc-117">如果您一律使用語句，則可更輕鬆地確保從程式傳回的每個傳回值 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-117">It's easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="e0ffc-118">如果您這樣做，之前的最後一個語句 `End Get` 應該是 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="e0ffc-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0ffc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ffc-119">See also</span></span>

- [<span data-ttu-id="e0ffc-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="e0ffc-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="e0ffc-121">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e0ffc-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="e0ffc-122">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0ffc-122">Get Statement</span></span>](../statements/get-statement.md)
