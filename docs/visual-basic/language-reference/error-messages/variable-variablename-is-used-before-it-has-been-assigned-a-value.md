---
title: "變數 &quot;&lt;variablename&gt;&quot; 已在指派值之前使用 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: dfc924ebbebb8b20654156b8871684dcfad6848a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="2778c-102">變數 '&lt;variablename&gt;' 已在指派值之前使用</span><span class="sxs-lookup"><span data-stu-id="2778c-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="2778c-103">變數 '\<variablename >' 已在指派值之前使用。</span><span class="sxs-lookup"><span data-stu-id="2778c-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="2778c-104">可能會在執行階段產生 null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2778c-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="2778c-105">必須至少一個可能的路徑，在讀取變數之前的任何值指派給它的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2778c-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="2778c-106">如果變數從未獲派值，則會持有其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="2778c-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="2778c-107">參考資料型別，該預設值是[Nothing](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="2778c-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="2778c-108">讀取的值為參考變數`Nothing`可能會導致<xref:System.NullReferenceException>在某些情況下。</xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="2778c-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="2778c-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="2778c-109">By default, this message is a warning.</span></span> <span data-ttu-id="2778c-110">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="2778c-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2778c-111">**錯誤識別碼︰** BC42104</span><span class="sxs-lookup"><span data-stu-id="2778c-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2778c-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2778c-112">To correct this error</span></span>  
  
-   <span data-ttu-id="2778c-113">檢查控制項流程邏輯，並確定變數具有有效的值，再將控制項傳遞至讀取它的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="2778c-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="2778c-114">若要保證變數的有效值方法之一是初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="2778c-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="2778c-115">請參閱中的 「 初始化 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="2778c-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2778c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2778c-116">See Also</span></span>  
 <span data-ttu-id="2778c-117">[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2778c-117">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="2778c-118"> [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="2778c-118"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="2778c-119"> [變數的疑難排解](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span><span class="sxs-lookup"><span data-stu-id="2778c-119"> [Troubleshooting Variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span></span>
