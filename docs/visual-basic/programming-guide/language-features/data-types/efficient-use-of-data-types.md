---
title: 有效率地使用資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="f7a0c-102">有效率地使用資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7a0c-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="f7a0c-103">指派給未宣告的變數和變數宣告為不具有資料類型的`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="f7a0c-104">這樣可以輕鬆撰寫程式快速，但是它可能會使程式執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="f7a0c-105">強型別</span><span class="sxs-lookup"><span data-stu-id="f7a0c-105">Strong Typing</span></span>  
 <span data-ttu-id="f7a0c-106">指定所有變數的資料型別稱為*強型別*。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="f7a0c-107">使用強型別有多項優點：</span><span class="sxs-lookup"><span data-stu-id="f7a0c-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="f7a0c-108">它可讓您的變數的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="f7a0c-109">這可讓您查看其屬性和其他成員，當您輸入程式碼中。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="f7a0c-110">它會利用的編譯器型別檢查。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="f7a0c-111">這會攔截可能會在執行階段因為例如溢位錯誤而失敗的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="f7a0c-112">它也會對方法的呼叫攔截不支援它們的物件。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="f7a0c-113">這樣可以更快地執行您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="f7a0c-114">最有效率的資料類型</span><span class="sxs-lookup"><span data-stu-id="f7a0c-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="f7a0c-115">對於絕對不能包含分數的變數，整數類資料類型會更有效率的非整數類型。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="f7a0c-116">在 Visual Basic 中`Integer`和`UInteger`是最有效率的數字類型。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="f7a0c-117">小數點的數字，如`Double`是最有效率的資料類型，因為在目前的平台上的處理器執行雙精度浮點數運算。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="f7a0c-118">不過，作業`Double`速度與整數類資料類型，例如`Integer`。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="f7a0c-119">指定資料類型</span><span class="sxs-lookup"><span data-stu-id="f7a0c-119">Specifying Data Type</span></span>  
 <span data-ttu-id="f7a0c-120">使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告特定類型的變數。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="f7a0c-121">您可以使用，以同時指定其存取層級[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，如下所示下列範例。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="f7a0c-122">字元轉換</span><span class="sxs-lookup"><span data-stu-id="f7a0c-122">Character Conversion</span></span>  
 <span data-ttu-id="f7a0c-123">`AscW`和`ChrW`函式會以 Unicode 作業。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="f7a0c-124">您應該使用這些優先`Asc`和`Chr`，Unicode 進出，必須將其轉譯。</span><span class="sxs-lookup"><span data-stu-id="f7a0c-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a0c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7a0c-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="f7a0c-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="f7a0c-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="f7a0c-127">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="f7a0c-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="f7a0c-128">變數宣告</span><span class="sxs-lookup"><span data-stu-id="f7a0c-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="f7a0c-129">使用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="f7a0c-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
