---
title: 如何：在變數中存放多個值 (Visual Basic)
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
ms.openlocfilehash: 781f56c7e710f5130d821ca4796398379dfa4c6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456486"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="85553-102">如何：在變數中存放多個值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85553-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="85553-103">變數會保留多個值，如果您將它的宣告*複合資料型別*。</span><span class="sxs-lookup"><span data-stu-id="85553-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="85553-104">[複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)包括結構、 陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="85553-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="85553-105">複合資料類型的變數可以保留基礎資料類型和其他複合類型的組合。</span><span class="sxs-lookup"><span data-stu-id="85553-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="85553-106">結構和類別可以在程式碼，以及資料保留。</span><span class="sxs-lookup"><span data-stu-id="85553-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="85553-107">若要在變數中存放多個值</span><span class="sxs-lookup"><span data-stu-id="85553-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="85553-108">判斷複合資料類型要使用您的變數。</span><span class="sxs-lookup"><span data-stu-id="85553-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="85553-109">如果沒有已定義的複合資料類型，其定義，讓您的變數可以使用它。</span><span class="sxs-lookup"><span data-stu-id="85553-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="85553-110">定義結構[Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="85553-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="85553-111">定義與陣列[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="85553-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="85553-112">定義具有的類別[Class 陳述式](../../../../visual-basic/language-reference/statements/class-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="85553-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="85553-113">您以宣告變數`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="85553-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="85553-114">變數名稱後面加`As`子句。</span><span class="sxs-lookup"><span data-stu-id="85553-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="85553-115">請依照下列`As`關鍵字搭配適當的複合資料類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="85553-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85553-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85553-116">See Also</span></span>  
 [<span data-ttu-id="85553-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="85553-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="85553-118">類型字元</span><span class="sxs-lookup"><span data-stu-id="85553-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="85553-119">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="85553-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="85553-120">結構</span><span class="sxs-lookup"><span data-stu-id="85553-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="85553-121">陣列</span><span class="sxs-lookup"><span data-stu-id="85553-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="85553-122">物件和類別</span><span class="sxs-lookup"><span data-stu-id="85553-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="85553-123">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="85553-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
