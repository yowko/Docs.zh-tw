---
title: "使用者定義常數 (Visual Basic) |Microsoft 文件"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
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
ms.openlocfilehash: b1ab1501309823b1565d5198fff25edf2927a2ce
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="0459c-102">使用者定義常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0459c-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="0459c-103">常數是有意義的名稱來取代數字或字串，不會變更。</span><span class="sxs-lookup"><span data-stu-id="0459c-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="0459c-104">常數用來儲存，正如其名，保持不變的應用程式執行過程中的值。</span><span class="sxs-lookup"><span data-stu-id="0459c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="0459c-105">您可以使用常數所定義的控制項或元件，或建立您自己。</span><span class="sxs-lookup"><span data-stu-id="0459c-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="0459c-106">您建立自己的常數之所以被形容為*使用者定義*。</span><span class="sxs-lookup"><span data-stu-id="0459c-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="0459c-107">您可使用宣告常數`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0459c-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="0459c-108">如果`Option Strict`是`On`，您必須明確宣告常數的類型。</span><span class="sxs-lookup"><span data-stu-id="0459c-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="0459c-109">Const 陳述式的使用方式</span><span class="sxs-lookup"><span data-stu-id="0459c-109">Const Statement Usage</span></span>  
 <span data-ttu-id="0459c-110">A`Const`陳述式可以代表數學或日期/時間數量︰</span><span class="sxs-lookup"><span data-stu-id="0459c-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 <span data-ttu-id="0459c-111">[!code-vb[VbEnumsTask #&10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0459c-111">[!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span></span>  
  
 <span data-ttu-id="0459c-112">它也可以定義`String`常數︰</span><span class="sxs-lookup"><span data-stu-id="0459c-112">It also can define `String` constants:</span></span>  
  
 <span data-ttu-id="0459c-113">[!code-vb[VbEnumsTask #&13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0459c-113">[!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span></span>  
  
 <span data-ttu-id="0459c-114">等號右邊的運算式 ( `=` ) 通常是一個數字或常值字串，但也可以是 （雖然運算式無法包含函式呼叫） 會導致數字或字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="0459c-114">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="0459c-115">您甚至可以定義常數，依據先前定義的常數︰</span><span class="sxs-lookup"><span data-stu-id="0459c-115">You can even define constants in terms of previously defined constants:</span></span>  
  
 <span data-ttu-id="0459c-116">[!code-vb[VbEnumsTask #&15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0459c-116">[!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span></span>  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="0459c-117">使用者定義常數的範圍</span><span class="sxs-lookup"><span data-stu-id="0459c-117">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="0459c-118">A`Const`陳述式的範圍是在相同的位置所宣告的變數相同。</span><span class="sxs-lookup"><span data-stu-id="0459c-118">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="0459c-119">您可以下列方式指定範圍︰</span><span class="sxs-lookup"><span data-stu-id="0459c-119">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="0459c-120">若要建立程序中只存在一個常數，請在該程序內宣告。</span><span class="sxs-lookup"><span data-stu-id="0459c-120">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="0459c-121">若要建立所有的程序，在類別中，但不是屬於該模組之外的任何程式碼可以使用的常數，請在類別宣告區段中宣告。</span><span class="sxs-lookup"><span data-stu-id="0459c-121">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="0459c-122">若要建立外部用戶端組件的所有成員的組件，但不是使用的常數，宣告使用`Friend`類別的宣告區段中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0459c-122">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="0459c-123">若要建立整個應用程式可以使用的常數，宣告使用`Public`關鍵字的宣告區段的類別。</span><span class="sxs-lookup"><span data-stu-id="0459c-123">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="0459c-124">如需詳細資訊，請參閱[如何︰ 宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。</span><span class="sxs-lookup"><span data-stu-id="0459c-124">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="0459c-125">避免循環參考</span><span class="sxs-lookup"><span data-stu-id="0459c-125">Avoiding Circular References</span></span>  
 <span data-ttu-id="0459c-126">因為可以根據其他常數定義常數，所以有可能會不小心建立*循環*，或兩個或多個常數之間的循環參考。</span><span class="sxs-lookup"><span data-stu-id="0459c-126">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="0459c-127">當您有兩個或多個公用常數，每一個都根據另一個，如下列範例所示定義時，就會發生循環︰</span><span class="sxs-lookup"><span data-stu-id="0459c-127">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 <span data-ttu-id="0459c-128">[!code-vb[VbEnumsTask #&16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0459c-128">[!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span></span>  
<span data-ttu-id="0459c-129">[!code-vb[VbEnumsTask #&17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="0459c-129">[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span></span>  
  
 <span data-ttu-id="0459c-130">如果發生循環，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0459c-130">If a cycle occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0459c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0459c-131">See Also</span></span>  
 <span data-ttu-id="0459c-132">[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-132">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="0459c-133"> [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-133"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="0459c-134"> [常數和列舉型別](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-134"> [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span></span>  
<span data-ttu-id="0459c-135"> [常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-135"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="0459c-136"> [列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-136"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="0459c-137"> [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-137"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="0459c-138"> [如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-138"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="0459c-139"> [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="0459c-139"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="0459c-140"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0459c-140"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
