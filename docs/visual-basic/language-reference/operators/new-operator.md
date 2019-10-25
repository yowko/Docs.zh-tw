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
ms.openlocfilehash: c0870f4b056658a22928769c369024cdda24f354
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799045"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="692bb-102">New 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="692bb-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="692bb-103">引進了一個 `New` 子句來建立新的物件實例、在型別參數上指定一個函式條件約束，或將 `Sub` 的程式識別為類別的函式。</span><span class="sxs-lookup"><span data-stu-id="692bb-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="692bb-104">備註</span><span class="sxs-lookup"><span data-stu-id="692bb-104">Remarks</span></span>

<span data-ttu-id="692bb-105">在宣告或指派語句中，`New` 子句必須指定可從中建立實例的已定義類別。</span><span class="sxs-lookup"><span data-stu-id="692bb-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="692bb-106">這表示類別必須公開呼叫程式碼可以存取的一個或多個函式。</span><span class="sxs-lookup"><span data-stu-id="692bb-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="692bb-107">您可以在宣告語句或指派語句中使用 `New` 子句。</span><span class="sxs-lookup"><span data-stu-id="692bb-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="692bb-108">當語句執行時，它會呼叫指定類別的適當的函式，並傳遞您所提供的任何引數。</span><span class="sxs-lookup"><span data-stu-id="692bb-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="692bb-109">下列範例會藉由建立具有兩個函式的 `Customer` 類別實例（其中一個不接受參數，另一個採用字串參數）來示範：</span><span class="sxs-lookup"><span data-stu-id="692bb-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="692bb-110">由於陣列是類別，因此 `New` 可以建立新的陣列實例，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="692bb-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="692bb-111">如果記憶體不足，無法建立新的實例，則 common language runtime （CLR）會擲回 <xref:System.OutOfMemoryException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="692bb-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="692bb-112">`New` 關鍵字也會用於型別參數清單中，以指定提供的型別必須公開可存取的無參數函數。</span><span class="sxs-lookup"><span data-stu-id="692bb-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="692bb-113">如需型別參數和條件約束的詳細資訊，請參閱[Type List](../statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="692bb-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="692bb-114">若要建立類別的函式程式，請將 `Sub` 程式的名稱設定為 `New` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="692bb-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="692bb-115">如需詳細資訊，請參閱[物件存留期：物件的建立和終結方式](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="692bb-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="692bb-116">`New` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="692bb-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="692bb-117">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="692bb-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="692bb-118">Of</span><span class="sxs-lookup"><span data-stu-id="692bb-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="692bb-119">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="692bb-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="692bb-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="692bb-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="692bb-121">關鍵字</span><span class="sxs-lookup"><span data-stu-id="692bb-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="692bb-122">類型清單</span><span class="sxs-lookup"><span data-stu-id="692bb-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="692bb-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="692bb-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="692bb-124">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="692bb-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
