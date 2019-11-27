---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: fbc87bffebc265e6062512e96fc29a64334b3c65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351365"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="c602e-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c602e-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="c602e-103">指定程式參數接受指定之類型的選擇性元素陣列。</span><span class="sxs-lookup"><span data-stu-id="c602e-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="c602e-104">`ParamArray` 只能用在參數清單的最後一個參數上。</span><span class="sxs-lookup"><span data-stu-id="c602e-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c602e-105">備註</span><span class="sxs-lookup"><span data-stu-id="c602e-105">Remarks</span></span>  
 <span data-ttu-id="c602e-106">`ParamArray` 可讓您將任意數目的引數傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="c602e-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="c602e-107">`ParamArray` 參數一律使用[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)來宣告。</span><span class="sxs-lookup"><span data-stu-id="c602e-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="c602e-108">您可以藉由傳遞適當資料類型的陣列、以逗號分隔的值清單，或完全沒有任何內容，將一個或多個引數提供給 `ParamArray` 參數。</span><span class="sxs-lookup"><span data-stu-id="c602e-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="c602e-109">如需詳細資訊，請參閱[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)中的「呼叫 ParamArray」。</span><span class="sxs-lookup"><span data-stu-id="c602e-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c602e-110">當您處理可能會無限大的陣列時，會有 overrunning 應用程式的一些內部容量的風險。</span><span class="sxs-lookup"><span data-stu-id="c602e-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="c602e-111">如果您接受來自呼叫程式碼的參數陣列，您應該測試其長度，如果對您的應用程式而言太大，則採取適當的步驟。</span><span class="sxs-lookup"><span data-stu-id="c602e-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="c602e-112">`ParamArray` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="c602e-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c602e-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="c602e-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="c602e-114">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="c602e-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c602e-115">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="c602e-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c602e-116">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="c602e-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c602e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c602e-117">See also</span></span>

- [<span data-ttu-id="c602e-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c602e-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="c602e-119">參數陣列</span><span class="sxs-lookup"><span data-stu-id="c602e-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
