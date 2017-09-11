---
title: "類型提升 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 383f4b1d29e9bbf81eee44bf78762a80aea9eb36
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="07c60-102">類型提升 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07c60-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="07c60-103">當您宣告程式設計項目在模組中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提升其範圍包含模組的命名空間。</span><span class="sxs-lookup"><span data-stu-id="07c60-103">When you declare a programming element in a module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="07c60-104">這稱為*輸入促銷*。</span><span class="sxs-lookup"><span data-stu-id="07c60-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="07c60-105">下列範例會顯示模組的基本架構定義，該模組的兩個成員。</span><span class="sxs-lookup"><span data-stu-id="07c60-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 <span data-ttu-id="07c60-106">[!code-vb[VbVbalrDeclaredElements #&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="07c60-106">[!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span></span>  
  
 <span data-ttu-id="07c60-107">內`projModule`、 程式設計在模組層級宣告的項目會提升至`projNamespace`。</span><span class="sxs-lookup"><span data-stu-id="07c60-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="07c60-108">在上述範例中，`basicEnum`和`innerClass`會升級，但`numberSub`不是，因為它不會在模組層級宣告。</span><span class="sxs-lookup"><span data-stu-id="07c60-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="07c60-109">型別提升的效果</span><span class="sxs-lookup"><span data-stu-id="07c60-109">Effect of Type Promotion</span></span>  
 <span data-ttu-id="07c60-110">型別提升的效果是限定性條件字串不需要包含模組名稱。</span><span class="sxs-lookup"><span data-stu-id="07c60-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="07c60-111">下列範例會在上述範例中的兩個呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="07c60-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 <span data-ttu-id="07c60-112">[!code-vb[VbVbalrDeclaredElements #&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="07c60-112">[!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span></span>  
  
 <span data-ttu-id="07c60-113">在上述範例中，第一次呼叫會使用完整限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="07c60-113">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="07c60-114">不過，這是不需要因為型別提升。</span><span class="sxs-lookup"><span data-stu-id="07c60-114">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="07c60-115">第二個呼叫，也存取模組成員但不包括`projModule`中限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="07c60-115">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="07c60-116">型別提升失敗</span><span class="sxs-lookup"><span data-stu-id="07c60-116">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="07c60-117">如果命名空間已經有具有相同名稱做為模組成員的成員，型別提升將無效的模組成員。</span><span class="sxs-lookup"><span data-stu-id="07c60-117">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="07c60-118">下列範例示範基本架構定義的列舉型別與相同的命名空間內的模組。</span><span class="sxs-lookup"><span data-stu-id="07c60-118">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 <span data-ttu-id="07c60-119">[!code-vb[VbVbalrDeclaredElements #&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="07c60-119">[!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span></span>  
  
 <span data-ttu-id="07c60-120">在上述範例中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法升級類別`abc`至`thisNameSpace`因為已經有具有相同名稱的命名空間層級的列舉。</span><span class="sxs-lookup"><span data-stu-id="07c60-120">In the preceding example, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="07c60-121">若要存取`abcSub`，您必須使用完整限定性條件字串`thisNamespace.thisModule.abc.abcSub`。</span><span class="sxs-lookup"><span data-stu-id="07c60-121">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="07c60-122">不過，類別`xyz`仍升級，而且您可以存取`xyzSub`使用較短的限定性條件字串`thisNamespace.xyz.xyzSub`。</span><span class="sxs-lookup"><span data-stu-id="07c60-122">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="07c60-123">部分類型的型別提升失敗</span><span class="sxs-lookup"><span data-stu-id="07c60-123">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="07c60-124">如果類別或結構，在模組內使用[部分](../../../../visual-basic/language-reference/modifiers/partial.md)關鍵字、 型別提升會自動失效該類別或結構中，命名空間是否具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="07c60-124">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="07c60-125">在模組中的其他項目是仍可進行型別提升。</span><span class="sxs-lookup"><span data-stu-id="07c60-125">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="07c60-126">**結果。**</span><span class="sxs-lookup"><span data-stu-id="07c60-126">**Consequences.**</span></span> <span data-ttu-id="07c60-127">部分定義的型別提升失敗可能會造成非預期的結果，甚至是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="07c60-127">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="07c60-128">下列範例示範基本架構的部分定義的類別，一個是在模組內。</span><span class="sxs-lookup"><span data-stu-id="07c60-128">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 <span data-ttu-id="07c60-129">[!code-vb[VbVbalrDeclaredElements #&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="07c60-129">[!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span></span>  
  
 <span data-ttu-id="07c60-130">在上述範例中，開發人員可能預期要合併兩個部分定義的編譯器`sampleClass`。</span><span class="sxs-lookup"><span data-stu-id="07c60-130">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="07c60-131">不過，編譯器不會考慮升級部分定義內`sampleModule`。</span><span class="sxs-lookup"><span data-stu-id="07c60-131">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="07c60-132">如此一來，它會嘗試編譯兩個個別且不同的類別，名為`sampleClass`但具有不同的限定性條件路徑。</span><span class="sxs-lookup"><span data-stu-id="07c60-132">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="07c60-133">只有在完整路徑相同時，編譯器才會合併部分定義。</span><span class="sxs-lookup"><span data-stu-id="07c60-133">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="07c60-134">建議</span><span class="sxs-lookup"><span data-stu-id="07c60-134">Recommendations</span></span>  
 <span data-ttu-id="07c60-135">下列建議表示良好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="07c60-135">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="07c60-136">**唯一的名稱。**</span><span class="sxs-lookup"><span data-stu-id="07c60-136">**Unique Names.**</span></span> <span data-ttu-id="07c60-137">當您的程式項目命名的完整控制權，永遠是最好各處使用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="07c60-137">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="07c60-138">相同的名稱需要額外的限定性條件，而且可以讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="07c60-138">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="07c60-139">它們也可能會導致難以察覺的錯誤和非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="07c60-139">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="07c60-140">**完整路徑名稱。**</span><span class="sxs-lookup"><span data-stu-id="07c60-140">**Full Qualification.**</span></span> <span data-ttu-id="07c60-141">當您正在使用模組和其他項目相同的命名空間中時，最安全的方法就是一律使用完整限定性條件的所有程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="07c60-141">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="07c60-142">如果型別提升將無效的模組成員，且不完整限定該成員，您可能不小心存取不同的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="07c60-142">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c60-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07c60-143">See Also</span></span>  
 <span data-ttu-id="07c60-144">[Module 陳述式](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="07c60-144">[Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="07c60-145"> [Namespace 陳述式](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="07c60-145"> [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="07c60-146"> [部分](../../../../visual-basic/language-reference/modifiers/partial.md) </span><span class="sxs-lookup"><span data-stu-id="07c60-146"> [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) </span></span>  
<span data-ttu-id="07c60-147"> [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="07c60-147"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="07c60-148"> [如何︰ 控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="07c60-148"> [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span></span>  
<span data-ttu-id="07c60-149"> [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="07c60-149"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
