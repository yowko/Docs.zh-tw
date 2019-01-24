---
title: 常數和常值資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: d85ff343587e8689a4859a09c8dc80932374a82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498644"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="6b948-102">常數和常值資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b948-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="6b948-103">常值是表示為本身，而不是為變數的值或運算式，例如數字 3 或字串"Hello"的結果值。</span><span class="sxs-lookup"><span data-stu-id="6b948-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="6b948-104">常數是有意義的名稱，會取代常值，並保留在整個程式，而不是變數，可能會變更其值，這個相同的值。</span><span class="sxs-lookup"><span data-stu-id="6b948-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="6b948-105">當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`並[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告的所有常數，與資料型別。</span><span class="sxs-lookup"><span data-stu-id="6b948-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="6b948-106">在下列範例中，資料類型`MyByte`明確宣告資料類型為`Byte`:</span><span class="sxs-lookup"><span data-stu-id="6b948-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="6b948-107">當`Option Infer`是`On`或是`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="6b948-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="6b948-108">編譯器會判斷運算式的類型從常數的類型。</span><span class="sxs-lookup"><span data-stu-id="6b948-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="6b948-109">預設會將轉換的數字的整數常值`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="6b948-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="6b948-110">預設資料類型是浮點數`Double`，和關鍵字`True`並`False`指定`Boolean`常數。</span><span class="sxs-lookup"><span data-stu-id="6b948-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="6b948-111">常值和類型強制型轉</span><span class="sxs-lookup"><span data-stu-id="6b948-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="6b948-112">在某些情況下，您可能想要的常值強制為特定的資料類型;例如，當將特別大的整數常值指派給類型的變數`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="6b948-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="6b948-113">下列範例會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="6b948-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="6b948-114">從常值的表示法會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b948-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="6b948-115">`Decimal`資料類型可以保留值，這種大小，但常值隱含地表示為`Long`，哪些不可。</span><span class="sxs-lookup"><span data-stu-id="6b948-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="6b948-116">您可以將兩種方式為特定的資料類型的常值的強制轉型： 將型別字元附加到它，或將其放在封入字元。</span><span class="sxs-lookup"><span data-stu-id="6b948-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="6b948-117">類型字元或封入字元必須立即在之前和/或遵循常值，不含空格或任何種類的字元。</span><span class="sxs-lookup"><span data-stu-id="6b948-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="6b948-118">若要讓上述範例運作，您可以將附加`D`型別字元常值，這會導致它表示成`Decimal`:</span><span class="sxs-lookup"><span data-stu-id="6b948-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="6b948-119">下列範例會示範正確的使用方式的型別字元及封入字元：</span><span class="sxs-lookup"><span data-stu-id="6b948-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="6b948-120">下表顯示封入字元和 Visual Basic 提供的類型字元。</span><span class="sxs-lookup"><span data-stu-id="6b948-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="6b948-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="6b948-121">Data type</span></span>|<span data-ttu-id="6b948-122">封入字元</span><span class="sxs-lookup"><span data-stu-id="6b948-122">Enclosing character</span></span>|<span data-ttu-id="6b948-123">附加的類型字元</span><span class="sxs-lookup"><span data-stu-id="6b948-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="6b948-124">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-124">(none)</span></span>|<span data-ttu-id="6b948-125">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="6b948-126">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-126">(none)</span></span>|<span data-ttu-id="6b948-127">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="6b948-128">"</span><span class="sxs-lookup"><span data-stu-id="6b948-128">"</span></span>|<span data-ttu-id="6b948-129">C</span><span class="sxs-lookup"><span data-stu-id="6b948-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="6b948-130">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="6b948-131">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-131">(none)</span></span>|<span data-ttu-id="6b948-132">D 或使用 @</span><span class="sxs-lookup"><span data-stu-id="6b948-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="6b948-133">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-133">(none)</span></span>|<span data-ttu-id="6b948-134">R 或 #</span><span class="sxs-lookup"><span data-stu-id="6b948-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="6b948-135">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-135">(none)</span></span>|<span data-ttu-id="6b948-136">I 或 %</span><span class="sxs-lookup"><span data-stu-id="6b948-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="6b948-137">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-137">(none)</span></span>|<span data-ttu-id="6b948-138">L 或 （& s)</span><span class="sxs-lookup"><span data-stu-id="6b948-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="6b948-139">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-139">(none)</span></span>|<span data-ttu-id="6b948-140">S</span><span class="sxs-lookup"><span data-stu-id="6b948-140">S</span></span>|  
|`Single`|<span data-ttu-id="6b948-141">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-141">(none)</span></span>|<span data-ttu-id="6b948-142">F 或 ！</span><span class="sxs-lookup"><span data-stu-id="6b948-142">F or !</span></span>|  
|`String`|<span data-ttu-id="6b948-143">"</span><span class="sxs-lookup"><span data-stu-id="6b948-143">"</span></span>|<span data-ttu-id="6b948-144">(無)</span><span class="sxs-lookup"><span data-stu-id="6b948-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b948-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b948-145">See also</span></span>
- [<span data-ttu-id="6b948-146">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="6b948-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [<span data-ttu-id="6b948-147">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="6b948-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [<span data-ttu-id="6b948-148">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="6b948-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="6b948-149">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b948-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="6b948-150">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b948-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="6b948-151">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="6b948-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="6b948-152">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="6b948-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="6b948-153">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="6b948-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="6b948-154">資料類型</span><span class="sxs-lookup"><span data-stu-id="6b948-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6b948-155">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="6b948-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
