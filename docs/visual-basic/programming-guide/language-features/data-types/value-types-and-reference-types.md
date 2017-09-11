---
title: "實值型別和參考型別 |Microsoft 文件"
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
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
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
ms.openlocfilehash: 8136f58b2e7fce15e959e04b84b05f64d078d662
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="9a264-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="9a264-102">Value Types and Reference Types</span></span>
<span data-ttu-id="9a264-103">在 Visual Basic 中的資料型別會實作其分類為基礎。</span><span class="sxs-lookup"><span data-stu-id="9a264-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="9a264-104">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可依特定類型的變數是否儲存自己的資料或資料指標分類資料型別。</span><span class="sxs-lookup"><span data-stu-id="9a264-104">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="9a264-105">如果它自己的資料會儲存為*實值型別*; 如果它是的記憶體中其他位置的資料會保留指標*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="9a264-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="9a264-106">實值類型</span><span class="sxs-lookup"><span data-stu-id="9a264-106">Value Types</span></span>  
 <span data-ttu-id="9a264-107">資料型別是*實值型別*它存放在自己的記憶體配置中的資料。</span><span class="sxs-lookup"><span data-stu-id="9a264-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="9a264-108">實值型別包括︰</span><span class="sxs-lookup"><span data-stu-id="9a264-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="9a264-109">所有的數值資料類型</span><span class="sxs-lookup"><span data-stu-id="9a264-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="9a264-110">`Boolean`、`Char` 和 `Date`</span><span class="sxs-lookup"><span data-stu-id="9a264-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="9a264-111">所有的結構，即使它們的成員是參考型別</span><span class="sxs-lookup"><span data-stu-id="9a264-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="9a264-112">列舉型別，因為其基礎型別永遠為`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或`ULong`</span><span class="sxs-lookup"><span data-stu-id="9a264-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="9a264-113">每個結構是實值型別，即使它包含參考型別成員。</span><span class="sxs-lookup"><span data-stu-id="9a264-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="9a264-114">基於這個理由，值型別，例如`Char`和`Integer`由.NET Framework 結構。</span><span class="sxs-lookup"><span data-stu-id="9a264-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="9a264-115">您可以使用的保留的關鍵字，例如，宣告實值型別`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="9a264-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="9a264-116">您也可以使用`New`關鍵字初始化實值型別。</span><span class="sxs-lookup"><span data-stu-id="9a264-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="9a264-117">這是特別有用，如果型別參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="9a264-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="9a264-118">這個範例是<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`值從提供的部分。</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29></span><span class="sxs-lookup"><span data-stu-id="9a264-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="9a264-119">參考類型</span><span class="sxs-lookup"><span data-stu-id="9a264-119">Reference Types</span></span>  
 <span data-ttu-id="9a264-120">A*參考型別*包含保存資料的另一個記憶體位置的指標。</span><span class="sxs-lookup"><span data-stu-id="9a264-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="9a264-121">參考型別包括︰</span><span class="sxs-lookup"><span data-stu-id="9a264-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="9a264-122">所有的陣列，即使其元素為實值類型</span><span class="sxs-lookup"><span data-stu-id="9a264-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="9a264-123">類別類型例如<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="9a264-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="9a264-124">委派</span><span class="sxs-lookup"><span data-stu-id="9a264-124">Delegates</span></span>  
  
 <span data-ttu-id="9a264-125">類別是*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="9a264-125">A class is a *reference type*.</span></span> <span data-ttu-id="9a264-126">基於這個理由，參考型別例如`Object`和`String`支援[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別。</span><span class="sxs-lookup"><span data-stu-id="9a264-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes.</span></span> <span data-ttu-id="9a264-127">請注意每個陣列是參考型別，即使其成員都是實值型別。</span><span class="sxs-lookup"><span data-stu-id="9a264-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="9a264-128">由於每個參考型別代表基礎的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字時將它初始化。</span><span class="sxs-lookup"><span data-stu-id="9a264-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="9a264-129">下列陳述式中初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="9a264-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="9a264-130">不是類型的項目</span><span class="sxs-lookup"><span data-stu-id="9a264-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="9a264-131">下列的程式設計項目不會限定為型別，因為您無法將它們指定為資料類型的宣告的項目︰</span><span class="sxs-lookup"><span data-stu-id="9a264-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="9a264-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="9a264-132">Namespaces</span></span>  
  
-   <span data-ttu-id="9a264-133">模組</span><span class="sxs-lookup"><span data-stu-id="9a264-133">Modules</span></span>  
  
-   <span data-ttu-id="9a264-134">事件</span><span class="sxs-lookup"><span data-stu-id="9a264-134">Events</span></span>  
  
-   <span data-ttu-id="9a264-135">屬性和程序</span><span class="sxs-lookup"><span data-stu-id="9a264-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="9a264-136">變數、 常數和欄位</span><span class="sxs-lookup"><span data-stu-id="9a264-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="9a264-137">使用物件資料類型</span><span class="sxs-lookup"><span data-stu-id="9a264-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="9a264-138">您可以將參考類型或實值型別指派給變數`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="9a264-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="9a264-139">`Object`變數一律會保留指標的資料，永遠不會將資料本身。</span><span class="sxs-lookup"><span data-stu-id="9a264-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="9a264-140">不過，如果您指派的值型別`Object`變數時，它就會當做它會保留它自己的資料。</span><span class="sxs-lookup"><span data-stu-id="9a264-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="9a264-141">如需詳細資訊，請參閱[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9a264-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="9a264-142">您可以找出是否`Object`變數做為參考類型或實值型別傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別<xref:Microsoft.VisualBasic?displayProperty=fullName>命名空間。</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.Information> </xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="9a264-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="9a264-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>傳回`True`如果內容`Object`變數代表參考型別。</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9a264-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a264-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a264-144">See Also</span></span>  
 <span data-ttu-id="9a264-145">[可為 null 的實值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="9a264-145">[Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="9a264-146"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="9a264-146"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="9a264-147"> [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9a264-147"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="9a264-148"> [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9a264-148"> [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="9a264-149"> [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="9a264-149"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="9a264-150"> [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="9a264-150"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
