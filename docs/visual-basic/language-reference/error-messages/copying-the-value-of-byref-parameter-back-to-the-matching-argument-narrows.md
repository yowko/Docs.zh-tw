---
title: "複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 從類型 &#39; 比對的引數以縮小回到&lt;typename1&gt;&#39; 輸入 &#39;&lt;2>&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="32df5-102">複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 從類型 &#39; 比對的引數以縮小回到&lt;typename1&gt;&#39; 輸入 &#39;&lt;2>&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="32df5-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="32df5-103">可擴展為對應的參數類型的引數呼叫的程序，會縮小轉換從參數的引數。</span><span class="sxs-lookup"><span data-stu-id="32df5-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="32df5-104">當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。</span><span class="sxs-lookup"><span data-stu-id="32df5-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="32df5-105">您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。</span><span class="sxs-lookup"><span data-stu-id="32df5-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="32df5-106">當您在程序呼叫中使用類別或結構類型時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 可以使用這些轉換運算子將引數的類型轉換成其對應參數的類型。</span><span class="sxs-lookup"><span data-stu-id="32df5-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="32df5-107">如果您要傳入的引數[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]有時會將引數值複製至區域變數，而不是傳遞參考程序中。</span><span class="sxs-lookup"><span data-stu-id="32df5-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="32df5-108">在這類情況下，此程序傳回時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 接著必須將區域變數值複製回呼叫中程式碼中的引數。</span><span class="sxs-lookup"><span data-stu-id="32df5-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="32df5-109">如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。</span><span class="sxs-lookup"><span data-stu-id="32df5-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="32df5-110">但是，如果類型不同，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須進行雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="32df5-110">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="32df5-111">如果其中一種類型是類別或結構類型，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須將它轉換成其他類型，以及從其他類型轉換它。</span><span class="sxs-lookup"><span data-stu-id="32df5-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="32df5-112">如果其中一個這些轉換會擴展，就可能會縮小反向轉換。</span><span class="sxs-lookup"><span data-stu-id="32df5-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="32df5-113">**錯誤 ID:** BC32053</span><span class="sxs-lookup"><span data-stu-id="32df5-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32df5-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="32df5-114">To correct this error</span></span>  
  
-   <span data-ttu-id="32df5-115">如果可能，請使用類型與程序參數相同的呼叫中引數，這樣 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 就不需要執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="32df5-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="32df5-116">如果您要呼叫的程序的引數類型的參數類型不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。</span><span class="sxs-lookup"><span data-stu-id="32df5-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="32df5-117">如果您要將值傳回呼叫的引數，請定義反向轉換運算子，作為[Widening](../../../visual-basic/language-reference/modifiers/widening.md)如果可能。</span><span class="sxs-lookup"><span data-stu-id="32df5-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32df5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32df5-118">See Also</span></span>  
 [<span data-ttu-id="32df5-119">程序</span><span class="sxs-lookup"><span data-stu-id="32df5-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="32df5-120">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="32df5-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="32df5-121">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="32df5-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="32df5-122">運算子程序</span><span class="sxs-lookup"><span data-stu-id="32df5-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="32df5-123">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="32df5-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="32df5-124">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="32df5-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="32df5-125">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="32df5-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="32df5-126">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="32df5-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="32df5-127">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="32df5-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
