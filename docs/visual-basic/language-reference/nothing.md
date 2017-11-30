---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6932fee01ec6f39f67fb1a26a9a5b5cbd47d9767
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nothing-visual-basic"></a><span data-ttu-id="c68e0-102">Nothing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c68e0-102">Nothing (Visual Basic)</span></span>
<span data-ttu-id="c68e0-103">代表任何資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c68e0-103">Represents the default value of any data type.</span></span> <span data-ttu-id="c68e0-104">預設值是參考類型`null`參考。</span><span class="sxs-lookup"><span data-stu-id="c68e0-104">For reference types, the default value is the `null` reference.</span></span> <span data-ttu-id="c68e0-105">對於實值類型的預設值取決於是否可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="c68e0-105">For value types, the default value depends on whether the value type is nullable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c68e0-106">不可為 null 的實值型別，`Nothing`在 Visual Basic 中不同於`null`C# 中。</span><span class="sxs-lookup"><span data-stu-id="c68e0-106">For non-nullable value types, `Nothing` in Visual Basic differs from `null` in C#.</span></span> <span data-ttu-id="c68e0-107">在 Visual Basic，如果您設定的非 null 值型別變數`Nothing`，此變數會設為其宣告類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c68e0-107">In Visual Basic, if you set a variable of a non-nullable value type to `Nothing`, the variable is set to the default value for its declared type.</span></span> <span data-ttu-id="c68e0-108">在 C# 中，如果您指派的變數不可為 null 的實值型別`null`，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c68e0-108">In C#, if you assign a variable of a non-nullable value type to `null`, a compile-time error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c68e0-109">備註</span><span class="sxs-lookup"><span data-stu-id="c68e0-109">Remarks</span></span>  
 <span data-ttu-id="c68e0-110">`Nothing`代表資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c68e0-110">`Nothing` represents the default value of a data type.</span></span> <span data-ttu-id="c68e0-111">預設值取決於變數是否是實值類型或參考型別。</span><span class="sxs-lookup"><span data-stu-id="c68e0-111">The default value depends on whether the variable is of a value type or of a reference type.</span></span>  
  
 <span data-ttu-id="c68e0-112">變數的*實值型別*直接包含其值。</span><span class="sxs-lookup"><span data-stu-id="c68e0-112">A variable of a *value type* directly contains its value.</span></span> <span data-ttu-id="c68e0-113">實值型別包含所有的數值資料類型， `Boolean`， `Char`， `Date`，所有的結構，以及所有列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c68e0-113">Value types include all numeric data types, `Boolean`, `Char`, `Date`, all structures, and all enumerations.</span></span> <span data-ttu-id="c68e0-114">變數的*參考型別*儲存在記憶體中物件的執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="c68e0-114">A variable of a *reference type* stores a reference to an instance of the object in memory.</span></span> <span data-ttu-id="c68e0-115">參考類型包括類別、 陣列、 委派和字串。</span><span class="sxs-lookup"><span data-stu-id="c68e0-115">Reference types include classes, arrays, delegates, and strings.</span></span> <span data-ttu-id="c68e0-116">如需詳細資訊，請參閱 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c68e0-116">For more information, see [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
 <span data-ttu-id="c68e0-117">如果變數是實值類型，行為`Nothing`取決於是否可為 null 的資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="c68e0-117">If a variable is of a value type, the behavior of `Nothing` depends on whether the variable is of a nullable data type.</span></span> <span data-ttu-id="c68e0-118">若要表示 null 的實值類型，新增`?`修飾詞加入型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c68e0-118">To represent a nullable value type, add a `?` modifier to the type name.</span></span> <span data-ttu-id="c68e0-119">指派`Nothing`可為 null 的變數的值設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-119">Assigning `Nothing` to a nullable variable sets the value to `null`.</span></span> <span data-ttu-id="c68e0-120">如需詳細資訊和範例，請參閱[可為 Null 的實值型別](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c68e0-120">For more information and examples, see [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>  
  
 <span data-ttu-id="c68e0-121">如果變數屬於實值型別不是可為 null，指派`Nothing`到它將它設定為預設值為其宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="c68e0-121">If a variable is of a value type that is not nullable, assigning `Nothing` to it sets it to the default value for its declared type.</span></span> <span data-ttu-id="c68e0-122">如果該類型包含可變成員，它們是全部設定為其預設值。</span><span class="sxs-lookup"><span data-stu-id="c68e0-122">If that type contains variable members, they are all set to their default values.</span></span> <span data-ttu-id="c68e0-123">下列範例將說明這點的純量類型。</span><span class="sxs-lookup"><span data-stu-id="c68e0-123">The following example illustrates this for scalar types.</span></span>  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 <span data-ttu-id="c68e0-124">如果變數屬於參考型別，指派`Nothing`變數將其設為`null`參考變數的類型。</span><span class="sxs-lookup"><span data-stu-id="c68e0-124">If a variable is of a reference type, assigning `Nothing` to the variable sets it to a `null` reference of the variable's type.</span></span> <span data-ttu-id="c68e0-125">此變數會設為`null`參考不是任何物件相關聯。</span><span class="sxs-lookup"><span data-stu-id="c68e0-125">A variable that is set to a `null` reference is not associated with any object.</span></span> <span data-ttu-id="c68e0-126">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="c68e0-126">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 <span data-ttu-id="c68e0-127">當檢查是否參考 （或 null 的實值類型） 變數`null`，請勿使用`= Nothing`或`<> Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-127">When checking whether a reference (or nullable value type) variable is `null`, do not use `= Nothing` or `<> Nothing`.</span></span> <span data-ttu-id="c68e0-128">一律使用`Is Nothing`或`IsNot Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-128">Always use `Is Nothing` or `IsNot Nothing`.</span></span>  
  
 <span data-ttu-id="c68e0-129">在 Visual Basic 中的字串，則為空字串等於`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-129">For strings in Visual Basic, the empty string equals `Nothing`.</span></span> <span data-ttu-id="c68e0-130">因此，`"" = Nothing`為 true。</span><span class="sxs-lookup"><span data-stu-id="c68e0-130">Therefore, `"" = Nothing` is true.</span></span>  
  
 <span data-ttu-id="c68e0-131">下列範例顯示使用的比較`Is`和`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="c68e0-131">The following example shows comparisons that use the `Is` and `IsNot` operators.</span></span>  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 <span data-ttu-id="c68e0-132">如果您宣告變數，而不使用`As`子句並將它設定為`Nothing`，變數會有一種`Object`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-132">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="c68e0-133">舉例來說，這是`Dim something = Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c68e0-133">An example of this is `Dim something = Nothing`.</span></span> <span data-ttu-id="c68e0-134">編譯時間錯誤，就會發生這種情況下時`Option Strict`上和`Option Infer`已關閉。</span><span class="sxs-lookup"><span data-stu-id="c68e0-134">A compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is off.</span></span>  
  
 <span data-ttu-id="c68e0-135">當您指派`Nothing`物件變數，即不再參考任何物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c68e0-135">When you assign `Nothing` to an object variable, it no longer refers to any object instance.</span></span> <span data-ttu-id="c68e0-136">如果執行個體，之前已參考變數，將它設定為`Nothing`並不會終止執行個體本身。</span><span class="sxs-lookup"><span data-stu-id="c68e0-136">If the variable had previously referred to an instance, setting it to `Nothing` does not terminate the instance itself.</span></span> <span data-ttu-id="c68e0-137">終止執行個體，並與它相關聯的記憶體和系統資源之後才, 釋放記憶體回收行程 (GC) 偵測到沒有剩餘的作用中參考。</span><span class="sxs-lookup"><span data-stu-id="c68e0-137">The instance is terminated, and the memory and system resources associated with it are released, only after the garbage collector (GC) detects that there are no active references remaining.</span></span>  
  
 <span data-ttu-id="c68e0-138">`Nothing`不同於<xref:System.DBNull>物件，代表未初始化的變數或不存在的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="c68e0-138">`Nothing` differs from the <xref:System.DBNull> object, which represents an uninitialized variant or a nonexistent database column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68e0-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c68e0-139">See Also</span></span>  
 [<span data-ttu-id="c68e0-140">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="c68e0-140">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="c68e0-141">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="c68e0-141">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="c68e0-142">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="c68e0-142">Lifetime in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="c68e0-143">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="c68e0-143">Is Operator</span></span>](../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="c68e0-144">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="c68e0-144">IsNot Operator</span></span>](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="c68e0-145">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="c68e0-145">Nullable Value Types</span></span>](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
