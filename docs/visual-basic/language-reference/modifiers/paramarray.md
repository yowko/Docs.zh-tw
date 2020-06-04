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
ms.openlocfilehash: e3c24818ea87884a0dd9b42c604e13e16ca6d3d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391816"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="e0274-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0274-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="e0274-103">指定程式參數接受指定之類型的選擇性元素陣列。</span><span class="sxs-lookup"><span data-stu-id="e0274-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="e0274-104">`ParamArray`只能用於參數清單的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="e0274-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0274-105">備註</span><span class="sxs-lookup"><span data-stu-id="e0274-105">Remarks</span></span>  
 <span data-ttu-id="e0274-106">`ParamArray`可讓您將任意數目的引數傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="e0274-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="e0274-107">`ParamArray`參數一律使用[ByVal](byval.md)來宣告。</span><span class="sxs-lookup"><span data-stu-id="e0274-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="e0274-108">您可以提供一或多個引數給 `ParamArray` 參數，方法是傳遞適當資料類型的陣列、以逗號分隔的值清單，或完全沒有任何內容。</span><span class="sxs-lookup"><span data-stu-id="e0274-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="e0274-109">如需詳細資訊，請參閱[參數陣列](../../programming-guide/language-features/procedures/parameter-arrays.md)中的「呼叫 ParamArray」。</span><span class="sxs-lookup"><span data-stu-id="e0274-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0274-110">當您處理可能會無限大的陣列時，會有 overrunning 應用程式的一些內部容量的風險。</span><span class="sxs-lookup"><span data-stu-id="e0274-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="e0274-111">如果您接受來自呼叫程式碼的參數陣列，您應該測試其長度，如果對您的應用程式而言太大，則採取適當的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0274-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="e0274-112">`ParamArray` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="e0274-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e0274-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="e0274-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="e0274-114">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0274-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="e0274-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e0274-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="e0274-116">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e0274-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0274-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0274-117">See also</span></span>

- [<span data-ttu-id="e0274-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e0274-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e0274-119">參數陣列</span><span class="sxs-lookup"><span data-stu-id="e0274-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
