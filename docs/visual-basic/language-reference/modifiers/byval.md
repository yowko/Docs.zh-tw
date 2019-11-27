---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351589"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="608d4-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="608d4-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="608d4-103">指定以傳[值方式](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)傳遞引數，讓被呼叫的程式或屬性無法變更呼叫程式碼中引數基礎的變數值。</span><span class="sxs-lookup"><span data-stu-id="608d4-103">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="608d4-104">如果未指定任何修飾詞，則預設值為 ByVal。</span><span class="sxs-lookup"><span data-stu-id="608d4-104">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="608d4-105">因為它是預設值，所以您不需要在方法簽章中明確指定 `ByVal` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="608d4-105">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="608d4-106">它通常會產生雜訊的程式碼，而且經常會導致非預設的 `ByRef` 關鍵字被忽略。</span><span class="sxs-lookup"><span data-stu-id="608d4-106">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="608d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="608d4-107">Remarks</span></span>
 <span data-ttu-id="608d4-108">`ByVal` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="608d4-108">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="608d4-109">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="608d4-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

 [<span data-ttu-id="608d4-110">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="608d4-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [<span data-ttu-id="608d4-111">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="608d4-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [<span data-ttu-id="608d4-112">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="608d4-112">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [<span data-ttu-id="608d4-113">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="608d4-113">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="608d4-114">範例</span><span class="sxs-lookup"><span data-stu-id="608d4-114">Example</span></span>
 <span data-ttu-id="608d4-115">下列範例示範如何使用 `ByVal` 參數傳遞機制搭配參考型別引數。</span><span class="sxs-lookup"><span data-stu-id="608d4-115">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="608d4-116">在此範例中，引數是 `c1`，類別的實例 `Class1`。</span><span class="sxs-lookup"><span data-stu-id="608d4-116">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="608d4-117">`ByVal` 可防止程式中的程式碼變更參考引數的基礎值，`c1`，但不會保護 `c1`的可存取欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="608d4-117">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="608d4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="608d4-118">See also</span></span>

- [<span data-ttu-id="608d4-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="608d4-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="608d4-120">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="608d4-120">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
