---
title: "複合資料類型 (Visual Basic) |Microsoft 文件"
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
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
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
ms.openlocfilehash: 5f0c6215ce45d724a7b5c8c4f8e34ea27bce8fe4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="594ed-102">複合資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="594ed-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="594ed-103">除了基本資料型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]供應器，您可以組合建立不同類型的項目*複合資料型別*例如結構、 陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="594ed-103">In addition to the elementary data types [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="594ed-104">基本型別和其他複合類型，您可以建置複合資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="594ed-105">例如，您可以定義結構元素的陣列或結構的陣列成員。</span><span class="sxs-lookup"><span data-stu-id="594ed-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="594ed-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="594ed-106">Data Types</span></span>  
 <span data-ttu-id="594ed-107">一種複合類型是不同於元件的資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="594ed-108">例如，陣列`Integer`項目不是`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="594ed-109">使用所需的項目型別、 括號和逗號，通常表示陣列資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="594ed-110">比方說，一維陣列的`String`項目以`String()`，和一個二維陣列`Boolean`項目以`Boolean(,)`。</span><span class="sxs-lookup"><span data-stu-id="594ed-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="594ed-111">結構化型別</span><span class="sxs-lookup"><span data-stu-id="594ed-111">Structure Types</span></span>  
 <span data-ttu-id="594ed-112">沒有可包含所有結構的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="594ed-113">相反地，每個結構的定義都代表唯一的資料類型，即使兩個結構會定義相同的項目會以相同的順序。</span><span class="sxs-lookup"><span data-stu-id="594ed-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="594ed-114">不過，如果您建立兩個或多個執行個體相同的結構，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會考慮它們是相同的資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="array-types"></a><span data-ttu-id="594ed-115">陣列型別</span><span class="sxs-lookup"><span data-stu-id="594ed-115">Array Types</span></span>  
 <span data-ttu-id="594ed-116">沒有可包含所有陣列的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-116">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="594ed-117">陣列的特定執行個體的資料型別是由下列決定︰</span><span class="sxs-lookup"><span data-stu-id="594ed-117">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="594ed-118">根本就屬於陣列</span><span class="sxs-lookup"><span data-stu-id="594ed-118">The fact of being an array</span></span>  
  
-   <span data-ttu-id="594ed-119">陣列的陣序規範 （維度數目）</span><span class="sxs-lookup"><span data-stu-id="594ed-119">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="594ed-120">陣列的項目類型</span><span class="sxs-lookup"><span data-stu-id="594ed-120">The element type of the array</span></span>  
  
 <span data-ttu-id="594ed-121">特別是，指定維度的長度不是執行個體的資料類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="594ed-121">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="594ed-122">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="594ed-122">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="594ed-123">在上述範例中，陣列變數`arrayA`和`arrayB`視為相同的資料類型的 — `Byte()` — 即使它們會初始化為不同的長度。</span><span class="sxs-lookup"><span data-stu-id="594ed-123">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="594ed-124">變數`arrayB`和`arrayC`相同類型的不是，因為其項目型別不同。</span><span class="sxs-lookup"><span data-stu-id="594ed-124">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="594ed-125">變數`arrayC`和`arrayD`相同類型的不是，因為其陣序規範不相同。</span><span class="sxs-lookup"><span data-stu-id="594ed-125">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="594ed-126">變數`arrayD`和`arrayE`有相同的類型 — `Short(,)` ，因為它們的陣序規範和項目類型都相同，即使`arrayD`尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="594ed-126">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="594ed-127">如需有關陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="594ed-127">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="594ed-128">類別類型</span><span class="sxs-lookup"><span data-stu-id="594ed-128">Class Types</span></span>  
 <span data-ttu-id="594ed-129">沒有可包含的所有類別的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="594ed-129">There is no single data type comprising all classes.</span></span> <span data-ttu-id="594ed-130">雖然一個類別可以繼承自另一個類別，每一個都是個別的資料類型。</span><span class="sxs-lookup"><span data-stu-id="594ed-130">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="594ed-131">多個相同執行個體是類別的相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="594ed-131">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="594ed-132">如果指派給另一個類別的執行個體變數，不只它們有相同的資料類型，其指向在記憶體中相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="594ed-132">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="594ed-133">如需類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="594ed-133">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594ed-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="594ed-134">See Also</span></span>  
 <span data-ttu-id="594ed-135">[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-135">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="594ed-136"> [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-136"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="594ed-137"> [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-137"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="594ed-138"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-138"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="594ed-139"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-139"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="594ed-140"> [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-140"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="594ed-141"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="594ed-141"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="594ed-142"> [如何：在變數中存放多個值](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span><span class="sxs-lookup"><span data-stu-id="594ed-142"> [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span></span>
