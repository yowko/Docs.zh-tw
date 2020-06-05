---
title: 作法：在變數中存放多個值
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393892"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="a8637-102">如何：在變數中存放多個值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8637-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="a8637-103">如果您將變數宣告為*複合資料型別*，則會保留一個以上的值。</span><span class="sxs-lookup"><span data-stu-id="a8637-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="a8637-104">[複合資料型別](composite-data-types.md)包括結構、陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="a8637-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="a8637-105">複合資料型別的變數可以保存基本資料類型和其他複合類型的組合。</span><span class="sxs-lookup"><span data-stu-id="a8637-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="a8637-106">結構和類別可以保存程式碼及資料。</span><span class="sxs-lookup"><span data-stu-id="a8637-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="a8637-107">在變數中保存一個以上的值</span><span class="sxs-lookup"><span data-stu-id="a8637-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="a8637-108">決定您想要用於變數的複合資料型別。</span><span class="sxs-lookup"><span data-stu-id="a8637-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="a8637-109">如果尚未定義複合資料型別，請定義它，讓您的變數可以使用它。</span><span class="sxs-lookup"><span data-stu-id="a8637-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="a8637-110">使用[結構語句](../../../language-reference/statements/structure-statement.md)定義結構。</span><span class="sxs-lookup"><span data-stu-id="a8637-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="a8637-111">使用[Dim 語句](../../../language-reference/statements/dim-statement.md)定義陣列。</span><span class="sxs-lookup"><span data-stu-id="a8637-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="a8637-112">使用[Class 語句](../../../language-reference/statements/class-statement.md)定義類別。</span><span class="sxs-lookup"><span data-stu-id="a8637-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="a8637-113">使用語句宣告您的變數 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="a8637-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="a8637-114">請在變數名稱後面加上 `As` 子句。</span><span class="sxs-lookup"><span data-stu-id="a8637-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="a8637-115">請在 `As` 關鍵字後面加上適當的複合資料型別名稱。</span><span class="sxs-lookup"><span data-stu-id="a8637-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8637-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8637-116">See also</span></span>

- [<span data-ttu-id="a8637-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="a8637-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="a8637-118">類型字元</span><span class="sxs-lookup"><span data-stu-id="a8637-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="a8637-119">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="a8637-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="a8637-120">結構</span><span class="sxs-lookup"><span data-stu-id="a8637-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="a8637-121">陣列</span><span class="sxs-lookup"><span data-stu-id="a8637-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="a8637-122">物件和類別</span><span class="sxs-lookup"><span data-stu-id="a8637-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="a8637-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="a8637-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
