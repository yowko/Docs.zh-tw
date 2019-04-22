---
title: 屬性 '<propertyname>' 不會在所有程式碼路徑上傳回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a535a6b951dc9872109527f78d7de5f3fcdd3292
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821877"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="e6c62-102">屬性 '\<屬性名稱 >' 並未傳回有關所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="e6c62-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="e6c62-103">屬性 '\<屬性名稱 >' 並未傳回有關所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="e6c62-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="e6c62-104">使用結果時，Null 參考例外狀況可能在執行階段時發生。</span><span class="sxs-lookup"><span data-stu-id="e6c62-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="e6c62-105">屬性`Get`程序中的至少一個通過程式碼不會傳回值的可能的路徑。</span><span class="sxs-lookup"><span data-stu-id="e6c62-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="e6c62-106">您可以從屬性傳回值`Get`程序，在下列任一方式：</span><span class="sxs-lookup"><span data-stu-id="e6c62-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="e6c62-107">將值指派給屬性名稱，然後再執行`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6c62-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="e6c62-108">將值指派給屬性名稱，然後再執行`End Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6c62-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="e6c62-109">包含值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c62-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="e6c62-110">如果控制權傳遞給`Exit Property`或是`End Get`和您不指派任何值給屬性名稱，`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="e6c62-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="e6c62-111">如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c62-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="e6c62-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="e6c62-112">By default, this message is a warning.</span></span> <span data-ttu-id="e6c62-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e6c62-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e6c62-114">**錯誤 ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="e6c62-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e6c62-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e6c62-115">To correct this error</span></span>  
  
-   <span data-ttu-id="e6c62-116">檢查控制項流程邏輯，並確定您指定的值會導致傳回每個陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="e6c62-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="e6c62-117">很容易就能保證每一次從程序傳回將傳回值，如果您總是使用`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6c62-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="e6c62-118">如果您這麼做，最後一個陳述式前面`End Get`應該是`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e6c62-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c62-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c62-119">See also</span></span>

- [<span data-ttu-id="e6c62-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="e6c62-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="e6c62-121">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="e6c62-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e6c62-122">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="e6c62-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
