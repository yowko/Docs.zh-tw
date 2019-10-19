---
title: Mid 語句（Visual Basic）
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
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581481"
---
# <a name="mid-statement"></a><span data-ttu-id="d46df-102">Mid 陳述式</span><span class="sxs-lookup"><span data-stu-id="d46df-102">Mid Statement</span></span>
<span data-ttu-id="d46df-103">以另一個字串中的字元取代 `String` 變數中指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="d46df-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d46df-104">語法</span><span class="sxs-lookup"><span data-stu-id="d46df-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="d46df-105">組件</span><span class="sxs-lookup"><span data-stu-id="d46df-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="d46df-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d46df-106">Required.</span></span> <span data-ttu-id="d46df-107">要修改之 `String` 變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d46df-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="d46df-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d46df-108">Required.</span></span> <span data-ttu-id="d46df-109">`Integer` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d46df-109">`Integer` expression.</span></span> <span data-ttu-id="d46df-110">@No__t_0 中的字元位置會開始取代文字。</span><span class="sxs-lookup"><span data-stu-id="d46df-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="d46df-111">`Start` 使用以一為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="d46df-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="d46df-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="d46df-112">Optional.</span></span> <span data-ttu-id="d46df-113">`Integer` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d46df-113">`Integer` expression.</span></span> <span data-ttu-id="d46df-114">要取代的字元數。</span><span class="sxs-lookup"><span data-stu-id="d46df-114">Number of characters to replace.</span></span> <span data-ttu-id="d46df-115">如果省略，則會使用所有的 `String`。</span><span class="sxs-lookup"><span data-stu-id="d46df-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="d46df-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="d46df-116">Required.</span></span> <span data-ttu-id="d46df-117">取代 `Target` 部分的 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d46df-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="d46df-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d46df-118">Exceptions</span></span>  
  
|<span data-ttu-id="d46df-119">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="d46df-119">Exception type</span></span>|<span data-ttu-id="d46df-120">條件</span><span class="sxs-lookup"><span data-stu-id="d46df-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="d46df-121">`Start` < = 0 或 `Length` < 0。</span><span class="sxs-lookup"><span data-stu-id="d46df-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d46df-122">備註</span><span class="sxs-lookup"><span data-stu-id="d46df-122">Remarks</span></span>  
 <span data-ttu-id="d46df-123">已取代的字元數一律小於或等於 `Target` 中的字元數。</span><span class="sxs-lookup"><span data-stu-id="d46df-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="d46df-124">Visual Basic 具有 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 函數和 `Mid` 語句。</span><span class="sxs-lookup"><span data-stu-id="d46df-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="d46df-125">這些專案都是在字串中以指定的字元數來運作，但是 `Mid` 函式會傳回字元，而 `Mid` 語句則會取代這些字元。</span><span class="sxs-lookup"><span data-stu-id="d46df-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="d46df-126">如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。</span><span class="sxs-lookup"><span data-stu-id="d46df-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d46df-127">舊版 Visual Basic 的 `MidB` 語句會取代子字串（以位元組為單位），而不是字元。</span><span class="sxs-lookup"><span data-stu-id="d46df-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="d46df-128">它主要是用來在雙位元組字集（DBCS）應用程式中轉換字串。</span><span class="sxs-lookup"><span data-stu-id="d46df-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="d46df-129">所有 Visual Basic 字串都是 Unicode，而且不再支援 `MidB`。</span><span class="sxs-lookup"><span data-stu-id="d46df-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d46df-130">範例</span><span class="sxs-lookup"><span data-stu-id="d46df-130">Example</span></span>  
 <span data-ttu-id="d46df-131">這個範例會使用 `Mid` 語句，將字串變數中指定數目的字元取代為另一個字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="d46df-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="d46df-132">需求</span><span class="sxs-lookup"><span data-stu-id="d46df-132">Requirements</span></span>  
 <span data-ttu-id="d46df-133">**命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="d46df-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="d46df-134">**模組：** `Strings`</span><span class="sxs-lookup"><span data-stu-id="d46df-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="d46df-135">**元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）</span><span class="sxs-lookup"><span data-stu-id="d46df-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d46df-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="d46df-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="d46df-137">字串</span><span class="sxs-lookup"><span data-stu-id="d46df-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="d46df-138">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="d46df-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
