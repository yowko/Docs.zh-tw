---
title: Mid 語句 (Visual Basic)
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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963543"
---
# <a name="mid-statement"></a><span data-ttu-id="8abba-102">Mid 陳述式</span><span class="sxs-lookup"><span data-stu-id="8abba-102">Mid Statement</span></span>
<span data-ttu-id="8abba-103">以另一個字串中的字元取代`String`變數中指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="8abba-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8abba-104">語法</span><span class="sxs-lookup"><span data-stu-id="8abba-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="8abba-105">組件</span><span class="sxs-lookup"><span data-stu-id="8abba-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="8abba-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="8abba-106">Required.</span></span> <span data-ttu-id="8abba-107">要修改之`String`變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8abba-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="8abba-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="8abba-108">Required.</span></span> <span data-ttu-id="8abba-109">`Integer`運算式.</span><span class="sxs-lookup"><span data-stu-id="8abba-109">`Integer` expression.</span></span> <span data-ttu-id="8abba-110">中`Target`的字元位置: 取代文字的開始位置。</span><span class="sxs-lookup"><span data-stu-id="8abba-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="8abba-111">`Start`使用以一個為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="8abba-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="8abba-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8abba-112">Optional.</span></span> <span data-ttu-id="8abba-113">`Integer`運算式.</span><span class="sxs-lookup"><span data-stu-id="8abba-113">`Integer` expression.</span></span> <span data-ttu-id="8abba-114">要取代的字元數。</span><span class="sxs-lookup"><span data-stu-id="8abba-114">Number of characters to replace.</span></span> <span data-ttu-id="8abba-115">如果省略, `String`則會使用所有。</span><span class="sxs-lookup"><span data-stu-id="8abba-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="8abba-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="8abba-116">Required.</span></span> <span data-ttu-id="8abba-117">`String`取代部分的`Target`運算式。</span><span class="sxs-lookup"><span data-stu-id="8abba-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="8abba-118">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8abba-118">Exceptions</span></span>  
  
|<span data-ttu-id="8abba-119">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="8abba-119">Exception type</span></span>|<span data-ttu-id="8abba-120">條件</span><span class="sxs-lookup"><span data-stu-id="8abba-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="8abba-121">`Start`< = 0 或`Length` < 0。</span><span class="sxs-lookup"><span data-stu-id="8abba-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8abba-122">備註</span><span class="sxs-lookup"><span data-stu-id="8abba-122">Remarks</span></span>  
 <span data-ttu-id="8abba-123">已取代的字元數一律小於或等於中`Target`的字元數。</span><span class="sxs-lookup"><span data-stu-id="8abba-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="8abba-124">Visual Basic 具有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函數`Mid`和語句。</span><span class="sxs-lookup"><span data-stu-id="8abba-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="8abba-125">這些專案都是在字串中以指定的字元數來運作, 但是`Mid`函式會傳回字元, `Mid`而語句則會取代這些字元。</span><span class="sxs-lookup"><span data-stu-id="8abba-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="8abba-126">如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Strings.Mid%2A>。</span><span class="sxs-lookup"><span data-stu-id="8abba-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8abba-127">舊版`MidB` Visual Basic 的語句會取代子字串 (以位元組為單位), 而不是字元。</span><span class="sxs-lookup"><span data-stu-id="8abba-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="8abba-128">它主要是用來在雙位元組字集 (DBCS) 應用程式中轉換字串。</span><span class="sxs-lookup"><span data-stu-id="8abba-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="8abba-129">所有 Visual Basic 字串都是 Unicode, `MidB`不再受到支援。</span><span class="sxs-lookup"><span data-stu-id="8abba-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8abba-130">範例</span><span class="sxs-lookup"><span data-stu-id="8abba-130">Example</span></span>  
 <span data-ttu-id="8abba-131">這個範例會使用`Mid`語句, 將字串變數中指定數目的字元取代為另一個字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="8abba-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="8abba-132">需求</span><span class="sxs-lookup"><span data-stu-id="8abba-132">Requirements</span></span>  
 <span data-ttu-id="8abba-133">**命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="8abba-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="8abba-134">**模組:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="8abba-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="8abba-135">**Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="8abba-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8abba-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8abba-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="8abba-137">字串</span><span class="sxs-lookup"><span data-stu-id="8abba-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="8abba-138">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="8abba-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
