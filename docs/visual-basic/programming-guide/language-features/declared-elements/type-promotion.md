---
title: 類型提升 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb0d61f0f1c94e8e28493d0c62afe1e09503804
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="c7f04-102">類型提升 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7f04-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="c7f04-103">當您宣告的模組中的程式設計項目時，Visual Basic 會將其範圍包含模組的命名空間以提升。</span><span class="sxs-lookup"><span data-stu-id="c7f04-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="c7f04-104">這稱為*輸入促銷*。</span><span class="sxs-lookup"><span data-stu-id="c7f04-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="c7f04-105">下列範例會示範模組的基本架構定義，該模組的兩個成員。</span><span class="sxs-lookup"><span data-stu-id="c7f04-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 <span data-ttu-id="c7f04-106">內`projModule`程式設計，在模組層級宣告的項目會提升至`projNamespace`。</span><span class="sxs-lookup"><span data-stu-id="c7f04-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="c7f04-107">在上述範例中，`basicEnum`和`innerClass`會升級，但`numberSub`不是，因為它未宣告為在模組層級。</span><span class="sxs-lookup"><span data-stu-id="c7f04-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="c7f04-108">類型提升的效果</span><span class="sxs-lookup"><span data-stu-id="c7f04-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="c7f04-109">類型提升的效果是限定性條件字串不需要包含模組名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f04-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="c7f04-110">下列範例會在上述範例中的兩個呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="c7f04-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 <span data-ttu-id="c7f04-111">在上述範例中，第一次呼叫會使用完整限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="c7f04-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="c7f04-112">不過，這是不必要因為型別提升。</span><span class="sxs-lookup"><span data-stu-id="c7f04-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="c7f04-113">第二個呼叫也存取模組的成員不包括`projModule`限定性條件字串中。</span><span class="sxs-lookup"><span data-stu-id="c7f04-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="c7f04-114">型別提升失敗</span><span class="sxs-lookup"><span data-stu-id="c7f04-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="c7f04-115">如果命名空間中已經有具有相同名稱做為模組成員的成員，型別提升將無效該模組成員。</span><span class="sxs-lookup"><span data-stu-id="c7f04-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="c7f04-116">下列範例顯示基本架構定義的列舉型別和相同的命名空間內的模組。</span><span class="sxs-lookup"><span data-stu-id="c7f04-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 <span data-ttu-id="c7f04-117">在上述範例中，Visual Basic 無法將升級類別`abc`至`thisNameSpace`因為已經有具有相同名稱的命名空間層級的列舉。</span><span class="sxs-lookup"><span data-stu-id="c7f04-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="c7f04-118">若要存取`abcSub`，您必須使用完整限定性條件字串`thisNamespace.thisModule.abc.abcSub`。</span><span class="sxs-lookup"><span data-stu-id="c7f04-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="c7f04-119">不過，類別`xyz`仍然會升級，而且您可以存取`xyzSub`使用較短的限定性條件字串`thisNamespace.xyz.xyzSub`。</span><span class="sxs-lookup"><span data-stu-id="c7f04-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="c7f04-120">部分類型的型別提升失敗</span><span class="sxs-lookup"><span data-stu-id="c7f04-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="c7f04-121">如果類別或結構，在模組內使用[部分](../../../../visual-basic/language-reference/modifiers/partial.md)關鍵字，型別提升會自動失效該類別或結構，指出是否在命名空間具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="c7f04-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="c7f04-122">模組中的其他項目都仍有資格型別提升。</span><span class="sxs-lookup"><span data-stu-id="c7f04-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="c7f04-123">**結果。**</span><span class="sxs-lookup"><span data-stu-id="c7f04-123">**Consequences.**</span></span> <span data-ttu-id="c7f04-124">部分定義的型別提升失敗可能會導致非預期的結果，甚至是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7f04-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="c7f04-125">下列範例顯示基本架構的類別，其中是在模組內的部分定義。</span><span class="sxs-lookup"><span data-stu-id="c7f04-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 <span data-ttu-id="c7f04-126">在上述範例中，開發人員可能預期要合併兩個部分定義的編譯器`sampleClass`。</span><span class="sxs-lookup"><span data-stu-id="c7f04-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="c7f04-127">不過，編譯器不會考慮的部分定義內的升級`sampleModule`。</span><span class="sxs-lookup"><span data-stu-id="c7f04-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="c7f04-128">如此一來，它會嘗試編譯兩個個別且不同的類別，名為`sampleClass`但具有不同的限定性條件路徑。</span><span class="sxs-lookup"><span data-stu-id="c7f04-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="c7f04-129">只有在完整路徑相同時，編譯器才會合併部分定義。</span><span class="sxs-lookup"><span data-stu-id="c7f04-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="c7f04-130">建議</span><span class="sxs-lookup"><span data-stu-id="c7f04-130">Recommendations</span></span>  
 <span data-ttu-id="c7f04-131">下列建議代表良好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="c7f04-131">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="c7f04-132">**唯一的名稱。**</span><span class="sxs-lookup"><span data-stu-id="c7f04-132">**Unique Names.**</span></span> <span data-ttu-id="c7f04-133">當您擁有完整控制權的程式設計項目命名時，最好一律 everywhere 使用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7f04-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="c7f04-134">相同的名稱需要額外的限定性條件，而且可以讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="c7f04-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="c7f04-135">它們也可能導致難以察覺的錯誤和非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="c7f04-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="c7f04-136">**完整限定性條件。**</span><span class="sxs-lookup"><span data-stu-id="c7f04-136">**Full Qualification.**</span></span> <span data-ttu-id="c7f04-137">當您使用模組，以及相同的命名空間中其他項目時，最安全的方法就是一律使用完整限定性條件的所有程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="c7f04-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="c7f04-138">如果型別提升將無效的模組成員，而且未完整限定該成員，您不小心無法存取不同的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="c7f04-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f04-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f04-139">See Also</span></span>  
 [<span data-ttu-id="c7f04-140">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="c7f04-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="c7f04-141">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="c7f04-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="c7f04-142">Partial</span><span class="sxs-lookup"><span data-stu-id="c7f04-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="c7f04-143">在 Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="c7f04-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="c7f04-144">如何：控制變數的範圍</span><span class="sxs-lookup"><span data-stu-id="c7f04-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="c7f04-145">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="c7f04-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
