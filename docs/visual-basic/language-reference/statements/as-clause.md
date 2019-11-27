---
title: As 子句
ms.date: 07/20/2015
f1_keywords:
- vb.as
helpviewer_keywords:
- constraints, Visual Basic generic types
- As keyword [Visual Basic], statement syntax
- As keyword [Visual Basic]
ms.assetid: b4281ec8-2be5-49f7-aae8-ae0a96265b0d
ms.openlocfilehash: cf1acbfeee150f1ea353ce134a4e94dab9928e8a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350178"
---
# <a name="as-clause-visual-basic"></a><span data-ttu-id="bbdfb-102">As 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbdfb-102">As Clause (Visual Basic)</span></span>
<span data-ttu-id="bbdfb-103">引進了一個 `As` 子句，它會識別宣告語句中的資料類型或泛型型別參數的條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="bbdfb-103">Introduces an `As` clause, which identifies a data type in a declaration statement or a constraint list on a generic type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbdfb-104">備註</span><span class="sxs-lookup"><span data-stu-id="bbdfb-104">Remarks</span></span>  
 <span data-ttu-id="bbdfb-105">`As` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="bbdfb-105">The `As` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bbdfb-106">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-106">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
  
 [<span data-ttu-id="bbdfb-107">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-107">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="bbdfb-108">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-108">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="bbdfb-109">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="bbdfb-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="bbdfb-111">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="bbdfb-112">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-112">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="bbdfb-113">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-113">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="bbdfb-114">針對 .。。下一個語句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-114">For...Next Statements</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
  
 [<span data-ttu-id="bbdfb-115">針對每個 .。。下一個語句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-115">For Each...Next Statements</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
  
 [<span data-ttu-id="bbdfb-116">From 子句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-116">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
  
 [<span data-ttu-id="bbdfb-117">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-117">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bbdfb-118">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-118">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
  
 [<span data-ttu-id="bbdfb-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="bbdfb-120">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="bbdfb-120">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="bbdfb-121">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bbdfb-122">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="bbdfb-123">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="bbdfb-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
 [<span data-ttu-id="bbdfb-124">嘗試 .。。Catch .。。Finally 語句</span><span class="sxs-lookup"><span data-stu-id="bbdfb-124">Try...Catch...Finally Statements</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bbdfb-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbdfb-125">See also</span></span>

- [<span data-ttu-id="bbdfb-126">如何：建立新的變數</span><span class="sxs-lookup"><span data-stu-id="bbdfb-126">How to: Create a New Variable</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [<span data-ttu-id="bbdfb-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="bbdfb-127">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="bbdfb-128">變數宣告</span><span class="sxs-lookup"><span data-stu-id="bbdfb-128">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="bbdfb-129">類型清單</span><span class="sxs-lookup"><span data-stu-id="bbdfb-129">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="bbdfb-130">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="bbdfb-130">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="bbdfb-131">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bbdfb-131">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
