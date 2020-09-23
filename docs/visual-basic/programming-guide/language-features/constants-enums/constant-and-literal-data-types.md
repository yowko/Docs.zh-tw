---
title: 常數和常值資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 03d693653cd166bbf1096031f1a864b492e2e896
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086292"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="f1f00-102">常數和常值資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1f00-102">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="f1f00-103">常值是表示為本身的值，而不是變數的值或運算式的結果（例如數位3或字串 "Hello"）。</span><span class="sxs-lookup"><span data-stu-id="f1f00-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="f1f00-104">常數是有意義的名稱，它會取代常值，並在整個程式中保留這個相同的值，而不是變數，其值可能會變更。</span><span class="sxs-lookup"><span data-stu-id="f1f00-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="f1f00-105">當 [Option 推斷](../../../language-reference/statements/option-infer-statement.md) 為 `Off` ，且 [option Strict](../../../language-reference/statements/option-strict-statement.md) 為時 `On` ，您必須明確地宣告具有資料類型的所有常數。</span><span class="sxs-lookup"><span data-stu-id="f1f00-105">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="f1f00-106">在下列範例中，的資料型別 `MyByte` 會明確宣告為資料類型 `Byte` ：</span><span class="sxs-lookup"><span data-stu-id="f1f00-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="f1f00-107">當 `Option Infer` 是 `On` 或 `Option Strict` 時 `Off` ，您可以宣告常數，而不需要使用子句來指定資料類型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="f1f00-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="f1f00-108">編譯器會從運算式的型別判斷常數的型別。</span><span class="sxs-lookup"><span data-stu-id="f1f00-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="f1f00-109">依預設，數值整數常值會轉換成 `Integer` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="f1f00-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="f1f00-110">浮點數的預設資料類型是 `Double` ，以及關鍵字 `True` 和 `False` 指定 `Boolean` 常數。</span><span class="sxs-lookup"><span data-stu-id="f1f00-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="f1f00-111">常值和類型強制型轉</span><span class="sxs-lookup"><span data-stu-id="f1f00-111">Literals and Type Coercion</span></span>  

 <span data-ttu-id="f1f00-112">在某些情況下，您可能會想要強制常值成為特定的資料類型;例如，將特別大的整數常值指派給類型的變數時 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="f1f00-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="f1f00-113">下列範例會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="f1f00-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="f1f00-114">來自常值表示的錯誤結果。</span><span class="sxs-lookup"><span data-stu-id="f1f00-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="f1f00-115">`Decimal`資料類型可以保留這個很大的值，但是常值會以隱含的方式表示，而無法這麼做 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="f1f00-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="f1f00-116">您可以透過兩種方式將常值強制轉換成特定的資料類型：將類型字元附加至其中，或將它放在封入字元內。</span><span class="sxs-lookup"><span data-stu-id="f1f00-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="f1f00-117">類型字元或封入字元必須緊接在常值前面和/或後面，不含任何種類的中間空格或字元。</span><span class="sxs-lookup"><span data-stu-id="f1f00-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="f1f00-118">若要讓先前的範例正常運作，您可以將 `D` 類型字元附加到常值，這會使其表示為 `Decimal` ：</span><span class="sxs-lookup"><span data-stu-id="f1f00-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f1f00-119">下列範例示範類型字元和封入字元的正確用法：</span><span class="sxs-lookup"><span data-stu-id="f1f00-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f1f00-120">下表顯示 Visual Basic 中可用的封入字元和類型字元。</span><span class="sxs-lookup"><span data-stu-id="f1f00-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="f1f00-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="f1f00-121">Data type</span></span>|<span data-ttu-id="f1f00-122">封入字元</span><span class="sxs-lookup"><span data-stu-id="f1f00-122">Enclosing character</span></span>|<span data-ttu-id="f1f00-123">附加的類型字元</span><span class="sxs-lookup"><span data-stu-id="f1f00-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="f1f00-124">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-124">(none)</span></span>|<span data-ttu-id="f1f00-125">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="f1f00-126">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-126">(none)</span></span>|<span data-ttu-id="f1f00-127">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="f1f00-128">"</span><span class="sxs-lookup"><span data-stu-id="f1f00-128">"</span></span>|<span data-ttu-id="f1f00-129">C</span><span class="sxs-lookup"><span data-stu-id="f1f00-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="f1f00-130">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="f1f00-131">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-131">(none)</span></span>|<span data-ttu-id="f1f00-132">D 或@</span><span class="sxs-lookup"><span data-stu-id="f1f00-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="f1f00-133">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-133">(none)</span></span>|<span data-ttu-id="f1f00-134">R 或#</span><span class="sxs-lookup"><span data-stu-id="f1f00-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="f1f00-135">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-135">(none)</span></span>|<span data-ttu-id="f1f00-136">I 或%</span><span class="sxs-lookup"><span data-stu-id="f1f00-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="f1f00-137">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-137">(none)</span></span>|<span data-ttu-id="f1f00-138">L 或 &</span><span class="sxs-lookup"><span data-stu-id="f1f00-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="f1f00-139">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-139">(none)</span></span>|<span data-ttu-id="f1f00-140">S</span><span class="sxs-lookup"><span data-stu-id="f1f00-140">S</span></span>|  
|`Single`|<span data-ttu-id="f1f00-141">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-141">(none)</span></span>|<span data-ttu-id="f1f00-142">F 或！</span><span class="sxs-lookup"><span data-stu-id="f1f00-142">F or !</span></span>|  
|`String`|<span data-ttu-id="f1f00-143">"</span><span class="sxs-lookup"><span data-stu-id="f1f00-143">"</span></span>|<span data-ttu-id="f1f00-144">(無)</span><span class="sxs-lookup"><span data-stu-id="f1f00-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1f00-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1f00-145">See also</span></span>

- [<span data-ttu-id="f1f00-146">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="f1f00-146">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="f1f00-147">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="f1f00-147">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="f1f00-148">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="f1f00-148">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="f1f00-149">Long</span><span class="sxs-lookup"><span data-stu-id="f1f00-149">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f1f00-150">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="f1f00-150">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="f1f00-151">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="f1f00-151">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="f1f00-152">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="f1f00-152">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="f1f00-153">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="f1f00-153">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="f1f00-154">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="f1f00-154">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="f1f00-155">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="f1f00-155">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
