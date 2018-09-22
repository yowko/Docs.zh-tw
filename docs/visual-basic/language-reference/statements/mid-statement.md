---
title: Mid 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: a653e63ded04616b6b0c6bdfb26a0a673d9299fc
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46576649"
---
# <a name="mid-statement"></a><span data-ttu-id="759f6-102">Mid 陳述式</span><span class="sxs-lookup"><span data-stu-id="759f6-102">Mid Statement</span></span>
<span data-ttu-id="759f6-103">取代字元的指定的數目`String`變數與另一個字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="759f6-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="759f6-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="759f6-105">組件</span><span class="sxs-lookup"><span data-stu-id="759f6-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="759f6-106">必要。</span><span class="sxs-lookup"><span data-stu-id="759f6-106">Required.</span></span> <span data-ttu-id="759f6-107">名稱`String`修改的變數。</span><span class="sxs-lookup"><span data-stu-id="759f6-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="759f6-108">必要。</span><span class="sxs-lookup"><span data-stu-id="759f6-108">Required.</span></span> <span data-ttu-id="759f6-109">`Integer` 運算式。</span><span class="sxs-lookup"><span data-stu-id="759f6-109">`Integer` expression.</span></span> <span data-ttu-id="759f6-110">字元在位置`Target`取代文字的開始位置。</span><span class="sxs-lookup"><span data-stu-id="759f6-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="759f6-111">`Start` 使用以一為基的索引。</span><span class="sxs-lookup"><span data-stu-id="759f6-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="759f6-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="759f6-112">Optional.</span></span> <span data-ttu-id="759f6-113">`Integer` 運算式。</span><span class="sxs-lookup"><span data-stu-id="759f6-113">`Integer` expression.</span></span> <span data-ttu-id="759f6-114">若要取代的字元數。</span><span class="sxs-lookup"><span data-stu-id="759f6-114">Number of characters to replace.</span></span> <span data-ttu-id="759f6-115">如果省略，所有`String`用。</span><span class="sxs-lookup"><span data-stu-id="759f6-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="759f6-116">必要。</span><span class="sxs-lookup"><span data-stu-id="759f6-116">Required.</span></span> <span data-ttu-id="759f6-117">`String` 取代一部分的運算式`Target`。</span><span class="sxs-lookup"><span data-stu-id="759f6-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="759f6-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="759f6-118">Exceptions</span></span>  
  
|<span data-ttu-id="759f6-119">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="759f6-119">Exception type</span></span>|<span data-ttu-id="759f6-120">條件</span><span class="sxs-lookup"><span data-stu-id="759f6-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="759f6-121">`Start` < = 0 或`Length`< 0。</span><span class="sxs-lookup"><span data-stu-id="759f6-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="759f6-122">備註</span><span class="sxs-lookup"><span data-stu-id="759f6-122">Remarks</span></span>  
 <span data-ttu-id="759f6-123">被取代的字元數目一律為小於或等於中的字元數`Target`。</span><span class="sxs-lookup"><span data-stu-id="759f6-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="759f6-124">Visual Basic 也有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函式和`Mid`陳述式。</span><span class="sxs-lookup"><span data-stu-id="759f6-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="759f6-125">這些項目都會運作指定的字串中的字元數，但`Mid`函式會傳回的字元時`Mid`陳述式會取代字元。</span><span class="sxs-lookup"><span data-stu-id="759f6-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="759f6-126">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。</span><span class="sxs-lookup"><span data-stu-id="759f6-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="759f6-127">`MidB`舊版的 Visual Basic 的陳述式可以取代子字串的位元組，而不是字元。</span><span class="sxs-lookup"><span data-stu-id="759f6-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="759f6-128">它是主要用於將雙位元組字元集 (DBCS) 應用程式中的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="759f6-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="759f6-129">所有的 Visual Basic 字串為 Unicode，和`MidB`不受支援。</span><span class="sxs-lookup"><span data-stu-id="759f6-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="759f6-130">範例</span><span class="sxs-lookup"><span data-stu-id="759f6-130">Example</span></span>  
 <span data-ttu-id="759f6-131">這個範例會使用`Mid`陳述式來取代指定的字串變數中的字元數，從另一個字串的字元。</span><span class="sxs-lookup"><span data-stu-id="759f6-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="759f6-132">需求</span><span class="sxs-lookup"><span data-stu-id="759f6-132">Requirements</span></span>  
 <span data-ttu-id="759f6-133">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="759f6-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="759f6-134">**模組：** `Strings`</span><span class="sxs-lookup"><span data-stu-id="759f6-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="759f6-135">**組件︰** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759f6-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759f6-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="759f6-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="759f6-137">字串</span><span class="sxs-lookup"><span data-stu-id="759f6-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="759f6-138">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="759f6-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
