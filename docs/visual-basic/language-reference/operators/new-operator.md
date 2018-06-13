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
ms.openlocfilehash: 0fe511b2c16681d7bab7eeda7c121fcbbaa2f5dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603635"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="1f759-102">New 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f759-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="1f759-103">導入了`New`子句來建立新的物件執行個體，指定型別參數的建構函式條件約束，或識別`Sub`與類別建構函式的程序。</span><span class="sxs-lookup"><span data-stu-id="1f759-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f759-104">備註</span><span class="sxs-lookup"><span data-stu-id="1f759-104">Remarks</span></span>  
 <span data-ttu-id="1f759-105">在宣告或指派陳述式，`New`子句必須指定已定義的類別，可以從中建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f759-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="1f759-106">這表示類別必須公開一個或多個建構函式呼叫的程式碼可以存取。</span><span class="sxs-lookup"><span data-stu-id="1f759-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="1f759-107">您可以使用`New`宣告陳述式或指派陳述式中的子句。</span><span class="sxs-lookup"><span data-stu-id="1f759-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="1f759-108">陳述式執行時，它會呼叫適當的建構函式指定類別，並傳遞您提供任何引數。</span><span class="sxs-lookup"><span data-stu-id="1f759-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="1f759-109">下列範例會示範這藉由建立的執行個體`Customer`類別具有兩個建構函式不接受參數，一個可接受字串參數。</span><span class="sxs-lookup"><span data-stu-id="1f759-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="1f759-110">由於陣列是類別，`New`可以建立新的陣列執行個體，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1f759-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="1f759-111">Common language runtime (CLR) 擲回<xref:System.OutOfMemoryException>如果記憶體不足，無法建立新的執行個體的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f759-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f759-112">`New`關鍵字也用在型別參數清單來指定提供的型別必須公開存取的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="1f759-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="1f759-113">如需型別參數和條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="1f759-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="1f759-114">若要建立之類別的建構函式程序，將名稱設定`Sub`程序`New`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1f759-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="1f759-115">如需詳細資訊，請參閱[物件存留期： 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="1f759-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="1f759-116">`New` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="1f759-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1f759-117">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="1f759-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1f759-118">Of</span><span class="sxs-lookup"><span data-stu-id="1f759-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="1f759-119">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="1f759-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f759-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f759-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="1f759-121">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1f759-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1f759-122">類型清單</span><span class="sxs-lookup"><span data-stu-id="1f759-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="1f759-123">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="1f759-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="1f759-124">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="1f759-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
