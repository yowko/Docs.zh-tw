---
title: "Mid 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61d812ef91acc65728b04efc9aa99e3975e71d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mid-statement"></a><span data-ttu-id="f19fb-102">Mid 陳述式</span><span class="sxs-lookup"><span data-stu-id="f19fb-102">Mid Statement</span></span>
<span data-ttu-id="f19fb-103">取代指定的字元數`String`變數與另一個字串的字元。</span><span class="sxs-lookup"><span data-stu-id="f19fb-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="f19fb-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="f19fb-105">組件</span><span class="sxs-lookup"><span data-stu-id="f19fb-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="f19fb-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="f19fb-106">Required.</span></span> <span data-ttu-id="f19fb-107">名稱`String`修改變數。</span><span class="sxs-lookup"><span data-stu-id="f19fb-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="f19fb-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f19fb-108">Required.</span></span> <span data-ttu-id="f19fb-109">`Integer`運算式。</span><span class="sxs-lookup"><span data-stu-id="f19fb-109">`Integer` expression.</span></span> <span data-ttu-id="f19fb-110">字元位置`Target`開始取代文字。</span><span class="sxs-lookup"><span data-stu-id="f19fb-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="f19fb-111">`Start`會使用 1 為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="f19fb-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="f19fb-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f19fb-112">Optional.</span></span> <span data-ttu-id="f19fb-113">`Integer`運算式。</span><span class="sxs-lookup"><span data-stu-id="f19fb-113">`Integer` expression.</span></span> <span data-ttu-id="f19fb-114">要取代的字元數。</span><span class="sxs-lookup"><span data-stu-id="f19fb-114">Number of characters to replace.</span></span> <span data-ttu-id="f19fb-115">如果省略，則所有`String`用。</span><span class="sxs-lookup"><span data-stu-id="f19fb-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="f19fb-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="f19fb-116">Required.</span></span> <span data-ttu-id="f19fb-117">`String`取代部份的運算式`Target`。</span><span class="sxs-lookup"><span data-stu-id="f19fb-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="f19fb-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="f19fb-118">Exceptions</span></span>  
  
|<span data-ttu-id="f19fb-119">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="f19fb-119">Exception type</span></span>|<span data-ttu-id="f19fb-120">條件</span><span class="sxs-lookup"><span data-stu-id="f19fb-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="f19fb-121">`Start`< = 0 或`Length`< 0。</span><span class="sxs-lookup"><span data-stu-id="f19fb-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f19fb-122">備註</span><span class="sxs-lookup"><span data-stu-id="f19fb-122">Remarks</span></span>  
 <span data-ttu-id="f19fb-123">被取代的字元數目一律為小於或等於中的字元數`Target`。</span><span class="sxs-lookup"><span data-stu-id="f19fb-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="f19fb-124">Visual Basic 擁有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函式和`Mid`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f19fb-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="f19fb-125">兩者的指定數目的字元在字串中, 操作這些項目但`Mid`函式會傳回的字元時`Mid`陳述式會取代字元。</span><span class="sxs-lookup"><span data-stu-id="f19fb-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="f19fb-126">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。</span><span class="sxs-lookup"><span data-stu-id="f19fb-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f19fb-127">`MidB`較舊版本的 Visual Basic 的陳述式可以取代位元組，而非字元的子字串。</span><span class="sxs-lookup"><span data-stu-id="f19fb-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="f19fb-128">它是主要用來轉換雙位元組字元集 (DBCS) 應用程式中的字串。</span><span class="sxs-lookup"><span data-stu-id="f19fb-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="f19fb-129">所有的 Visual Basic 字串都位於 Unicode，和`MidB`不再支援。</span><span class="sxs-lookup"><span data-stu-id="f19fb-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f19fb-130">範例</span><span class="sxs-lookup"><span data-stu-id="f19fb-130">Example</span></span>  
 <span data-ttu-id="f19fb-131">這個範例會使用`Mid`陳述式來取代指定的字串變數中的字元數，另一個字串的字元。</span><span class="sxs-lookup"><span data-stu-id="f19fb-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="f19fb-132">需求</span><span class="sxs-lookup"><span data-stu-id="f19fb-132">Requirements</span></span>  
 <span data-ttu-id="f19fb-133">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="f19fb-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="f19fb-134">**模組：**`Strings`</span><span class="sxs-lookup"><span data-stu-id="f19fb-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="f19fb-135">**組件︰** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f19fb-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19fb-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f19fb-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="f19fb-137">字串</span><span class="sxs-lookup"><span data-stu-id="f19fb-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="f19fb-138">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="f19fb-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
