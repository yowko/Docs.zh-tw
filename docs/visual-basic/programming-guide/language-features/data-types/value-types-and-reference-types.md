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
ms.openlocfilehash: 72cb1455300e1ff00d9d558aa5a9df95f32aa7b0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090114"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="c38ae-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="c38ae-102">Value Types and Reference Types</span></span>

<span data-ttu-id="c38ae-103">Visual Basic 中有兩種類型：參考型別和實數值型別。</span><span class="sxs-lookup"><span data-stu-id="c38ae-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="c38ae-104">參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。</span><span class="sxs-lookup"><span data-stu-id="c38ae-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="c38ae-105">使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="c38ae-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="c38ae-106">使用實值型別時，每個變數都有自己的資料複本，而且在某個變數上進行的作業不可能會影響其他 (但在參數) 的 [ByRef 修飾](../../../language-reference/modifiers/byref.md) 詞情況下除外。</span><span class="sxs-lookup"><span data-stu-id="c38ae-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="c38ae-107">實值類型</span><span class="sxs-lookup"><span data-stu-id="c38ae-107">Value Types</span></span>  

 <span data-ttu-id="c38ae-108">如果資料類型在它自己的記憶體配置內保存資料，就是實 *值型* 別。</span><span class="sxs-lookup"><span data-stu-id="c38ae-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="c38ae-109">數值型別包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="c38ae-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="c38ae-110">所有數值資料類型</span><span class="sxs-lookup"><span data-stu-id="c38ae-110">All numeric data types</span></span>  
  
- <span data-ttu-id="c38ae-111">`Boolean`、`Char` 和 `Date`</span><span class="sxs-lookup"><span data-stu-id="c38ae-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="c38ae-112">所有結構，即使其成員為參考型別</span><span class="sxs-lookup"><span data-stu-id="c38ae-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="c38ae-113">列舉，因為它們的基礎類型一律是、、、、、 `SByte` `Short` `Integer` `Long` `Byte` `UShort` 、 `UInteger` 或 `ULong`</span><span class="sxs-lookup"><span data-stu-id="c38ae-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="c38ae-114">每個結構都是實值型別，即使它包含參考型別成員也一樣。</span><span class="sxs-lookup"><span data-stu-id="c38ae-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="c38ae-115">基於這個理由，實數值型別（例如 `Char` 和） `Integer` 會由 .NET Framework 結構來執行。</span><span class="sxs-lookup"><span data-stu-id="c38ae-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="c38ae-116">您可以使用保留關鍵字宣告實值型別，例如， `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="c38ae-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="c38ae-117">您也可以使用 `New` 關鍵字來初始化實值型別。</span><span class="sxs-lookup"><span data-stu-id="c38ae-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="c38ae-118">如果類型具有接受參數的函式，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="c38ae-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="c38ae-119">其中一個範例是 <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> 從提供的元件建立新值的函式 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="c38ae-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="c38ae-120">參考類型</span><span class="sxs-lookup"><span data-stu-id="c38ae-120">Reference Types</span></span>  

 <span data-ttu-id="c38ae-121">*參考型*別會儲存其資料的參考。</span><span class="sxs-lookup"><span data-stu-id="c38ae-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="c38ae-122">參考型別包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="c38ae-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="c38ae-123">所有陣列（即使其元素為實數值型別）</span><span class="sxs-lookup"><span data-stu-id="c38ae-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="c38ae-124">類別類型，例如 <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="c38ae-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="c38ae-125">委派</span><span class="sxs-lookup"><span data-stu-id="c38ae-125">Delegates</span></span>  
  
 <span data-ttu-id="c38ae-126">類別是 *參考型別*。</span><span class="sxs-lookup"><span data-stu-id="c38ae-126">A class is a *reference type*.</span></span> <span data-ttu-id="c38ae-127">請注意，每個陣列都是參考型別，即使其成員是實數值型別。</span><span class="sxs-lookup"><span data-stu-id="c38ae-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="c38ae-128">因為每個參考型別都代表基礎 .NET Framework 類別，所以您必須在初始化時使用 [New Operator](../../../language-reference/operators/new-operator.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c38ae-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="c38ae-129">下列語句會初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="c38ae-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="c38ae-130">非類型的元素</span><span class="sxs-lookup"><span data-stu-id="c38ae-130">Elements That Are Not Types</span></span>  

 <span data-ttu-id="c38ae-131">下列程式設計專案不符合型別資格，因為您不能將它們指定為宣告專案的資料類型：</span><span class="sxs-lookup"><span data-stu-id="c38ae-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="c38ae-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="c38ae-132">Namespaces</span></span>  
  
- <span data-ttu-id="c38ae-133">模組</span><span class="sxs-lookup"><span data-stu-id="c38ae-133">Modules</span></span>  
  
- <span data-ttu-id="c38ae-134">事件</span><span class="sxs-lookup"><span data-stu-id="c38ae-134">Events</span></span>  
  
- <span data-ttu-id="c38ae-135">屬性和程式</span><span class="sxs-lookup"><span data-stu-id="c38ae-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="c38ae-136">變數、常數和欄位</span><span class="sxs-lookup"><span data-stu-id="c38ae-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="c38ae-137">使用物件資料類型</span><span class="sxs-lookup"><span data-stu-id="c38ae-137">Working with the Object Data Type</span></span>  

 <span data-ttu-id="c38ae-138">您可以將參考型別或實值型別指派給 `Object` 資料類型的變數。</span><span class="sxs-lookup"><span data-stu-id="c38ae-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="c38ae-139">`Object`變數一律會保存資料的參考，而不是資料本身。</span><span class="sxs-lookup"><span data-stu-id="c38ae-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="c38ae-140">但是，如果您將實值型別指派給 `Object` 變數，它的行為就像它擁有自己的資料一樣。</span><span class="sxs-lookup"><span data-stu-id="c38ae-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="c38ae-141">如需詳細資訊，請參閱 [物件資料類型](../../../language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="c38ae-141">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="c38ae-142">您可以藉 `Object` 由將變數傳遞給 <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> 命名空間類別中的方法，找出變數是否做為參考型別或實值型別 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c38ae-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c38ae-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True`如果變數的內容 `Object` 表示參考型別，則傳回。</span><span class="sxs-lookup"><span data-stu-id="c38ae-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38ae-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c38ae-144">See also</span></span>

- [<span data-ttu-id="c38ae-145">可為 null 的實數值型別</span><span class="sxs-lookup"><span data-stu-id="c38ae-145">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="c38ae-146">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="c38ae-146">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="c38ae-147">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="c38ae-147">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c38ae-148">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="c38ae-148">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="c38ae-149">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="c38ae-149">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="c38ae-150">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="c38ae-150">Data Types</span></span>](index.md)
