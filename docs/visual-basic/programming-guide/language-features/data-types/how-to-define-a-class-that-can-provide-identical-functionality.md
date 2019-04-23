---
title: HOW TO：定義的類別，可提供完全相同的功能上不同的資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 9121041f936c091cda0e2af41b4f5be8d826d582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318439"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="b4075-102">HOW TO：定義的類別，可提供完全相同的功能上不同的資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4075-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="b4075-103">您可以定義一個類別，以從中建立可在不同資料類型上提供相同功能的物件。</span><span class="sxs-lookup"><span data-stu-id="b4075-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="b4075-104">若要這樣做，請在定義中指定一個或多個 *「類型參數」* (type parameter)。</span><span class="sxs-lookup"><span data-stu-id="b4075-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="b4075-105">類別之後可以作為使用各種資料類型之物件的範本。</span><span class="sxs-lookup"><span data-stu-id="b4075-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="b4075-106">使用這種方法所定義的類別稱為 *「泛型類別」*(generic class)。</span><span class="sxs-lookup"><span data-stu-id="b4075-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="b4075-107">定義泛型類別的優點是只需要定義一次，而且您的程式碼可以使用它來建立許多使用各種資料類型的物件。</span><span class="sxs-lookup"><span data-stu-id="b4075-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="b4075-108">這所導致的效能優於定義具有 `Object` 類型的類別。</span><span class="sxs-lookup"><span data-stu-id="b4075-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="b4075-109">除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。</span><span class="sxs-lookup"><span data-stu-id="b4075-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="b4075-110">定義具有類型參數的類別</span><span class="sxs-lookup"><span data-stu-id="b4075-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="b4075-111">以一般方式定義類別。</span><span class="sxs-lookup"><span data-stu-id="b4075-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="b4075-112">立即在類別名稱後面加入 `(Of` *類型參數*`)` ，以指定類型參數。</span><span class="sxs-lookup"><span data-stu-id="b4075-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="b4075-113">如果您有多個類型參數，請在括號內建立以逗號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="b4075-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="b4075-114">請不要重複 `Of` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b4075-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="b4075-115">如果您的程式碼對類型參數執行簡單指派以外的作業，請在該類型參數後面加上 `As` 子句來加入一個或多個 *「條件約束」*(constraint)。</span><span class="sxs-lookup"><span data-stu-id="b4075-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="b4075-116">條件約束保證針對該類型參數所提供的類型符合下列這類需求：</span><span class="sxs-lookup"><span data-stu-id="b4075-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="b4075-117">支援您程式碼所執行的作業 (例如 `>`)</span><span class="sxs-lookup"><span data-stu-id="b4075-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="b4075-118">支援您程式碼所存取的成員 (例如方法)</span><span class="sxs-lookup"><span data-stu-id="b4075-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="b4075-119">公開無參數建構函式</span><span class="sxs-lookup"><span data-stu-id="b4075-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="b4075-120">如果您未指定任何條件約束，則您程式碼可使用的唯一作業和成員是 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)所支援的作業和成員。</span><span class="sxs-lookup"><span data-stu-id="b4075-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="b4075-121">如需詳細資訊，請參閱 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="b4075-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="b4075-122">識別要宣告所提供類型的每個類別成員，並將它宣告為 `As` `typeparameter`。</span><span class="sxs-lookup"><span data-stu-id="b4075-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="b4075-123">這適用於內部儲存體、程序參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="b4075-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="b4075-124">請確定您的程式碼只會使用它可提供給 `itemType`之任何資料類型所支援的作業和方法。</span><span class="sxs-lookup"><span data-stu-id="b4075-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="b4075-125">下列範例定義可管理極簡單清單的類別。</span><span class="sxs-lookup"><span data-stu-id="b4075-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="b4075-126">它會將清單保留在內部陣列 `items`中，而 using 程式碼可以宣告清單項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b4075-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="b4075-127">參數化建構函式可讓 using 程式碼設定 `items`上限，而預設建構函式會將此項目設為 9 (共 10 個項目)。</span><span class="sxs-lookup"><span data-stu-id="b4075-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="b4075-128">您可以從 `simpleList` 宣告一個類別來保留 `Integer` 值清單、另一個類別來保留 `String` 值清單，以及另一個類別來保留 `Date` 值。</span><span class="sxs-lookup"><span data-stu-id="b4075-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="b4075-129">除了清單成員的資料類型之外，從所有這些類別建立之物件的行為都相同。</span><span class="sxs-lookup"><span data-stu-id="b4075-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="b4075-130">using 程式碼提供給 `itemType` 的類型引數可以是內建類型 (例如 `Boolean` 或 `Double`)、結構、列舉值或任何類型的類別 (包括您應用程式所定義的其中一個類別)。</span><span class="sxs-lookup"><span data-stu-id="b4075-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="b4075-131">您可以使用下列程式碼測試 `simpleList` 類別。</span><span class="sxs-lookup"><span data-stu-id="b4075-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="b4075-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4075-132">See also</span></span>

- [<span data-ttu-id="b4075-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="b4075-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="b4075-134">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4075-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b4075-135">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="b4075-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="b4075-136">Of</span><span class="sxs-lookup"><span data-stu-id="b4075-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="b4075-137">類型清單</span><span class="sxs-lookup"><span data-stu-id="b4075-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="b4075-138">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="b4075-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="b4075-139">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="b4075-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
