---
title: New 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837690"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="bb0f5-102">New 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb0f5-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="bb0f5-103">導入了`New`子句，以建立新的物件執行個體，指定型別參數的建構函式條件約束，或識別`Sub`類別建構函式與程序。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb0f5-104">備註</span><span class="sxs-lookup"><span data-stu-id="bb0f5-104">Remarks</span></span>  
 <span data-ttu-id="bb0f5-105">在宣告或指派陳述式，`New`子句必須指定已定義的類別，可以從中建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="bb0f5-106">這表示此類別必須公開一或多個建構函式呼叫的程式碼可以存取。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="bb0f5-107">您可以使用`New`宣告陳述式或指派陳述式中的子句。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="bb0f5-108">陳述式執行時，它會呼叫指定的類別，將您提供任何引數傳遞的適當建構函式。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="bb0f5-109">下列範例所示範的是這所建立的執行個體`Customer`有兩個建構函式的類別，其中一個不接受任何參數，另一個會採用字串參數。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="bb0f5-110">由於陣列是類別，`New`可以建立新的陣列執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="bb0f5-111">Common language runtime (CLR) 會擲回<xref:System.OutOfMemoryException>錯誤，如果沒有記憶體不足，無法建立新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb0f5-112">`New`關鍵字也用在類型參數清單中，指定提供的型別必須公開存取的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="bb0f5-113">如需有關型別參數和條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="bb0f5-114">若要建立類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="bb0f5-115">如需詳細資訊，請參閱[物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="bb0f5-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="bb0f5-116">`New` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="bb0f5-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bb0f5-117">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb0f5-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="bb0f5-118">Of</span><span class="sxs-lookup"><span data-stu-id="bb0f5-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="bb0f5-119">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb0f5-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb0f5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb0f5-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="bb0f5-121">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bb0f5-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="bb0f5-122">類型清單</span><span class="sxs-lookup"><span data-stu-id="bb0f5-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="bb0f5-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb0f5-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="bb0f5-124">物件存留期：如何建立和終結物件</span><span class="sxs-lookup"><span data-stu-id="bb0f5-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
