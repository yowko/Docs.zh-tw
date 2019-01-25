---
title: 複製的值&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回相符引數會從型別&#39; &lt;typename1&gt; &#39; &#39; &lt;2&gt&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: ec733ecd605d0a9db840ea3f0c3e0e3b5b698054
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506264"
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="c98b4-102">複製的值&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回相符引數會從型別&#39; &lt;typename1&gt; &#39; &#39; &lt;2&gt&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="c98b4-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="c98b4-103">可擴展為對應參數類型的引數呼叫的程序，並將參數轉換成引數會縮小。</span><span class="sxs-lookup"><span data-stu-id="c98b4-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="c98b4-104">當您定義類別或結構時，可以定義一個或多個轉換運算子，以將該類別或結構類型轉換成其他類型。</span><span class="sxs-lookup"><span data-stu-id="c98b4-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="c98b4-105">您也可以定義反向轉換運算子，以這些其他類型轉換回您的類別或結構類型。</span><span class="sxs-lookup"><span data-stu-id="c98b4-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="c98b4-106">當您使用類別或結構類型中的程序呼叫時，Visual Basic 就可以使用這些轉換運算子，來將引數的類型轉換成其對應參數的型別。</span><span class="sxs-lookup"><span data-stu-id="c98b4-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="c98b4-107">如果您傳遞的引數[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，Visual Basic 有時會將引數值複製至區域變數，而不是傳遞參考程序中。</span><span class="sxs-lookup"><span data-stu-id="c98b4-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="c98b4-108">在此情況下，此程序傳回時，Visual Basic 必須接著將本機變數的值複製回呼叫端程式碼中的引數。</span><span class="sxs-lookup"><span data-stu-id="c98b4-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="c98b4-109">如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。</span><span class="sxs-lookup"><span data-stu-id="c98b4-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="c98b4-110">但如果類型不同，Visual Basic 必須雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="c98b4-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="c98b4-111">如果其中一個型別是類別或結構類型時，Visual Basic 必須將它與另一個型別。</span><span class="sxs-lookup"><span data-stu-id="c98b4-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="c98b4-112">如果其中一個這些轉換擴展轉換，則可能會縮小反向轉換。</span><span class="sxs-lookup"><span data-stu-id="c98b4-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="c98b4-113">**錯誤 ID:** BC32053</span><span class="sxs-lookup"><span data-stu-id="c98b4-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c98b4-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c98b4-114">To correct this error</span></span>  
  
-   <span data-ttu-id="c98b4-115">可能的話，因此不需要執行任何轉換 Visual Basic，請做為程序參數，使用相同類型的呼叫中引數。</span><span class="sxs-lookup"><span data-stu-id="c98b4-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="c98b4-116">如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ，而非 `ByRef`。</span><span class="sxs-lookup"><span data-stu-id="c98b4-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="c98b4-117">如果您需要將值傳回呼叫的引數，定義反向轉換運算子，作為[Widening](../../../visual-basic/language-reference/modifiers/widening.md)、 的話。</span><span class="sxs-lookup"><span data-stu-id="c98b4-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98b4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c98b4-118">See also</span></span>
- [<span data-ttu-id="c98b4-119">程序</span><span class="sxs-lookup"><span data-stu-id="c98b4-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c98b4-120">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="c98b4-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c98b4-121">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="c98b4-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c98b4-122">運算子程序</span><span class="sxs-lookup"><span data-stu-id="c98b4-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="c98b4-123">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="c98b4-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c98b4-124">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="c98b4-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c98b4-125">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="c98b4-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="c98b4-126">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="c98b4-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c98b4-127">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="c98b4-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
