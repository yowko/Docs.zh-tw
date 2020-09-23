---
title: 有效率地使用資料類型
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
ms.openlocfilehash: 7f446b264dcb5c05ed6ddfba34acbbf66be0e447
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084108"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="cbe1e-102">有效率地使用資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe1e-102">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="cbe1e-103">未宣告的變數和沒有資料類型宣告的變數會被指派 `Object` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="cbe1e-104">這可讓您輕鬆地快速撰寫程式，但這可能會導致這些程式執行速度變得更慢。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="cbe1e-105">強型別</span><span class="sxs-lookup"><span data-stu-id="cbe1e-105">Strong Typing</span></span>

 <span data-ttu-id="cbe1e-106">指定所有變數的資料類型稱為 *強*型別。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="cbe1e-107">使用強型別有幾個優點：</span><span class="sxs-lookup"><span data-stu-id="cbe1e-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="cbe1e-108">它可為您的變數啟用 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="cbe1e-109">當您在程式碼中輸入時，這可讓您查看其屬性和其他成員。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="cbe1e-110">它會利用編譯器類型檢查。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="cbe1e-111">這會攔截在執行時間因為溢位之類的錯誤而失敗的語句。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="cbe1e-112">它也會攔截對不支援它們之物件的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="cbe1e-113">這會導致程式碼的執行速度更快。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="cbe1e-114">最有效率的資料類型</span><span class="sxs-lookup"><span data-stu-id="cbe1e-114">Most Efficient Data Types</span></span>

 <span data-ttu-id="cbe1e-115">對於永遠不包含分數的變數而言，整數資料類型比非整數類型更有效率。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="cbe1e-116">在 Visual Basic 中， `Integer` 和 `UInteger` 是最有效率的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="cbe1e-117">對於小數數位而言， `Double` 是最有效率的資料類型，因為目前平臺上的處理器會以雙精確度執行浮點運算。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="cbe1e-118">不過，使用的作業 `Double` 不像整數類資料類型一樣快 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="cbe1e-119">指定資料類型</span><span class="sxs-lookup"><span data-stu-id="cbe1e-119">Specifying Data Type</span></span>

 <span data-ttu-id="cbe1e-120">使用 [Dim 語句](../../../language-reference/statements/dim-statement.md) 來宣告特定型別的變數。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-120">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="cbe1e-121">您可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 關鍵字同時指定其存取層級，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-121">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="cbe1e-122">字元轉換</span><span class="sxs-lookup"><span data-stu-id="cbe1e-122">Character Conversion</span></span>

 <span data-ttu-id="cbe1e-123">和函式會 `AscW` `ChrW` 以 Unicode 運作。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="cbe1e-124">您應該將其喜好設定為 `Asc` 和 `Chr` ，而必須將其轉譯成 Unicode 或從中轉換。</span><span class="sxs-lookup"><span data-stu-id="cbe1e-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbe1e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe1e-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="cbe1e-126">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="cbe1e-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="cbe1e-127">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="cbe1e-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="cbe1e-128">變數宣告</span><span class="sxs-lookup"><span data-stu-id="cbe1e-128">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="cbe1e-129">使用 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="cbe1e-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
