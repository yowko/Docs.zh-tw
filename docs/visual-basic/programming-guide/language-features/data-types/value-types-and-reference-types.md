---
title: Value Types and Reference Types
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 9456316f71a213905bcb50336533c4e618f5174a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651579"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="78998-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="78998-102">Value Types and Reference Types</span></span>
<span data-ttu-id="78998-103">在 Visual Basic 中，資料類型會實作其分類為基礎。</span><span class="sxs-lookup"><span data-stu-id="78998-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="78998-104">Visual Basic 資料類型可以根據自己的資料或資料指標，特定類型的變數是否儲存分類。</span><span class="sxs-lookup"><span data-stu-id="78998-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="78998-105">如果它會儲存它自己的資料很*實值型別*; 如果它是的記憶體中其他位置的資料會保留指標*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="78998-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="78998-106">實值類型</span><span class="sxs-lookup"><span data-stu-id="78998-106">Value Types</span></span>  
 <span data-ttu-id="78998-107">資料類型是*實值型別*如果它包含在它自己的記憶體配置中的資料。</span><span class="sxs-lookup"><span data-stu-id="78998-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="78998-108">實值類型包括：</span><span class="sxs-lookup"><span data-stu-id="78998-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="78998-109">所有的數值資料類型</span><span class="sxs-lookup"><span data-stu-id="78998-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="78998-110">`Boolean`、`Char` 和 `Date`</span><span class="sxs-lookup"><span data-stu-id="78998-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="78998-111">所有的結構，即使它們的成員屬於參考類型</span><span class="sxs-lookup"><span data-stu-id="78998-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="78998-112">列舉型別，因為其基礎類型一律為`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或 `ULong`</span><span class="sxs-lookup"><span data-stu-id="78998-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="78998-113">每個結構是實值類型，即使它包含參考類型的成員。</span><span class="sxs-lookup"><span data-stu-id="78998-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="78998-114">基於這個理由，實值類型例如`Char`和`Integer`.NET Framework 結構來實作。</span><span class="sxs-lookup"><span data-stu-id="78998-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="78998-115">您可以使用保留的關鍵字，例如，宣告實值類型`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="78998-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="78998-116">您也可以使用`New`初始化實值類型的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="78998-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="78998-117">這是特別有用，如果型別參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="78998-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="78998-118">舉例來說，這是<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`值從提供的部分。</span><span class="sxs-lookup"><span data-stu-id="78998-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="78998-119">參考類型</span><span class="sxs-lookup"><span data-stu-id="78998-119">Reference Types</span></span>  
 <span data-ttu-id="78998-120">A*參考型別*包含保存資料的另一個記憶體位置的指標。</span><span class="sxs-lookup"><span data-stu-id="78998-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="78998-121">參考型別包括：</span><span class="sxs-lookup"><span data-stu-id="78998-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="78998-122">所有的陣列，即使其元素為實值類型</span><span class="sxs-lookup"><span data-stu-id="78998-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="78998-123">類別類型例如 <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="78998-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="78998-124">委派</span><span class="sxs-lookup"><span data-stu-id="78998-124">Delegates</span></span>  
  
 <span data-ttu-id="78998-125">類別是*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="78998-125">A class is a *reference type*.</span></span> <span data-ttu-id="78998-126">基於這個理由，參考類型例如`Object`和`String`支援[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別。</span><span class="sxs-lookup"><span data-stu-id="78998-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="78998-127">請注意，每個陣列參考類型，即使其成員都是實值類型。</span><span class="sxs-lookup"><span data-stu-id="78998-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="78998-128">由於每個參考型別代表基本的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，當您將它初始化。</span><span class="sxs-lookup"><span data-stu-id="78998-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="78998-129">下列陳述式初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="78998-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="78998-130">不是類型的項目</span><span class="sxs-lookup"><span data-stu-id="78998-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="78998-131">下列的程式設計項目不符合做為型別，因為您無法將它們其中任何一個指定為資料類型的宣告的項目：</span><span class="sxs-lookup"><span data-stu-id="78998-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="78998-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="78998-132">Namespaces</span></span>  
  
-   <span data-ttu-id="78998-133">模組</span><span class="sxs-lookup"><span data-stu-id="78998-133">Modules</span></span>  
  
-   <span data-ttu-id="78998-134">事件</span><span class="sxs-lookup"><span data-stu-id="78998-134">Events</span></span>  
  
-   <span data-ttu-id="78998-135">屬性和程序</span><span class="sxs-lookup"><span data-stu-id="78998-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="78998-136">變數、 常數和欄位</span><span class="sxs-lookup"><span data-stu-id="78998-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="78998-137">使用物件資料類型</span><span class="sxs-lookup"><span data-stu-id="78998-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="78998-138">您可以將參考類型或實值類型指派給變數`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="78998-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="78998-139">`Object`變數一律會保留指標的資料，永遠不會資料本身。</span><span class="sxs-lookup"><span data-stu-id="78998-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="78998-140">不過，如果您指派至實值類型`Object`變數，其行為就如同它包含它自己的資料。</span><span class="sxs-lookup"><span data-stu-id="78998-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="78998-141">如需詳細資訊，請參閱[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="78998-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="78998-142">您可以找出是否`Object`變數做為參考類型或實值類型傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="78998-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="78998-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 傳回`True`如果內容`Object`變數代表參考型別。</span><span class="sxs-lookup"><span data-stu-id="78998-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78998-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78998-144">See Also</span></span>  
 [<span data-ttu-id="78998-145">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="78998-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="78998-146">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="78998-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="78998-147">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="78998-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="78998-148">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="78998-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="78998-149">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="78998-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="78998-150">資料類型</span><span class="sxs-lookup"><span data-stu-id="78998-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
