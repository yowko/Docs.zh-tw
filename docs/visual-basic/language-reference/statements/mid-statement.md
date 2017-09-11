---
title: "Mid 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e94500c8bd7f2c6351c91ba028c1ad6d8d3dd4c3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="mid-statement"></a><span data-ttu-id="b48c3-102">Mid 陳述式</span><span class="sxs-lookup"><span data-stu-id="b48c3-102">Mid Statement</span></span>
<span data-ttu-id="b48c3-103">取代指定的字元數`String`變數與另一個字串的字元。</span><span class="sxs-lookup"><span data-stu-id="b48c3-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b48c3-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="b48c3-105">組件</span><span class="sxs-lookup"><span data-stu-id="b48c3-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="b48c3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="b48c3-106">Required.</span></span> <span data-ttu-id="b48c3-107">名稱`String`若要修改的變數。</span><span class="sxs-lookup"><span data-stu-id="b48c3-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="b48c3-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="b48c3-108">Required.</span></span> <span data-ttu-id="b48c3-109">`Integer`運算式。</span><span class="sxs-lookup"><span data-stu-id="b48c3-109">`Integer` expression.</span></span> <span data-ttu-id="b48c3-110">字元位置`Target`取代文字的開始位置。</span><span class="sxs-lookup"><span data-stu-id="b48c3-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="b48c3-111">`Start`使用起始的索引。</span><span class="sxs-lookup"><span data-stu-id="b48c3-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="b48c3-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="b48c3-112">Optional.</span></span> <span data-ttu-id="b48c3-113">`Integer`運算式。</span><span class="sxs-lookup"><span data-stu-id="b48c3-113">`Integer` expression.</span></span> <span data-ttu-id="b48c3-114">要取代的字元數。</span><span class="sxs-lookup"><span data-stu-id="b48c3-114">Number of characters to replace.</span></span> <span data-ttu-id="b48c3-115">如果省略，所有的`String`用。</span><span class="sxs-lookup"><span data-stu-id="b48c3-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="b48c3-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="b48c3-116">Required.</span></span> <span data-ttu-id="b48c3-117">`String`取代部份的運算式`Target`。</span><span class="sxs-lookup"><span data-stu-id="b48c3-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="b48c3-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b48c3-118">Exceptions</span></span>  
  
|<span data-ttu-id="b48c3-119">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="b48c3-119">Exception type</span></span>|<span data-ttu-id="b48c3-120">條件</span><span class="sxs-lookup"><span data-stu-id="b48c3-120">Condition</span></span>|  
|--------------------|---------------|  
|<span data-ttu-id="b48c3-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="b48c3-121"><xref:System.ArgumentException></span></span>|<span data-ttu-id="b48c3-122">`Start`<= 0="" or=""></=>`Length`< 0.></ 0.></span><span class="sxs-lookup"><span data-stu-id="b48c3-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b48c3-123">備註</span><span class="sxs-lookup"><span data-stu-id="b48c3-123">Remarks</span></span>  
 <span data-ttu-id="b48c3-124">被取代的字元數目一律為小於或等於中的字元數`Target`。</span><span class="sxs-lookup"><span data-stu-id="b48c3-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="b48c3-125">Visual Basic 也有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函式和`Mid`陳述式。</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="b48c3-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="b48c3-126">這些項目都會運作指定的字串中的字元數，但`Mid`函式傳回的字元時`Mid`陳述式會取代字元。</span><span class="sxs-lookup"><span data-stu-id="b48c3-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="b48c3-127">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="b48c3-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b48c3-128">`MidB`舊版的 Visual Basic 的陳述式可以取代位元組，而不是字元的子字串。</span><span class="sxs-lookup"><span data-stu-id="b48c3-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="b48c3-129">它是主要用於轉換雙位元組字元集 (DBCS) 應用程式中的字串。</span><span class="sxs-lookup"><span data-stu-id="b48c3-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="b48c3-130">所有的 Visual Basic 字串是在 Unicode 中，和`MidB`不受支援。</span><span class="sxs-lookup"><span data-stu-id="b48c3-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b48c3-131">範例</span><span class="sxs-lookup"><span data-stu-id="b48c3-131">Example</span></span>  
 <span data-ttu-id="b48c3-132">這個範例會使用`Mid`陳述式來取代指定的字串變數中的字元數，另一個字串的字元。</span><span class="sxs-lookup"><span data-stu-id="b48c3-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 <span data-ttu-id="b48c3-133">[!code-vb[VbVbalrStrings #&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b48c3-133">[!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b48c3-134">需求</span><span class="sxs-lookup"><span data-stu-id="b48c3-134">Requirements</span></span>  
 <span data-ttu-id="b48c3-135">**命名空間︰** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b48c3-135">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="b48c3-136">**Module:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="b48c3-136">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="b48c3-137">**組件︰**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span><span class="sxs-lookup"><span data-stu-id="b48c3-137">**Assembly:** [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48c3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b48c3-138">See Also</span></span>  
 <span data-ttu-id="b48c3-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="b48c3-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
<span data-ttu-id="b48c3-140"> [字串](../../../visual-basic/programming-guide/language-features/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="b48c3-140"> [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md) </span></span>  
<span data-ttu-id="b48c3-141"> [在 Visual Basic 中的字串簡介](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="b48c3-141"> [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
