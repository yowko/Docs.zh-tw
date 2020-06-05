---
title: 變數 '<variablename>' 已在指派值之前使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406530"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="5d87e-102">變數 '\<variablename>' 已在指派值之前使用</span><span class="sxs-lookup"><span data-stu-id="5d87e-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="5d87e-103">在 \<variablename> 指派值之前，會使用變數 ' '。</span><span class="sxs-lookup"><span data-stu-id="5d87e-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="5d87e-104">可能會在執行階段產生 null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5d87e-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="5d87e-105">應用程式在指派任何值給它之前，至少有一個可能的路徑，它會先讀取變數。</span><span class="sxs-lookup"><span data-stu-id="5d87e-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="5d87e-106">如果變數從未獲派值，則會持有其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="5d87e-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="5d87e-107">若是參考資料類型，該預設值為 [Nothing](../nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="5d87e-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="5d87e-108">在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="5d87e-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="5d87e-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="5d87e-109">By default, this message is a warning.</span></span> <span data-ttu-id="5d87e-110">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="5d87e-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5d87e-111">**錯誤識別碼：** BC42104</span><span class="sxs-lookup"><span data-stu-id="5d87e-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d87e-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5d87e-112">To correct this error</span></span>  
  
- <span data-ttu-id="5d87e-113">檢查您的控制流程邏輯，並確定變數具有有效的值，再將控制權傳遞給任何讀取它的語句。</span><span class="sxs-lookup"><span data-stu-id="5d87e-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
- <span data-ttu-id="5d87e-114">保證變數一律具有有效值的其中一個方法，就是將它初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="5d87e-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="5d87e-115">請參閱[Dim 語句](../statements/dim-statement.md)中的「初始化」。</span><span class="sxs-lookup"><span data-stu-id="5d87e-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d87e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d87e-116">See also</span></span>

- [<span data-ttu-id="5d87e-117">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d87e-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="5d87e-118">變數宣告</span><span class="sxs-lookup"><span data-stu-id="5d87e-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="5d87e-119">變數的疑難排解</span><span class="sxs-lookup"><span data-stu-id="5d87e-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
