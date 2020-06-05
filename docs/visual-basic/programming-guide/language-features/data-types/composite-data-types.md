---
title: 複合資料類型
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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394294"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="d5d91-102">複合資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d91-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="d5d91-103">除了 Visual Basic 提供的基本資料類型之外，您也可以組合不同類型的專案來建立*複合資料型別*，例如結構、陣列和類別。</span><span class="sxs-lookup"><span data-stu-id="d5d91-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="d5d91-104">您可以從基本類型和其他複合類型建立複合資料型別。</span><span class="sxs-lookup"><span data-stu-id="d5d91-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="d5d91-105">例如，您可以定義結構專案的陣列，或是包含陣列成員的結構。</span><span class="sxs-lookup"><span data-stu-id="d5d91-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="d5d91-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-106">Data Types</span></span>  
 <span data-ttu-id="d5d91-107">複合類型與任何元件的資料類型不同。</span><span class="sxs-lookup"><span data-stu-id="d5d91-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="d5d91-108">例如，元素的陣列 `Integer` 不是 `Integer` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="d5d91-109">陣列資料類型通常會在必要時使用元素類型、括弧和逗號來表示。</span><span class="sxs-lookup"><span data-stu-id="d5d91-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="d5d91-110">例如，一維的 `String` 元素陣列會表示為 `String()` ，而元素的二維陣列 `Boolean` 則會表示為 `Boolean(,)` 。</span><span class="sxs-lookup"><span data-stu-id="d5d91-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="d5d91-111">結構類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-111">Structure Types</span></span>  
 <span data-ttu-id="d5d91-112">沒有組成所有結構的單一資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="d5d91-113">相反地，結構的每個定義都代表唯一的資料類型，即使兩個結構以相同的順序定義相同的元素。</span><span class="sxs-lookup"><span data-stu-id="d5d91-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="d5d91-114">不過，如果您建立相同結構的兩個或多個實例，Visual Basic 會將它們視為相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="d5d91-115">Tuples</span><span class="sxs-lookup"><span data-stu-id="d5d91-115">Tuples</span></span>

<span data-ttu-id="d5d91-116">元組是輕量結構，其中包含兩個或多個預先定義類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="d5d91-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="d5d91-117">從 Visual Basic 2017 開始支援元組。</span><span class="sxs-lookup"><span data-stu-id="d5d91-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="d5d91-118">元組最常用來傳回單一方法呼叫中的多個值，而不需要以傳址方式傳遞引數，或將傳回的欄位封裝在較高的權數類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="d5d91-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="d5d91-119">如需元組的詳細資訊，請參閱[元組](tuples.md)主題。</span><span class="sxs-lookup"><span data-stu-id="d5d91-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="d5d91-120">陣列類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-120">Array Types</span></span>  
 <span data-ttu-id="d5d91-121">沒有組成所有陣列的單一資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="d5d91-122">陣列特定實例的資料類型取決於下列各項：</span><span class="sxs-lookup"><span data-stu-id="d5d91-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="d5d91-123">成為陣列的事實</span><span class="sxs-lookup"><span data-stu-id="d5d91-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="d5d91-124">陣列的順位（維度數目）</span><span class="sxs-lookup"><span data-stu-id="d5d91-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="d5d91-125">陣列的元素類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-125">The element type of the array</span></span>  
  
 <span data-ttu-id="d5d91-126">特別是，指定維度的長度不是實例資料類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="d5d91-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="d5d91-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="d5d91-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="d5d91-128">在上述範例中，會將陣列變數 `arrayA` 和 `arrayB` 視為相同的資料類型（）， `Byte()` 即使它們已初始化為不同的長度也一樣。</span><span class="sxs-lookup"><span data-stu-id="d5d91-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="d5d91-129">變數 `arrayB` 和 `arrayC` 不是相同的類型，因為它們的元素類型不同。</span><span class="sxs-lookup"><span data-stu-id="d5d91-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="d5d91-130">變數 `arrayC` 和 `arrayD` 不屬於相同的類型，因為它們的次序不同。</span><span class="sxs-lookup"><span data-stu-id="d5d91-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="d5d91-131">變數 `arrayD` 和 `arrayE` 具有相同的類型（ `Short(,)` ），因為它們的次序和元素類型相同，即使尚未 `arrayD` 初始化也一樣。</span><span class="sxs-lookup"><span data-stu-id="d5d91-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="d5d91-132">如需陣列的詳細資訊，請參閱[陣列](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d91-132">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="d5d91-133">類別類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-133">Class Types</span></span>  
 <span data-ttu-id="d5d91-134">沒有組成所有類別的單一資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="d5d91-135">雖然一個類別可以繼承自另一個類別，但每個都是不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="d5d91-136">相同類別的多個實例屬於相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d5d91-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="d5d91-137">如果您將一個類別執行個體變數指派給另一個，不只是它們具有相同的資料類型，而是指向記憶體中的相同類別實例。</span><span class="sxs-lookup"><span data-stu-id="d5d91-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="d5d91-138">如需類別的詳細資訊，請參閱[物件和類別](../objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d91-138">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d91-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d91-139">See also</span></span>

- [<span data-ttu-id="d5d91-140">資料類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="d5d91-141">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="d5d91-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="d5d91-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5d91-142">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="d5d91-143">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="d5d91-143">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="d5d91-144">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="d5d91-144">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="d5d91-145">結構</span><span class="sxs-lookup"><span data-stu-id="d5d91-145">Structures</span></span>](structures.md)
- [<span data-ttu-id="d5d91-146">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="d5d91-146">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="d5d91-147">作法：在變數中存放多個值</span><span class="sxs-lookup"><span data-stu-id="d5d91-147">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
