---
title: "複合資料類型 (Visual Basic)"
ms.custom: 
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9adb407757dbee2f7ac5a94118623a62212faec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="80bc5-102">複合資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80bc5-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="80bc5-103">除了基本資料型別[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]供應器，您可以組合建立不同類型的項目*複合資料類型*例如結構、 陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="80bc5-103">In addition to the elementary data types [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="80bc5-104">基本型別和其他複合類型，您可以建置複合資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="80bc5-105">例如，您可以定義結構元素的陣列或結構的陣列成員。</span><span class="sxs-lookup"><span data-stu-id="80bc5-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="80bc5-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-106">Data Types</span></span>  
 <span data-ttu-id="80bc5-107">一種複合類型與不同元件的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="80bc5-108">例如，陣列`Integer`項目不是`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="80bc5-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="80bc5-109">視使用的項目類型、 括號和逗號，通常表示陣列資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="80bc5-110">例如的一維陣列`String`項目以`String()`，和的二維陣列`Boolean`項目以`Boolean(,)`。</span><span class="sxs-lookup"><span data-stu-id="80bc5-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="80bc5-111">結構類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-111">Structure Types</span></span>  
 <span data-ttu-id="80bc5-112">沒有可包含所有結構的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="80bc5-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="80bc5-113">相反地，結構的每個定義都代表唯一的資料類型，即使兩個結構會定義相同的項目相同的順序。</span><span class="sxs-lookup"><span data-stu-id="80bc5-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="80bc5-114">不過，如果您建立兩個或多個執行個體相同的結構，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會考慮它們是相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="80bc5-115">Tuple</span><span class="sxs-lookup"><span data-stu-id="80bc5-115">Tuples</span></span>

<span data-ttu-id="80bc5-116">Tuple 是輕量型的結構，包含其類型已預先定義的兩個或多個欄位。</span><span class="sxs-lookup"><span data-stu-id="80bc5-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="80bc5-117">開始 Visual Basic 2017，支援 Tuple。</span><span class="sxs-lookup"><span data-stu-id="80bc5-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="80bc5-118">Tuple 最常用在單一方法呼叫傳回多個值，而不需傳址方式傳遞引數，或封裝更重量類別或結構中傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="80bc5-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="80bc5-119">請參閱[Tuple](tuples.md)如需有關 tuple 的主題。</span><span class="sxs-lookup"><span data-stu-id="80bc5-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="80bc5-120">陣列類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-120">Array Types</span></span>  
 <span data-ttu-id="80bc5-121">沒有可包含所有陣列的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="80bc5-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="80bc5-122">陣列的特定執行個體的資料類型是由以下決定：</span><span class="sxs-lookup"><span data-stu-id="80bc5-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="80bc5-123">事實上，在陣列</span><span class="sxs-lookup"><span data-stu-id="80bc5-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="80bc5-124">陣列的陣序 （維度數目）</span><span class="sxs-lookup"><span data-stu-id="80bc5-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="80bc5-125">陣列的項目類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-125">The element type of the array</span></span>  
  
 <span data-ttu-id="80bc5-126">特別是，指定維度的長度不是執行個體的資料類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="80bc5-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="80bc5-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="80bc5-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="80bc5-128">在上述範例中，陣列變數`arrayA`和`arrayB`會被視為相同的資料類型的 — `Byte()` — 即使已初始化為不同的長度。</span><span class="sxs-lookup"><span data-stu-id="80bc5-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="80bc5-129">變數`arrayB`和`arrayC`相同類型的不是，因為其項目類型不同。</span><span class="sxs-lookup"><span data-stu-id="80bc5-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="80bc5-130">變數`arrayC`和`arrayD`相同類型的不是，因為其順位不同。</span><span class="sxs-lookup"><span data-stu-id="80bc5-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="80bc5-131">變數`arrayD`和`arrayE`有相同的類型 — `Short(,)` ，因為它們的排列次序和項目型別是相同的即使`arrayD`尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="80bc5-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="80bc5-132">如需陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="80bc5-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="80bc5-133">類別類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-133">Class Types</span></span>  
 <span data-ttu-id="80bc5-134">沒有可包含的所有類別的單一資料型別。</span><span class="sxs-lookup"><span data-stu-id="80bc5-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="80bc5-135">雖然一個類別可以繼承自另一個類別，每一個都是個別的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="80bc5-136">多個相同的類別執行個體都屬於相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="80bc5-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="80bc5-137">如果您將一個類別的執行個體變數指派給另一個時，不只有相同的資料類型，其指向在記憶體中相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="80bc5-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="80bc5-138">如需類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="80bc5-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bc5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80bc5-139">See Also</span></span>  
 [<span data-ttu-id="80bc5-140">資料類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="80bc5-141">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="80bc5-142">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="80bc5-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="80bc5-143">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="80bc5-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="80bc5-144">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="80bc5-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="80bc5-145">結構</span><span class="sxs-lookup"><span data-stu-id="80bc5-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="80bc5-146">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="80bc5-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="80bc5-147">如何：在變數中存放多個值</span><span class="sxs-lookup"><span data-stu-id="80bc5-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
