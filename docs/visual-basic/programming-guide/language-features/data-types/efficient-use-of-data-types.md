---
title: "有效率地使用資料類型 (Visual Basic) |Microsoft 文件"
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
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
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
ms.openlocfilehash: ca8d5885aea12a3f1f9cb35f08bf63c1a89e7ebc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="91507-102">有效率地使用資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91507-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="91507-103">未宣告的變數和不具資料型別宣告的變數指派`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="91507-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="91507-104">這樣可以容易撰寫的程式速度快，但它可能會使程式執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="91507-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="91507-105">強型別</span><span class="sxs-lookup"><span data-stu-id="91507-105">Strong Typing</span></span>  
 <span data-ttu-id="91507-106">指定所有變數的資料型別稱為*強型別*。</span><span class="sxs-lookup"><span data-stu-id="91507-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="91507-107">使用強型別有下列優點︰</span><span class="sxs-lookup"><span data-stu-id="91507-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="91507-108">它可讓您的變數的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="91507-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="91507-109">這可讓您查看其屬性和其他成員，當您輸入程式碼中。</span><span class="sxs-lookup"><span data-stu-id="91507-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="91507-110">它會利用編譯器型別檢查。</span><span class="sxs-lookup"><span data-stu-id="91507-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="91507-111">這會攔截可能會在執行階段，因為例如溢位錯誤而失敗的陳述式。</span><span class="sxs-lookup"><span data-stu-id="91507-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="91507-112">也會對方法的呼叫攔截並不支援的物件。</span><span class="sxs-lookup"><span data-stu-id="91507-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="91507-113">這樣可以更快地執行您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91507-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="91507-114">最有效率的資料類型</span><span class="sxs-lookup"><span data-stu-id="91507-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="91507-115">對於絕對不能包含分數的變數，整數類資料類型會比非整數類型有效。</span><span class="sxs-lookup"><span data-stu-id="91507-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="91507-116">在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，`Integer`和`UInteger`是最有效率的數字類型。</span><span class="sxs-lookup"><span data-stu-id="91507-116">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="91507-117">小數的數字，`Double`是最有效率的資料類型，因為目前平台上的處理器執行雙精度浮點數運算。</span><span class="sxs-lookup"><span data-stu-id="91507-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="91507-118">不過，作業`Double`速度與整數類資料型別，例如`Integer`。</span><span class="sxs-lookup"><span data-stu-id="91507-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="91507-119">指定資料型別</span><span class="sxs-lookup"><span data-stu-id="91507-119">Specifying Data Type</span></span>  
 <span data-ttu-id="91507-120">使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告特定型別的變數。</span><span class="sxs-lookup"><span data-stu-id="91507-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="91507-121">您可以使用，以同時指定其存取層級[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="91507-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="91507-122">字元轉換</span><span class="sxs-lookup"><span data-stu-id="91507-122">Character Conversion</span></span>  
 <span data-ttu-id="91507-123">`AscW`和`ChrW`函式會以 Unicode 作業。</span><span class="sxs-lookup"><span data-stu-id="91507-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="91507-124">您應該使用這些優先`Asc`和`Chr`，這必須在傳入和傳出 Unicode 轉譯。</span><span class="sxs-lookup"><span data-stu-id="91507-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91507-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91507-125">See Also</span></span>  
 <span data-ttu-id="91507-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="91507-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></span></span>   
 <span data-ttu-id="91507-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="91507-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
 <span data-ttu-id="91507-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="91507-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></span></span>   
 <span data-ttu-id="91507-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="91507-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>   
<span data-ttu-id="91507-130"> [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="91507-130"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="91507-131"> [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="91507-131"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="91507-132"> [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="91507-132"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="91507-133"> [使用 IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span><span class="sxs-lookup"><span data-stu-id="91507-133"> [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span></span>
