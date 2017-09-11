---
title: "常數和常值資料類型 (Visual Basic) |Microsoft 文件"
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
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
ms.openlocfilehash: 29a997ee0dd847e8505d1a5c24cacfdfdb0a42cc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="714d4-102">常數和常值資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="714d4-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="714d4-103">常值是其本身，而不是變數的值或運算式，例如數字 3 或字串"Hello"的結果表示的值。</span><span class="sxs-lookup"><span data-stu-id="714d4-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="714d4-104">常數是有意義的名稱會採用取代常值，並維持相同的值在整個程式，而不是變數，其值可能會變更。</span><span class="sxs-lookup"><span data-stu-id="714d4-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="714d4-105">當[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)是`Off`和[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是`On`，您必須明確宣告的所有常數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="714d4-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="714d4-106">在下列範例中，資料類型的`MyByte`明確宣告資料型別為`Byte`:</span><span class="sxs-lookup"><span data-stu-id="714d4-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 <span data-ttu-id="714d4-107">[!code-vb[VbVbalrConstants #&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="714d4-107">[!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="714d4-108">當`Option Infer`是`On`或`Option Strict`是`Off`，您可以宣告但未指定的資料類型的常數`As`子句。</span><span class="sxs-lookup"><span data-stu-id="714d4-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="714d4-109">編譯器會判斷運算式的型別常數的類型。</span><span class="sxs-lookup"><span data-stu-id="714d4-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="714d4-110">預設會將數字的整數常值轉換`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="714d4-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="714d4-111">預設資料類型為浮點數`Double`，和關鍵字`True`和`False`指定`Boolean`常數。</span><span class="sxs-lookup"><span data-stu-id="714d4-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="714d4-112">常值和強制型轉</span><span class="sxs-lookup"><span data-stu-id="714d4-112">Literals and Type Coercion</span></span>  
 <span data-ttu-id="714d4-113">在某些情況下，您可能想要的常值強制為特定的資料類型;例如，將特別大的整數常值指派給類型的變數時`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="714d4-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="714d4-114">下列範例會產生錯誤︰</span><span class="sxs-lookup"><span data-stu-id="714d4-114">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="714d4-115">常值的表示方式會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="714d4-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="714d4-116">`Decimal`資料類型可以保留值，這種大小，但常值會隱含地表示為`Long`，哪些不可。</span><span class="sxs-lookup"><span data-stu-id="714d4-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="714d4-117">您可以強制轉型成特定的資料類型有兩種常值︰ 將型別字元附加到它，或將其放在封入字元。</span><span class="sxs-lookup"><span data-stu-id="714d4-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="714d4-118">型別字元或封入字元必須立即之前和/或遵循常值，沒有多餘的空格或任何種類的字元。</span><span class="sxs-lookup"><span data-stu-id="714d4-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="714d4-119">若要使先前的範例工作，您可以附加`D`輸入字元常值，使它表示成`Decimal`:</span><span class="sxs-lookup"><span data-stu-id="714d4-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 <span data-ttu-id="714d4-120">[!code-vb[VbVbalrConstants #&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="714d4-120">[!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="714d4-121">下列範例示範正確的型別字元和封入字元使用方式︰</span><span class="sxs-lookup"><span data-stu-id="714d4-121">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 <span data-ttu-id="714d4-122">[!code-vb[VbVbalrConstants #&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="714d4-122">[!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span></span>  
  
 <span data-ttu-id="714d4-123">下表顯示內含的字元和型別字元用於[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="714d4-123">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|<span data-ttu-id="714d4-124">資料類型</span><span class="sxs-lookup"><span data-stu-id="714d4-124">Data type</span></span>|<span data-ttu-id="714d4-125">封入字元</span><span class="sxs-lookup"><span data-stu-id="714d4-125">Enclosing character</span></span>|<span data-ttu-id="714d4-126">附加的型別字元</span><span class="sxs-lookup"><span data-stu-id="714d4-126">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="714d4-127">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-127">(none)</span></span>|<span data-ttu-id="714d4-128">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-128">(none)</span></span>|  
|`Byte`|<span data-ttu-id="714d4-129">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-129">(none)</span></span>|<span data-ttu-id="714d4-130">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-130">(none)</span></span>|  
|`Char`|<span data-ttu-id="714d4-131">"</span><span class="sxs-lookup"><span data-stu-id="714d4-131">"</span></span>|<span data-ttu-id="714d4-132">C</span><span class="sxs-lookup"><span data-stu-id="714d4-132">C</span></span>|  
|`Date`|#|<span data-ttu-id="714d4-133">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-133">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="714d4-134">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-134">(none)</span></span>|<span data-ttu-id="714d4-135">D 或 @</span><span class="sxs-lookup"><span data-stu-id="714d4-135">D or @</span></span>|  
|`Double`|<span data-ttu-id="714d4-136">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-136">(none)</span></span>|<span data-ttu-id="714d4-137">R 或</span><span class="sxs-lookup"><span data-stu-id="714d4-137">R or</span></span> #|  
|`Integer`|<span data-ttu-id="714d4-138">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-138">(none)</span></span>|<span data-ttu-id="714d4-139">I 或 %</span><span class="sxs-lookup"><span data-stu-id="714d4-139">I or %</span></span>|  
|`Long`|<span data-ttu-id="714d4-140">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-140">(none)</span></span>|<span data-ttu-id="714d4-141">L 或 i</span><span class="sxs-lookup"><span data-stu-id="714d4-141">L or &</span></span>|  
|`Short`|<span data-ttu-id="714d4-142">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-142">(none)</span></span>|<span data-ttu-id="714d4-143">S</span><span class="sxs-lookup"><span data-stu-id="714d4-143">S</span></span>|  
|`Single`|<span data-ttu-id="714d4-144">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-144">(none)</span></span>|<span data-ttu-id="714d4-145">F 或 ！</span><span class="sxs-lookup"><span data-stu-id="714d4-145">F or !</span></span>|  
|`String`|<span data-ttu-id="714d4-146">"</span><span class="sxs-lookup"><span data-stu-id="714d4-146">"</span></span>|<span data-ttu-id="714d4-147">(無)</span><span class="sxs-lookup"><span data-stu-id="714d4-147">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="714d4-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="714d4-148">See Also</span></span>  
 <span data-ttu-id="714d4-149">[使用者定義常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-149">[User-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span></span>  
<span data-ttu-id="714d4-150"> [如何︰ 宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-150"> [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span></span>  
<span data-ttu-id="714d4-151"> [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-151"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="714d4-152"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-152"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="714d4-153"> [Option Explicit 陳述式](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-153"> [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="714d4-154"> [列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-154"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="714d4-155"> [如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-155"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="714d4-156"> [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-156"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="714d4-157"> [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="714d4-157"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="714d4-158"> [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="714d4-158"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
