---
title: 作法：在變數中保存一個以上的值（Visual Basic）
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054189"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="b2329-102">作法：在變數中保存一個以上的值（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b2329-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="b2329-103">如果您將變數宣告為*複合資料型別*，則會保留一個以上的值。</span><span class="sxs-lookup"><span data-stu-id="b2329-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="b2329-104">[複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)包括結構、陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="b2329-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="b2329-105">複合資料型別的變數可以保存基本資料類型和其他複合類型的組合。</span><span class="sxs-lookup"><span data-stu-id="b2329-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="b2329-106">結構和類別可以保存程式碼及資料。</span><span class="sxs-lookup"><span data-stu-id="b2329-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="b2329-107">在變數中保存一個以上的值</span><span class="sxs-lookup"><span data-stu-id="b2329-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="b2329-108">決定您想要用於變數的複合資料型別。</span><span class="sxs-lookup"><span data-stu-id="b2329-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="b2329-109">如果尚未定義複合資料型別，請定義它，讓您的變數可以使用它。</span><span class="sxs-lookup"><span data-stu-id="b2329-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="b2329-110">使用[結構語句](../../../../visual-basic/language-reference/statements/structure-statement.md)定義結構。</span><span class="sxs-lookup"><span data-stu-id="b2329-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="b2329-111">使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)定義陣列。</span><span class="sxs-lookup"><span data-stu-id="b2329-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="b2329-112">使用[Class 語句](../../../../visual-basic/language-reference/statements/class-statement.md)定義類別。</span><span class="sxs-lookup"><span data-stu-id="b2329-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="b2329-113">使用`Dim`語句宣告您的變數。</span><span class="sxs-lookup"><span data-stu-id="b2329-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="b2329-114">請在變數名稱後面加`As`上子句。</span><span class="sxs-lookup"><span data-stu-id="b2329-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="b2329-115">請在`As`關鍵字後面加上適當的複合資料型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b2329-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2329-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2329-116">See also</span></span>

- [<span data-ttu-id="b2329-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="b2329-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b2329-118">類型字元</span><span class="sxs-lookup"><span data-stu-id="b2329-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="b2329-119">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="b2329-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="b2329-120">結構</span><span class="sxs-lookup"><span data-stu-id="b2329-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b2329-121">陣列</span><span class="sxs-lookup"><span data-stu-id="b2329-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="b2329-122">物件和類別</span><span class="sxs-lookup"><span data-stu-id="b2329-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="b2329-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="b2329-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
