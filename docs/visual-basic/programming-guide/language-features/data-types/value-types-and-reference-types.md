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
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582637"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="65dc6-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="65dc6-102">Value Types and Reference Types</span></span>
<span data-ttu-id="65dc6-103">Visual Basic 中有兩種類型：參考型別和實數值型別。</span><span class="sxs-lookup"><span data-stu-id="65dc6-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="65dc6-104">參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="65dc6-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="65dc6-105">使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="65dc6-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="65dc6-106">使用實值型別時，每個變數都有自己的資料複本，而且一個變數上的作業不可能影響另一個（在[參數上為 ByRef 修飾](../../../language-reference/modifiers/byref.md)詞的情況除外）。</span><span class="sxs-lookup"><span data-stu-id="65dc6-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="65dc6-107">實值類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-107">Value Types</span></span>  
 <span data-ttu-id="65dc6-108">如果資料類型在它自己的記憶體配置中保存資料，就是實*數值型別*。</span><span class="sxs-lookup"><span data-stu-id="65dc6-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="65dc6-109">數值型別包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="65dc6-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="65dc6-110">所有數值資料類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-110">All numeric data types</span></span>  
  
- <span data-ttu-id="65dc6-111">`Boolean`、 `Char`和 `Date`</span><span class="sxs-lookup"><span data-stu-id="65dc6-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="65dc6-112">所有結構，即使它們的成員是參考型別</span><span class="sxs-lookup"><span data-stu-id="65dc6-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="65dc6-113">列舉，因為其基礎類型一律為 `SByte`、`Short`、`Integer`、`Long`、`Byte`、`UShort`、`UInteger` 或 `ULong`</span><span class="sxs-lookup"><span data-stu-id="65dc6-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="65dc6-114">每個結構都是實值型別，即使它包含引用型別成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="65dc6-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="65dc6-115">基於這個理由，`Char` 和 `Integer` 之類的實值型別會由 .NET Framework 結構來執行。</span><span class="sxs-lookup"><span data-stu-id="65dc6-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="65dc6-116">您可以使用 reserved 關鍵字來宣告實值型別，例如 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="65dc6-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="65dc6-117">您也可以使用 `New` 關鍵字來初始化實值型別。</span><span class="sxs-lookup"><span data-stu-id="65dc6-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="65dc6-118">如果型別具有接受參數的函式，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="65dc6-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="65dc6-119">其中一個範例是 <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> 的函式，它會從提供的部分建立新的 `Decimal` 值。</span><span class="sxs-lookup"><span data-stu-id="65dc6-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="65dc6-120">參考類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-120">Reference Types</span></span>  
 <span data-ttu-id="65dc6-121">*參考型*別會儲存其資料的參考。</span><span class="sxs-lookup"><span data-stu-id="65dc6-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="65dc6-122">參考型別包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="65dc6-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="65dc6-123">所有陣列，即使其元素是實數值型別</span><span class="sxs-lookup"><span data-stu-id="65dc6-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="65dc6-124">類別類型，例如 <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="65dc6-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="65dc6-125">委派</span><span class="sxs-lookup"><span data-stu-id="65dc6-125">Delegates</span></span>  
  
 <span data-ttu-id="65dc6-126">類別是*參考型*別。</span><span class="sxs-lookup"><span data-stu-id="65dc6-126">A class is a *reference type*.</span></span> <span data-ttu-id="65dc6-127">請注意，每個陣列都是參考型別，即使它的成員是實數值型別也是如此。</span><span class="sxs-lookup"><span data-stu-id="65dc6-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="65dc6-128">由於每個參考型別都代表一個基礎 .NET Framework 類別，因此當您初始化它時，您必須使用[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="65dc6-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="65dc6-129">下列語句會初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="65dc6-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="65dc6-130">不是類型的元素</span><span class="sxs-lookup"><span data-stu-id="65dc6-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="65dc6-131">下列程式設計項目不符合型別的資格，因為您無法將其中任何一個當做宣告專案的資料型別。</span><span class="sxs-lookup"><span data-stu-id="65dc6-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="65dc6-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="65dc6-132">Namespaces</span></span>  
  
- <span data-ttu-id="65dc6-133">模組</span><span class="sxs-lookup"><span data-stu-id="65dc6-133">Modules</span></span>  
  
- <span data-ttu-id="65dc6-134">「事件」</span><span class="sxs-lookup"><span data-stu-id="65dc6-134">Events</span></span>  
  
- <span data-ttu-id="65dc6-135">屬性和程式</span><span class="sxs-lookup"><span data-stu-id="65dc6-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="65dc6-136">變數、常數和欄位</span><span class="sxs-lookup"><span data-stu-id="65dc6-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="65dc6-137">使用 Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="65dc6-138">您可以將參考型別或實數值型別指派給 `Object` 資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="65dc6-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="65dc6-139">@No__t_0 變數一律會保留資料的參考，而不是資料本身。</span><span class="sxs-lookup"><span data-stu-id="65dc6-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="65dc6-140">不過，如果您將實值型別指派給 `Object` 變數，它的行為就如同它擁有自己的資料一樣。</span><span class="sxs-lookup"><span data-stu-id="65dc6-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="65dc6-141">如需詳細資訊，請參閱[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="65dc6-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="65dc6-142">您可以藉由將 `Object` 變數當做參考型別或實數值型別傳遞至 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 命名空間的 <xref:Microsoft.VisualBasic.Information> 類別中的 <xref:Microsoft.VisualBasic.Information.IsReference%2A> 方法，來找出它的作用。</span><span class="sxs-lookup"><span data-stu-id="65dc6-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="65dc6-143">如果 `Object` 變數的內容代表參考型別，<xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> 會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="65dc6-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65dc6-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="65dc6-144">See also</span></span>

- [<span data-ttu-id="65dc6-145">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="65dc6-146">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="65dc6-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="65dc6-147">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="65dc6-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="65dc6-148">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="65dc6-149">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="65dc6-150">資料類型</span><span class="sxs-lookup"><span data-stu-id="65dc6-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
