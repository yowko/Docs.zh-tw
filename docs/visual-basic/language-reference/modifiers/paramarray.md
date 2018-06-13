---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597356"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="c24ed-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c24ed-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="c24ed-103">指定程序參數可選擇性指定的型別元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="c24ed-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="c24ed-104">`ParamArray` 可以是只用於參數清單的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="c24ed-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c24ed-105">備註</span><span class="sxs-lookup"><span data-stu-id="c24ed-105">Remarks</span></span>  
 <span data-ttu-id="c24ed-106">`ParamArray` 可讓您將任意數目的引數傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="c24ed-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="c24ed-107">A`ParamArray`參數一律宣告使用[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="c24ed-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="c24ed-108">您可以一或多個引數提供給`ParamArray`藉由傳遞適當的資料陣列的參數類型，以逗號分隔清單的值，或不完全。</span><span class="sxs-lookup"><span data-stu-id="c24ed-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="c24ed-109">如需詳細資訊，請參閱 「 呼叫 ParamArray"[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="c24ed-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c24ed-110">只要處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。</span><span class="sxs-lookup"><span data-stu-id="c24ed-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="c24ed-111">如果您接受參數陣列，從呼叫程式碼，您應該測試它的長度，並採取適當步驟，如果您的應用程式而言太大。</span><span class="sxs-lookup"><span data-stu-id="c24ed-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="c24ed-112">`ParamArray` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="c24ed-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c24ed-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="c24ed-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="c24ed-114">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="c24ed-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c24ed-115">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="c24ed-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c24ed-116">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="c24ed-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c24ed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c24ed-117">See Also</span></span>  
 [<span data-ttu-id="c24ed-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c24ed-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="c24ed-119">參數陣列</span><span class="sxs-lookup"><span data-stu-id="c24ed-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
