---
title: 屬性 &#39;&lt;propertyname&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="1c239-102">屬性 &#39;&lt;propertyname&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值</span><span class="sxs-lookup"><span data-stu-id="1c239-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="1c239-103">屬性 '\<屬性名稱 >' 並未傳回有關所有程式碼路徑的值。</span><span class="sxs-lookup"><span data-stu-id="1c239-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1c239-104">使用結果時，Null 參考例外狀況可能在執行階段時發生。</span><span class="sxs-lookup"><span data-stu-id="1c239-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="1c239-105">屬性`Get`程序有至少一個通過程式碼不會傳回值的可能路徑。</span><span class="sxs-lookup"><span data-stu-id="1c239-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="1c239-106">您可以從屬性傳回值`Get`任何下列方式的程序：</span><span class="sxs-lookup"><span data-stu-id="1c239-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="1c239-107">將值指派給屬性名稱，然後執行`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c239-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="1c239-108">將值指派給屬性名稱，然後執行`End Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c239-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="1c239-109">包含中的值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1c239-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="1c239-110">如果控制權傳遞給`Exit Property`或`End Get`和您不指派任何值給屬性名稱，`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="1c239-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="1c239-111">如需詳細資訊，請參閱 「 行為 」 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1c239-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1c239-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="1c239-112">By default, this message is a warning.</span></span> <span data-ttu-id="1c239-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1c239-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1c239-114">**錯誤 ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="1c239-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c239-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1c239-115">To correct this error</span></span>  
  
-   <span data-ttu-id="1c239-116">請檢查控制項流程邏輯，並確定您指派值之前傳回每個陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c239-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="1c239-117">若要保證每一次從程序傳回將傳回值，如果您總是使用更容易`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c239-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1c239-118">如果您這麼做之前, 的最後一個陳述式`End Get`應該`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c239-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c239-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c239-119">See Also</span></span>  
 [<span data-ttu-id="1c239-120">屬性程序</span><span class="sxs-lookup"><span data-stu-id="1c239-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="1c239-121">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="1c239-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="1c239-122">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="1c239-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
