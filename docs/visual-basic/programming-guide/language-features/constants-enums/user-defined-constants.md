---
title: 使用者定義常數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: f0196457235ad77df545a367573f62b43209269d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813908"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="b7a78-102">使用者定義常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7a78-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="b7a78-103">常數是有意義的名稱來取代數字或字串，不會變更。</span><span class="sxs-lookup"><span data-stu-id="b7a78-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="b7a78-104">如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="b7a78-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="b7a78-105">您可以使用常數所定義的控制項或元件使用，或建立您自己。</span><span class="sxs-lookup"><span data-stu-id="b7a78-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="b7a78-106">您可以建立自己的常數會被稱為*使用者定義*。</span><span class="sxs-lookup"><span data-stu-id="b7a78-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="b7a78-107">您可使用宣告常數`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7a78-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="b7a78-108">如果`Option Strict`是`On`，您必須明確宣告常數的類型。</span><span class="sxs-lookup"><span data-stu-id="b7a78-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="b7a78-109">Const 陳述式使用方式</span><span class="sxs-lookup"><span data-stu-id="b7a78-109">Const Statement Usage</span></span>  
 <span data-ttu-id="b7a78-110">A`Const`陳述式可以代表數學或日期/時間數量：</span><span class="sxs-lookup"><span data-stu-id="b7a78-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="b7a78-111">它也可以定義`String`常數：</span><span class="sxs-lookup"><span data-stu-id="b7a78-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="b7a78-112">等號右邊的運算式 ( `=` ) 通常是數字或常值字串，但它也可以是運算式所產生的數字或字串中 （雖然該運算式無法包含函式的呼叫）。</span><span class="sxs-lookup"><span data-stu-id="b7a78-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="b7a78-113">您甚至可以定義常數，根據先前定義的常數：</span><span class="sxs-lookup"><span data-stu-id="b7a78-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="b7a78-114">使用者定義的常數的範圍</span><span class="sxs-lookup"><span data-stu-id="b7a78-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="b7a78-115">A`Const`陳述式的範圍是在相同的位置所宣告的變數相同。</span><span class="sxs-lookup"><span data-stu-id="b7a78-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="b7a78-116">您可以使用下列任一方式來指定範圍：</span><span class="sxs-lookup"><span data-stu-id="b7a78-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="b7a78-117">若要建立程序內只能存在一個常數，請將它宣告內該程序。</span><span class="sxs-lookup"><span data-stu-id="b7a78-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="b7a78-118">若要建立所有的程序，在類別中，但不是屬於該模組外的任何程式碼可以使用的常數，請將它宣告之類別的宣告區段中。</span><span class="sxs-lookup"><span data-stu-id="b7a78-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="b7a78-119">若要建立外部的用戶端組件的所有成員的組件，但不是使用的常數，宣告使用`Friend`類別的 「 宣告 」 區段中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b7a78-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="b7a78-120">若要建立整個應用程式，您可以使用的常數，宣告使用`Public`關鍵字在宣告中的區段的類別。</span><span class="sxs-lookup"><span data-stu-id="b7a78-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="b7a78-121">如需詳細資訊，請參閱[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。</span><span class="sxs-lookup"><span data-stu-id="b7a78-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="b7a78-122">避免循環參考</span><span class="sxs-lookup"><span data-stu-id="b7a78-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="b7a78-123">根據其他常數，就可以定義常數，因為很可能會不小心建立*循環*，或兩個或多個常數之間的循環參考。</span><span class="sxs-lookup"><span data-stu-id="b7a78-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="b7a78-124">當您有兩個或多個公用常數，每一個都以另一個，如下列範例所示定義時，就會發生循環：</span><span class="sxs-lookup"><span data-stu-id="b7a78-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="b7a78-125">如果發生循環，Visual Basic 會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7a78-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a78-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7a78-126">See also</span></span>

- [<span data-ttu-id="b7a78-127">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="b7a78-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="b7a78-128">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="b7a78-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="b7a78-129">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="b7a78-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="b7a78-130">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="b7a78-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="b7a78-131">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="b7a78-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="b7a78-132">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="b7a78-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="b7a78-133">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="b7a78-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="b7a78-134">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="b7a78-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="b7a78-135">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="b7a78-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
