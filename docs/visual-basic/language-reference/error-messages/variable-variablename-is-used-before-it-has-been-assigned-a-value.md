---
title: 變數&#39; &lt;variablename&gt; &#39;已在指派值之前使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: d314f952bd6e11adaac642ba63ed292f48cda805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596915"
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="19398-102">變數&#39; &lt;variablename&gt; &#39;已在指派值之前使用</span><span class="sxs-lookup"><span data-stu-id="19398-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="19398-103">變數 '\<變數名稱 >' 已在指派值之前使用。</span><span class="sxs-lookup"><span data-stu-id="19398-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="19398-104">可能會在執行階段產生 null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="19398-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="19398-105">應用程式已通過程式碼會讀取變數指派任何值之前，至少一個可能的路徑。</span><span class="sxs-lookup"><span data-stu-id="19398-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="19398-106">如果變數從未獲派值，則會持有其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="19398-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="19398-107">參考資料型別，該預設值是[Nothing](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="19398-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="19398-108">在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="19398-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="19398-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="19398-109">By default, this message is a warning.</span></span> <span data-ttu-id="19398-110">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="19398-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="19398-111">**錯誤 ID:** BC42104</span><span class="sxs-lookup"><span data-stu-id="19398-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19398-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="19398-112">To correct this error</span></span>  
  
-   <span data-ttu-id="19398-113">請檢查控制項流程邏輯，並確定變數具有有效的值，控制權會傳遞給讀取它的任何陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="19398-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="19398-114">若要保證變數一律具有有效的值的方法之一是初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="19398-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="19398-115">請參閱中的初始化 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="19398-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19398-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19398-116">See Also</span></span>  
 [<span data-ttu-id="19398-117">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="19398-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="19398-118">變數宣告</span><span class="sxs-lookup"><span data-stu-id="19398-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="19398-119">變數的疑難排解</span><span class="sxs-lookup"><span data-stu-id="19398-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
