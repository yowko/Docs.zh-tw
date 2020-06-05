---
title: 屬性 '<propertyname>' 不會在所有程式碼路徑上傳回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400418"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="1b413-102">屬性 '\<propertyname>' 不會在所有程式碼路徑上傳回值</span><span class="sxs-lookup"><span data-stu-id="1b413-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="1b413-103">屬性 ' \<propertyname> ' 不會傳回所有程式碼路徑上的值。</span><span class="sxs-lookup"><span data-stu-id="1b413-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1b413-104">使用結果時，Null 參考例外狀況可能在執行階段時發生。</span><span class="sxs-lookup"><span data-stu-id="1b413-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="1b413-105">屬性 `Get` 程式具有至少一個可能的路徑，而其程式碼不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="1b413-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="1b413-106">您可以 `Get` 使用下列任何一種方式，從屬性程式傳回值：</span><span class="sxs-lookup"><span data-stu-id="1b413-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="1b413-107">將值指派給屬性名稱，然後執行 `Exit Property` 語句。</span><span class="sxs-lookup"><span data-stu-id="1b413-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="1b413-108">將值指派給屬性名稱，然後執行 `End Get` 語句。</span><span class="sxs-lookup"><span data-stu-id="1b413-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="1b413-109">在[Return 語句](../statements/return-statement.md)中包含值。</span><span class="sxs-lookup"><span data-stu-id="1b413-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="1b413-110">如果控制項傳遞至 `Exit Property` 或 `End Get` ，而且您尚未將任何值指派給屬性名稱，則程式會傳回 `Get` 屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="1b413-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="1b413-111">如需詳細資訊，請參閱[Function 語句](../statements/function-statement.md)中的「行為」。</span><span class="sxs-lookup"><span data-stu-id="1b413-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1b413-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="1b413-112">By default, this message is a warning.</span></span> <span data-ttu-id="1b413-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1b413-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1b413-114">**錯誤識別碼：** BC42107</span><span class="sxs-lookup"><span data-stu-id="1b413-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b413-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1b413-115">To correct this error</span></span>  
  
- <span data-ttu-id="1b413-116">檢查您的控制流程邏輯，並務必在導致傳回的每個語句之前指派一個值。</span><span class="sxs-lookup"><span data-stu-id="1b413-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="1b413-117">如果您一律使用語句，則保證每次從程式傳回的傳回值會比較容易 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="1b413-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1b413-118">如果您這樣做，前面的最後一個語句 `End Get` 應該是 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="1b413-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b413-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b413-119">See also</span></span>

- [<span data-ttu-id="1b413-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="1b413-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="1b413-121">Property Statement</span><span class="sxs-lookup"><span data-stu-id="1b413-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="1b413-122">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="1b413-122">Get Statement</span></span>](../statements/get-statement.md)
