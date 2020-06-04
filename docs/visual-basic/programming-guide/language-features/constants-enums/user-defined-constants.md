---
title: 使用者定義的常數
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 14f3de39eb8d8e6820e2b40792a8e8e57217e410
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414372"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="18915-102">使用者定義常數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18915-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="18915-103">常數是有意義的名稱，用來取代不會變更的數位或字串。</span><span class="sxs-lookup"><span data-stu-id="18915-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="18915-104">如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。</span><span class="sxs-lookup"><span data-stu-id="18915-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="18915-105">您可以使用您所使用之控制項或元件所定義的常數，也可以自行建立。</span><span class="sxs-lookup"><span data-stu-id="18915-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="18915-106">您自行建立的常數會描述為*使用者定義*。</span><span class="sxs-lookup"><span data-stu-id="18915-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="18915-107">您可以 `Const` 使用語句來宣告常數，方法與建立變數名稱的方針相同。</span><span class="sxs-lookup"><span data-stu-id="18915-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="18915-108">如果 `Option Strict` 為 `On` ，則您必須明確宣告常數類型。</span><span class="sxs-lookup"><span data-stu-id="18915-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="18915-109">Const 語句使用方式</span><span class="sxs-lookup"><span data-stu-id="18915-109">Const Statement Usage</span></span>  
 <span data-ttu-id="18915-110">`Const`語句可以代表數學或日期/時間數量：</span><span class="sxs-lookup"><span data-stu-id="18915-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="18915-111">它也可以定義 `String` 常數：</span><span class="sxs-lookup"><span data-stu-id="18915-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="18915-112">等號（）右邊的運算式 `=` 通常是數位或常值字串，但也可以是產生數位或字串的運算式（雖然該運算式不能包含函數的呼叫）。</span><span class="sxs-lookup"><span data-stu-id="18915-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="18915-113">您甚至可以根據先前定義的常數來定義常數：</span><span class="sxs-lookup"><span data-stu-id="18915-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="18915-114">使用者定義常數的範圍</span><span class="sxs-lookup"><span data-stu-id="18915-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="18915-115">`Const`語句的範圍與在相同位置中宣告的變數相同。</span><span class="sxs-lookup"><span data-stu-id="18915-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="18915-116">您可以用下列任一種方式指定範圍：</span><span class="sxs-lookup"><span data-stu-id="18915-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="18915-117">若要建立只存在於程式中的常數，請在該程式內宣告它。</span><span class="sxs-lookup"><span data-stu-id="18915-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="18915-118">若要建立一個常數供類別內的所有程式使用，但不能用於該模組外的任何程式碼，請在類別的宣告區段中宣告它。</span><span class="sxs-lookup"><span data-stu-id="18915-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="18915-119">若要建立可用於元件的所有成員，但不是元件外部用戶端的常數，請 `Friend` 在類別的宣告區段中使用關鍵字來宣告。</span><span class="sxs-lookup"><span data-stu-id="18915-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="18915-120">若要在整個應用程式中建立常數，請 `Public` 在類別的宣告區段中使用關鍵字進行宣告。</span><span class="sxs-lookup"><span data-stu-id="18915-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="18915-121">如需詳細資訊，請參閱 how [to： Declare A 常數](how-to-declare-a-constant.md)。</span><span class="sxs-lookup"><span data-stu-id="18915-121">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="18915-122">避免迴圈參考</span><span class="sxs-lookup"><span data-stu-id="18915-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="18915-123">因為常數可以根據其他常數來定義，所以在兩個或多個常數之間，可能會不小心建立*迴圈*或迴圈參考。</span><span class="sxs-lookup"><span data-stu-id="18915-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="18915-124">當您有兩個或多個公用常數時，就會發生迴圈，其中每一個都是以另一個的角度定義，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="18915-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="18915-125">如果發生迴圈，Visual Basic 會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="18915-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18915-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18915-126">See also</span></span>

- [<span data-ttu-id="18915-127">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="18915-127">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="18915-128">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="18915-128">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="18915-129">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="18915-129">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="18915-130">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="18915-130">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="18915-131">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="18915-131">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="18915-132">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="18915-132">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="18915-133">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="18915-133">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="18915-134">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="18915-134">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="18915-135">Long</span><span class="sxs-lookup"><span data-stu-id="18915-135">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
