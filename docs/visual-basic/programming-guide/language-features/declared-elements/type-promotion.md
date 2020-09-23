---
title: 類型提升
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 6c28ca22e96616ff09e147400bfdb2adb922ff0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085798"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="ab70b-102">類型提升 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab70b-102">Type Promotion (Visual Basic)</span></span>

<span data-ttu-id="ab70b-103">當您在模組中宣告程式設計專案時，Visual Basic 會將其範圍升級為包含模組的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab70b-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="ab70b-104">這就是所謂的 *型別提升*。</span><span class="sxs-lookup"><span data-stu-id="ab70b-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="ab70b-105">下列範例顯示模組的基本架構定義，以及該模組的兩個成員。</span><span class="sxs-lookup"><span data-stu-id="ab70b-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="ab70b-106">在中 `projModule` ，在模組層級宣告的程式設計專案會升級為 `projNamespace` 。</span><span class="sxs-lookup"><span data-stu-id="ab70b-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="ab70b-107">在上述範例中， `basicEnum` 和 `innerClass` 會升級，但不是 `numberSub` ，因為它不是在模組層級宣告。</span><span class="sxs-lookup"><span data-stu-id="ab70b-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="ab70b-108">型別提升的效果</span><span class="sxs-lookup"><span data-stu-id="ab70b-108">Effect of Type Promotion</span></span>  

 <span data-ttu-id="ab70b-109">型別提升的影響是，限定性字串不需要包含模組名稱。</span><span class="sxs-lookup"><span data-stu-id="ab70b-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="ab70b-110">下列範例會對上述範例中的程式進行兩次呼叫。</span><span class="sxs-lookup"><span data-stu-id="ab70b-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ab70b-111">在上述範例中，第一個呼叫會使用完整的限定字串。</span><span class="sxs-lookup"><span data-stu-id="ab70b-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="ab70b-112">不過，這並不是必要的，因為升級型別。</span><span class="sxs-lookup"><span data-stu-id="ab70b-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="ab70b-113">第二個呼叫也會存取模組的成員，而不包含 `projModule` 在限定性字串中。</span><span class="sxs-lookup"><span data-stu-id="ab70b-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="ab70b-114">型別提升的擊敗</span><span class="sxs-lookup"><span data-stu-id="ab70b-114">Defeat of Type Promotion</span></span>  

 <span data-ttu-id="ab70b-115">如果命名空間已經有與模組成員同名的成員，則該模組成員的型別提升會失效。</span><span class="sxs-lookup"><span data-stu-id="ab70b-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="ab70b-116">下列範例顯示列舉的基本架構定義和相同命名空間中的模組。</span><span class="sxs-lookup"><span data-stu-id="ab70b-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="ab70b-117">在上述範例中，Visual Basic 無法將類別升級 `abc` 為， `thisNameSpace` 因為在命名空間層級已經有相同名稱的列舉。</span><span class="sxs-lookup"><span data-stu-id="ab70b-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="ab70b-118">若要存取 `abcSub` ，您必須使用完整的限定性字串 `thisNamespace.thisModule.abc.abcSub` 。</span><span class="sxs-lookup"><span data-stu-id="ab70b-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="ab70b-119">不過，類別 `xyz` 仍會升級，而且您可以 `xyzSub` 使用較短的限定性字串來存取 `thisNamespace.xyz.xyzSub` 。</span><span class="sxs-lookup"><span data-stu-id="ab70b-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="ab70b-120">部分類型的型別提升的擊敗</span><span class="sxs-lookup"><span data-stu-id="ab70b-120">Defeat of Type Promotion for Partial Types</span></span>  

 <span data-ttu-id="ab70b-121">如果模組內的類別或結構使用 [Partial](../../../language-reference/modifiers/partial.md) 關鍵字，則不論命名空間是否有相同名稱的成員，類別或結構的型別提升都會自動失效。</span><span class="sxs-lookup"><span data-stu-id="ab70b-121">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="ab70b-122">模組中的其他元素仍然符合類型升級的資格。</span><span class="sxs-lookup"><span data-stu-id="ab70b-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="ab70b-123">**後果。**</span><span class="sxs-lookup"><span data-stu-id="ab70b-123">**Consequences.**</span></span> <span data-ttu-id="ab70b-124">部分定義的型別提升的破壞可能會導致非預期的結果，甚至是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab70b-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="ab70b-125">下列範例顯示類別的基本架構部分定義，其中之一是在模組中。</span><span class="sxs-lookup"><span data-stu-id="ab70b-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ab70b-126">在上述範例中，開發人員可能會預期編譯器會合並的兩個部分定義 `sampleClass` 。</span><span class="sxs-lookup"><span data-stu-id="ab70b-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="ab70b-127">不過，編譯器並不會考慮升級內部的部分定義 `sampleModule` 。</span><span class="sxs-lookup"><span data-stu-id="ab70b-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="ab70b-128">如此一來，它會嘗試編譯兩個不同的不同類別，這兩個類別都命名為 `sampleClass` 但使用不同的限定路徑。</span><span class="sxs-lookup"><span data-stu-id="ab70b-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="ab70b-129">只有在完整路徑相同時，編譯器才會合併部分定義。</span><span class="sxs-lookup"><span data-stu-id="ab70b-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="ab70b-130">建議</span><span class="sxs-lookup"><span data-stu-id="ab70b-130">Recommendations</span></span>  

 <span data-ttu-id="ab70b-131">下列建議代表良好的程式設計作法。</span><span class="sxs-lookup"><span data-stu-id="ab70b-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="ab70b-132">**唯一的名稱。**</span><span class="sxs-lookup"><span data-stu-id="ab70b-132">**Unique Names.**</span></span> <span data-ttu-id="ab70b-133">當您完全掌控程式設計項目的命名時，在任何地方都可以使用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab70b-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="ab70b-134">相同的名稱需要額外的限定性，而且可能會讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="ab70b-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="ab70b-135">它們也可能導致微妙的錯誤和非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="ab70b-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="ab70b-136">**完整限定。**</span><span class="sxs-lookup"><span data-stu-id="ab70b-136">**Full Qualification.**</span></span> <span data-ttu-id="ab70b-137">當您使用相同命名空間中的模組和其他專案時，最安全的方法是一律針對所有程式設計專案使用完整限定。</span><span class="sxs-lookup"><span data-stu-id="ab70b-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="ab70b-138">如果模組成員的型別提升無法通過，而且您未完全符合該成員，您可能會不慎存取不同的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ab70b-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab70b-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab70b-139">See also</span></span>

- [<span data-ttu-id="ab70b-140">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab70b-140">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="ab70b-141">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab70b-141">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="ab70b-142">Partial</span><span class="sxs-lookup"><span data-stu-id="ab70b-142">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="ab70b-143">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="ab70b-143">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="ab70b-144">如何：控制變數的範圍</span><span class="sxs-lookup"><span data-stu-id="ab70b-144">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="ab70b-145">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="ab70b-145">References to Declared Elements</span></span>](references-to-declared-elements.md)
