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
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504887"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="1b9ad-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="1b9ad-102">Value Types and Reference Types</span></span>
<span data-ttu-id="1b9ad-103">有兩種類型的 Visual Basic 中類型： 參考類型和實值型別。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="1b9ad-104">參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="1b9ad-105">使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="1b9ad-106">使用實值類型，每個變數都有它自己的複本的資料，而且不可能會影響其他的一個變數上進行的作業 (除了的情況[ByRef 參數的修飾詞](../../../language-reference/modifiers/byref.md))。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="1b9ad-107">實值類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-107">Value Types</span></span>  
 <span data-ttu-id="1b9ad-108">資料類型是*實值型別*它存放在自己的記憶體配置中的資料。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="1b9ad-109">實值型別包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="1b9ad-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="1b9ad-110">所有數值資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-110">All numeric data types</span></span>  
  
- <span data-ttu-id="1b9ad-111">`Boolean`、 `Char`和 `Date`</span><span class="sxs-lookup"><span data-stu-id="1b9ad-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="1b9ad-112">所有的結構，即使它們的成員是參考型別</span><span class="sxs-lookup"><span data-stu-id="1b9ad-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="1b9ad-113">列舉型別，因為其基礎類型一律`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或 `ULong`</span><span class="sxs-lookup"><span data-stu-id="1b9ad-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="1b9ad-114">每個結構是實值類型，即使它包含參考型別成員。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="1b9ad-115">基於這個理由，實值型別這類`Char`和`Integer`由.NET Framework 結構。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="1b9ad-116">您可以使用的保留的關鍵字，例如，宣告實值型別`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="1b9ad-117">您也可以使用`New`初始化實值類型的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="1b9ad-118">這是特別有用，如果類型具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="1b9ad-119">舉例來說，這<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`從提供的組件的值。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="1b9ad-120">參考類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-120">Reference Types</span></span>  
 <span data-ttu-id="1b9ad-121">A*參考的型別*儲存其資料的參考。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="1b9ad-122">參考類型包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="1b9ad-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="1b9ad-123">所有的陣列，即使其元素為實值類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="1b9ad-124">類別類型例如 <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="1b9ad-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="1b9ad-125">委派</span><span class="sxs-lookup"><span data-stu-id="1b9ad-125">Delegates</span></span>  
  
 <span data-ttu-id="1b9ad-126">類別是*參考的型別*。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-126">A class is a *reference type*.</span></span> <span data-ttu-id="1b9ad-127">請注意，每個陣列參考類型，即使其成員都是實值型別。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="1b9ad-128">由於每個參考型別代表基本的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字時將它初始化。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="1b9ad-129">下列陳述式初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="1b9ad-130">不是類型的項目</span><span class="sxs-lookup"><span data-stu-id="1b9ad-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="1b9ad-131">下列的程式設計項目不會限定為型別，因為您無法指定任何一個宣告的項目資料類型為：</span><span class="sxs-lookup"><span data-stu-id="1b9ad-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="1b9ad-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="1b9ad-132">Namespaces</span></span>  
  
- <span data-ttu-id="1b9ad-133">模組</span><span class="sxs-lookup"><span data-stu-id="1b9ad-133">Modules</span></span>  
  
- <span data-ttu-id="1b9ad-134">事件</span><span class="sxs-lookup"><span data-stu-id="1b9ad-134">Events</span></span>  
  
- <span data-ttu-id="1b9ad-135">屬性和程序</span><span class="sxs-lookup"><span data-stu-id="1b9ad-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="1b9ad-136">變數、 常數和欄位</span><span class="sxs-lookup"><span data-stu-id="1b9ad-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="1b9ad-137">使用物件資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="1b9ad-138">您可以將參考類型或實值型別指派給變數的`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="1b9ad-139">`Object`變數一律會保留資料，也就是永遠不會將資料本身的參考。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="1b9ad-140">不過，如果您指派至實值型別`Object`變數，其行為就如同它會保留它自己的資料。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="1b9ad-141">如需詳細資訊，請參閱 < [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="1b9ad-142">您可以找出是否`Object`變數做為參考型別或實值型別傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別的<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1b9ad-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 會傳回`True`如果內容`Object`變數代表參考型別。</span><span class="sxs-lookup"><span data-stu-id="1b9ad-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9ad-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b9ad-144">See also</span></span>

- [<span data-ttu-id="1b9ad-145">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="1b9ad-146">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="1b9ad-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="1b9ad-147">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="1b9ad-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="1b9ad-148">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="1b9ad-149">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="1b9ad-150">資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9ad-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
