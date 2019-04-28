---
title: 複合資料類型 (Visual Basic)
ms.date: 04/25/2017
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
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907383"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="fc875-102">複合資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc875-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="fc875-103">除了提供基本資料型別 Visual Basic，您也可以組合來建立不同類型的項目*複合資料型別*結構、 陣列等類別。</span><span class="sxs-lookup"><span data-stu-id="fc875-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="fc875-104">從基本型別，以及從其他複合類型，您可以建置複合資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc875-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="fc875-105">比方說，您可以定義陣列的結構項目或結構的陣列成員。</span><span class="sxs-lookup"><span data-stu-id="fc875-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="fc875-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="fc875-106">Data Types</span></span>  
 <span data-ttu-id="fc875-107">一種複合類型與其中任何元件的資料類型不同。</span><span class="sxs-lookup"><span data-stu-id="fc875-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="fc875-108">例如，陣列`Integer`項目不是`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="fc875-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="fc875-109">視使用的項目型別、 括號和逗號，通常表示陣列資料型別。</span><span class="sxs-lookup"><span data-stu-id="fc875-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="fc875-110">比方說，一維陣列`String`項目以`String()`，和的二維陣列`Boolean`項目以`Boolean(,)`。</span><span class="sxs-lookup"><span data-stu-id="fc875-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="fc875-111">結構類型</span><span class="sxs-lookup"><span data-stu-id="fc875-111">Structure Types</span></span>  
 <span data-ttu-id="fc875-112">沒有任何單一資料型別，其中包含所有的結構。</span><span class="sxs-lookup"><span data-stu-id="fc875-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="fc875-113">相反地，結構的每個定義都代表唯一的資料類型，即使兩個結構會定義相同的項目相同的順序。</span><span class="sxs-lookup"><span data-stu-id="fc875-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="fc875-114">不過，如果您建立的相同結構的兩個或多個執行個體時，Visual Basic 會將它們視為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc875-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="fc875-115">Tuple</span><span class="sxs-lookup"><span data-stu-id="fc875-115">Tuples</span></span>

<span data-ttu-id="fc875-116">Tuple 是輕量級的結構，其中包含的類型預先定義的兩個或多個欄位。</span><span class="sxs-lookup"><span data-stu-id="fc875-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="fc875-117">使用 Visual Basic 2017 開始，支援 Tuple。</span><span class="sxs-lookup"><span data-stu-id="fc875-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="fc875-118">Tuple 最常用的單一方法呼叫傳回多個值，而無需以傳址方式傳遞引數，或封裝在更高負載類別或結構中傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="fc875-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="fc875-119">請參閱[Tuple](tuples.md) tuple 的更多有關的主題。</span><span class="sxs-lookup"><span data-stu-id="fc875-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="fc875-120">陣列類型</span><span class="sxs-lookup"><span data-stu-id="fc875-120">Array Types</span></span>  
 <span data-ttu-id="fc875-121">沒有單一的資料類型可包含所有的陣列。</span><span class="sxs-lookup"><span data-stu-id="fc875-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="fc875-122">陣列的特定執行個體的資料類型是由下列決定：</span><span class="sxs-lookup"><span data-stu-id="fc875-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="fc875-123">屬於陣列的這個事實</span><span class="sxs-lookup"><span data-stu-id="fc875-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="fc875-124">陣列陣序 （維度數目）</span><span class="sxs-lookup"><span data-stu-id="fc875-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="fc875-125">陣列的項目類型</span><span class="sxs-lookup"><span data-stu-id="fc875-125">The element type of the array</span></span>  
  
 <span data-ttu-id="fc875-126">特別是，指定維度的長度不是執行個體的資料類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="fc875-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="fc875-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="fc875-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="fc875-128">在上述範例中，陣列變數`arrayA`並`arrayB`會被視為是相同的資料型別 — `Byte()` — 即使它們初始化為不同的長度。</span><span class="sxs-lookup"><span data-stu-id="fc875-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="fc875-129">變數`arrayB`和`arrayC`相同類型的不是，因為其項目類型不同。</span><span class="sxs-lookup"><span data-stu-id="fc875-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="fc875-130">變數`arrayC`和`arrayD`相同類型的不是，因為其陣序規範不相同。</span><span class="sxs-lookup"><span data-stu-id="fc875-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="fc875-131">變數`arrayD`並`arrayE`有相同的類型 — `Short(,)` — 因為其陣序規範 」 和 「 項目型別完全相同，即使`arrayD`尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="fc875-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="fc875-132">如需有關陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fc875-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="fc875-133">類別類型</span><span class="sxs-lookup"><span data-stu-id="fc875-133">Class Types</span></span>  
 <span data-ttu-id="fc875-134">沒有單一的資料類型可包含的所有類別。</span><span class="sxs-lookup"><span data-stu-id="fc875-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="fc875-135">雖然一個類別可以繼承自另一個類別，每一個會是不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc875-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="fc875-136">多個相同的類別執行個體都屬於相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fc875-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="fc875-137">如果您將一個類別執行個體變數指派給另一個時，不只它們有相同的資料類型，其指向記憶體中相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc875-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="fc875-138">如需有關類別的詳細資訊，請參閱[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fc875-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc875-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc875-139">See also</span></span>

- [<span data-ttu-id="fc875-140">資料類型</span><span class="sxs-lookup"><span data-stu-id="fc875-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="fc875-141">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="fc875-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="fc875-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc875-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="fc875-143">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="fc875-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="fc875-144">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="fc875-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="fc875-145">結構</span><span class="sxs-lookup"><span data-stu-id="fc875-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="fc875-146">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="fc875-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="fc875-147">如何：在變數中存放多個值</span><span class="sxs-lookup"><span data-stu-id="fc875-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
