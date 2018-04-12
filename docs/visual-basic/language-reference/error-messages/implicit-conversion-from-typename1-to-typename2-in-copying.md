---
title: 從隱含轉換 &#39;&lt;typename1&gt;&#39; 加入 &#39;&lt;2>&gt;&#39; 複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 後，對應的引數。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="d72af-102">從隱含轉換 &#39;&lt;typename1&gt;&#39; 加入 &#39;&lt;2>&gt;&#39; 複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 後，對應的引數。</span><span class="sxs-lookup"><span data-stu-id="d72af-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="d72af-103">與呼叫的程序[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)類型不同於其對應參數的引數。</span><span class="sxs-lookup"><span data-stu-id="d72af-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="d72af-104">如果您要傳入的引數`ByRef`，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]有時會將引數值複製至區域變數，而不是傳遞參考程序中。</span><span class="sxs-lookup"><span data-stu-id="d72af-104">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="d72af-105">在這類情況下，此程序傳回時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 接著必須將區域變數值複製回呼叫中程式碼中的引數。</span><span class="sxs-lookup"><span data-stu-id="d72af-105">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="d72af-106">如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。</span><span class="sxs-lookup"><span data-stu-id="d72af-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="d72af-107">但是，如果類型不同，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須進行雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="d72af-107">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="d72af-108">因為您無法使用`CType`或任何其他轉換關鍵字，在上一個程序的引數或參數，這類轉換永遠是隱含。</span><span class="sxs-lookup"><span data-stu-id="d72af-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="d72af-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="d72af-109">By default, this message is a warning.</span></span> <span data-ttu-id="d72af-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d72af-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d72af-111">**錯誤 ID:** BC41999</span><span class="sxs-lookup"><span data-stu-id="d72af-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d72af-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d72af-112">To correct this error</span></span>  
  
-   <span data-ttu-id="d72af-113">如果可能，請使用類型與程序參數相同的呼叫中引數，這樣 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 就不需要執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="d72af-113">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="d72af-114">如果您要呼叫的程序的引數類型的參數類型不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="d72af-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72af-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d72af-115">See Also</span></span>  
 [<span data-ttu-id="d72af-116">程序</span><span class="sxs-lookup"><span data-stu-id="d72af-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="d72af-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="d72af-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d72af-118">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="d72af-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="d72af-119">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="d72af-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
