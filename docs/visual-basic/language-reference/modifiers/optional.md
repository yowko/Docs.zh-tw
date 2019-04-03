---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820785"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="d772d-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d772d-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="d772d-103">指定呼叫程序時，可以省略程序引數。</span><span class="sxs-lookup"><span data-stu-id="d772d-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d772d-104">備註</span><span class="sxs-lookup"><span data-stu-id="d772d-104">Remarks</span></span>  
 <span data-ttu-id="d772d-105">每一個選擇性的參數，您必須指定該參數的預設值的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="d772d-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="d772d-106">如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，值的資料類型的預設值做為參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="d772d-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="d772d-107">如果參數清單包含選擇性參數，便會跟隨它的每個參數也必須是選擇性。</span><span class="sxs-lookup"><span data-stu-id="d772d-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="d772d-108">`Optional` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d772d-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="d772d-109">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="d772d-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="d772d-110">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d772d-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="d772d-111">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="d772d-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="d772d-112">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d772d-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="d772d-113">呼叫程序時使用或不含選擇性參數，您可以依位置或依名稱傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="d772d-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="d772d-114">如需詳細資訊，請參閱 <<c0> [ 傳遞引數依位置和名稱](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。</span><span class="sxs-lookup"><span data-stu-id="d772d-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d772d-115">您也可以使用多載，以定義與選擇性參數的程序。</span><span class="sxs-lookup"><span data-stu-id="d772d-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="d772d-116">如果您有一個選擇性參數，您可以定義兩個程序，一個可接受的參數，其中並不多載的版本。</span><span class="sxs-lookup"><span data-stu-id="d772d-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="d772d-117">如需詳細資訊，請參閱 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="d772d-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d772d-118">範例</span><span class="sxs-lookup"><span data-stu-id="d772d-118">Example</span></span>  
 <span data-ttu-id="d772d-119">下列範例會定義具有一個選擇性參數的程序。</span><span class="sxs-lookup"><span data-stu-id="d772d-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="d772d-120">範例</span><span class="sxs-lookup"><span data-stu-id="d772d-120">Example</span></span>  
 <span data-ttu-id="d772d-121">下列範例示範如何呼叫程序，使用依位置傳遞的引數，並以依名稱傳遞的引數。</span><span class="sxs-lookup"><span data-stu-id="d772d-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="d772d-122">程序中的兩個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d772d-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d772d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d772d-123">See also</span></span>

- [<span data-ttu-id="d772d-124">參數清單</span><span class="sxs-lookup"><span data-stu-id="d772d-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="d772d-125">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="d772d-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="d772d-126">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d772d-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
