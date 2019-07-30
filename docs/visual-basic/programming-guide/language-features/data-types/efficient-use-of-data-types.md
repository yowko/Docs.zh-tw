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
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631114"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="113d5-102">有效率地使用資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="113d5-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="113d5-103">未宣告的變數和未宣告資料類型的`Object`變數會被指派資料類型。</span><span class="sxs-lookup"><span data-stu-id="113d5-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="113d5-104">這可讓您快速撰寫程式, 但它可能會導致執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="113d5-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="113d5-105">強式類型</span><span class="sxs-lookup"><span data-stu-id="113d5-105">Strong Typing</span></span>
 <span data-ttu-id="113d5-106">指定所有變數的資料類型稱為*強式類型*。</span><span class="sxs-lookup"><span data-stu-id="113d5-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="113d5-107">使用強型別有幾個優點:</span><span class="sxs-lookup"><span data-stu-id="113d5-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="113d5-108">它會針對您的變數啟用 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="113d5-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="113d5-109">這可讓您在程式碼中輸入時, 看到其屬性和其他成員。</span><span class="sxs-lookup"><span data-stu-id="113d5-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="113d5-110">它會利用編譯器類型檢查。</span><span class="sxs-lookup"><span data-stu-id="113d5-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="113d5-111">這會捕捉可能因為溢位錯誤而在執行時間失敗的語句。</span><span class="sxs-lookup"><span data-stu-id="113d5-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="113d5-112">它也會攔截不支援之物件上方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="113d5-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="113d5-113">這會導致程式碼的執行速度更快。</span><span class="sxs-lookup"><span data-stu-id="113d5-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="113d5-114">最有效率的資料類型</span><span class="sxs-lookup"><span data-stu-id="113d5-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="113d5-115">對於永不包含小數的變數而言, 整數資料類型比非整數類型更有效率。</span><span class="sxs-lookup"><span data-stu-id="113d5-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="113d5-116">在 Visual Basic 中`Integer` , `UInteger`和是最有效率的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="113d5-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="113d5-117">針對小數, `Double`是最有效率的資料類型, 因為目前平臺上的處理器會以雙精確度執行浮點運算。</span><span class="sxs-lookup"><span data-stu-id="113d5-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="113d5-118">不過, 使用`Double`的作業與整數類資料類型`Integer`(例如) 的速度並不一樣快。</span><span class="sxs-lookup"><span data-stu-id="113d5-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="113d5-119">指定資料類型</span><span class="sxs-lookup"><span data-stu-id="113d5-119">Specifying Data Type</span></span>
 <span data-ttu-id="113d5-120">使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來宣告特定類型的變數。</span><span class="sxs-lookup"><span data-stu-id="113d5-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="113d5-121">您可以使用[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Private](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字, 同時指定其存取層級, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="113d5-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="113d5-122">字元轉換</span><span class="sxs-lookup"><span data-stu-id="113d5-122">Character Conversion</span></span>
 <span data-ttu-id="113d5-123">`AscW` 和`ChrW`函數會以 Unicode 運作。</span><span class="sxs-lookup"><span data-stu-id="113d5-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="113d5-124">您應該將它們偏好`Asc`用於和`Chr`, 其必須在 Unicode 中轉譯。</span><span class="sxs-lookup"><span data-stu-id="113d5-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="113d5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="113d5-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="113d5-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="113d5-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="113d5-127">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="113d5-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="113d5-128">變數宣告</span><span class="sxs-lookup"><span data-stu-id="113d5-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="113d5-129">使用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="113d5-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
