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
ms.openlocfilehash: 16a69e547d14c619d427aa8860e9bf4002b6db04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703597"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="75a36-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75a36-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="75a36-103">指定程序參數會採用選擇性的項目指定之型別的陣列。</span><span class="sxs-lookup"><span data-stu-id="75a36-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="75a36-104">`ParamArray` 可以用於僅在參數清單的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="75a36-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a36-105">備註</span><span class="sxs-lookup"><span data-stu-id="75a36-105">Remarks</span></span>  
 <span data-ttu-id="75a36-106">`ParamArray` 可讓您將任意數目的引數傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="75a36-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="75a36-107">A`ParamArray`參數一律使用宣告[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="75a36-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="75a36-108">您可以一或多個引數提供給`ParamArray`藉由傳遞適當的資料陣列的參數類型，逗號分隔的清單值，或不完全。</span><span class="sxs-lookup"><span data-stu-id="75a36-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="75a36-109">如需詳細資訊，請參閱 「 呼叫 ParamArray 」 中[參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="75a36-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75a36-110">每當您處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。</span><span class="sxs-lookup"><span data-stu-id="75a36-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="75a36-111">如果您接受呼叫的程式碼的參數陣列時，您應該測試它的長度，並採取適當步驟，如果它是對您的應用程式而言太大。</span><span class="sxs-lookup"><span data-stu-id="75a36-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="75a36-112">`ParamArray` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="75a36-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="75a36-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="75a36-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="75a36-114">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="75a36-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="75a36-115">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="75a36-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="75a36-116">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="75a36-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="75a36-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75a36-117">See also</span></span>
- [<span data-ttu-id="75a36-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="75a36-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="75a36-119">參數陣列</span><span class="sxs-lookup"><span data-stu-id="75a36-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
