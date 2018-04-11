---
title: 匿名類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 530e21e1595f9bbc3436280418287413e2a48111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-types-visual-basic"></a><span data-ttu-id="5c5dd-102">匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c5dd-102">Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="5c5dd-103">Visual Basic 支援可讓您建立的物件，而不需要撰寫的資料類型的類別定義的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-103">Visual Basic supports anonymous types, which enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="5c5dd-104">編譯器 (Compiler) 會自動幫您建立類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-104">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="5c5dd-105">類別沒有可用的名稱，直接繼承自<xref:System.Object>，且包含您指定在宣告物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-105">The class has no usable name, inherits directly from <xref:System.Object>, and contains the properties you specify in declaring the object.</span></span> <span data-ttu-id="5c5dd-106">未指定資料類型的名稱，因為它指*匿名型別*。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-106">Because the name of the data type is not specified, it is referred to as an *anonymous type*.</span></span>  
  
 <span data-ttu-id="5c5dd-107">下列範例會宣告並建立變數`product`做為具有兩個屬性的匿名型別的執行個體`Name`和`Price`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-107">The following example declares and creates variable `product` as an instance of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 <span data-ttu-id="5c5dd-108">A*查詢運算式*會使用匿名型別結合資料查詢選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-108">A *query expression* uses anonymous types to combine columns of data selected by a query.</span></span> <span data-ttu-id="5c5dd-109">由於您無法預測特定的查詢會選取的資料行，您無法事先定義的結果類型。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-109">You cannot define the type of the result in advance, because you cannot predict the columns a particular query might select.</span></span> <span data-ttu-id="5c5dd-110">匿名類型可讓您撰寫依任何順序選取任意數目的資料行的查詢。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-110">Anonymous types enable you to write a query that selects any number of columns, in any order.</span></span> <span data-ttu-id="5c5dd-111">編譯器會建立比對指定的屬性和指定的順序的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-111">The compiler creates a data type that matches the specified properties and the specified order.</span></span>  
  
 <span data-ttu-id="5c5dd-112">在下列範例中，`products`是一份產品物件每一個都有許多屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-112">In the following examples, `products` is a list of product objects, each of which has many properties.</span></span> <span data-ttu-id="5c5dd-113">變數`namePriceQuery`儲存傳回的查詢，當它執行時，具有兩個屬性的匿名型別的執行個體的集合定義`Name`和`Price`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-113">Variable `namePriceQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 <span data-ttu-id="5c5dd-114">變數`nameQuantityQuery`儲存傳回的查詢，當它執行時，具有兩個屬性的匿名型別的執行個體的集合定義`Name`和`OnHand`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-114">Variable `nameQuantityQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 <span data-ttu-id="5c5dd-115">如需匿名型別為編譯器所建立的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-115">For more information about the code created by the compiler for an anonymous type, see [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5c5dd-116">匿名類型的名稱是編譯器產生，而可能有所不同編譯。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-116">The name of the anonymous type is compiler generated and may vary from compilation to compilation.</span></span> <span data-ttu-id="5c5dd-117">您的程式碼不應該使用或依賴匿名型別的名稱，因為重新編譯專案時，可能會變更名稱。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-117">Your code should not use or rely on the name of an anonymous type because the name might change when a project is recompiled.</span></span>  
  
## <a name="declaring-an-anonymous-type"></a><span data-ttu-id="5c5dd-118">宣告匿名類型</span><span class="sxs-lookup"><span data-stu-id="5c5dd-118">Declaring an Anonymous Type</span></span>  
 <span data-ttu-id="5c5dd-119">匿名型別的執行個體的宣告會使用初始設定式清單來指定類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-119">The declaration of an instance of an anonymous type uses an initializer list to specify the properties of the type.</span></span> <span data-ttu-id="5c5dd-120">當您宣告匿名類型、 不例如方法或事件其他類別項目時，您可以指定只有屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-120">You can specify only properties when you declare an anonymous type, not other class elements such as methods or events.</span></span> <span data-ttu-id="5c5dd-121">在下列範例中，`product1`是有兩個屬性的匿名類型的執行個體：`Name`和`Price`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-121">In the following example, `product1` is an instance of an anonymous type that has two properties: `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 <span data-ttu-id="5c5dd-122">如果您指定屬性為索引鍵屬性時，您可以使用它們來比較兩個匿名型別執行個體相等。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-122">If you designate properties as key properties, you can use them to compare two anonymous type instances for equality.</span></span> <span data-ttu-id="5c5dd-123">不過，您無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-123">However, the values of key properties cannot be changed.</span></span> <span data-ttu-id="5c5dd-124">請參閱本文稍後如需詳細資訊的索引鍵屬性 > 一節。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-124">See the Key Properties section later in this topic for more information.</span></span>  
  
 <span data-ttu-id="5c5dd-125">請注意，宣告匿名類型的執行個體是使用物件初始設定式宣告具名類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="5c5dd-125">Notice that declaring an instance of an anonymous type is like declaring an instance of a named type by using an object initializer:</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 <span data-ttu-id="5c5dd-126">如需指定匿名類型屬性的其他方式的詳細資訊，請參閱[How to： 推斷屬性名稱和匿名類型宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-126">For more information about other ways to specify anonymous type properties, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="5c5dd-127">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="5c5dd-127">Key Properties</span></span>  
 <span data-ttu-id="5c5dd-128">數種基本方式，與非索引鍵屬性不同索引鍵屬性：</span><span class="sxs-lookup"><span data-stu-id="5c5dd-128">Key properties differ from non-key properties in several fundamental ways:</span></span>  
  
-   <span data-ttu-id="5c5dd-129">只有索引鍵屬性的值會比較以判斷兩個執行個體是否相等。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-129">Only the values of key properties are compared in order to determine whether two instances are equal.</span></span>  
  
-   <span data-ttu-id="5c5dd-130">索引鍵屬性的值是唯讀而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-130">The values of key properties are read-only and cannot be changed.</span></span>  
  
-   <span data-ttu-id="5c5dd-131">只有索引鍵屬性值包含編譯器產生的雜湊程式碼演算法，如匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-131">Only key property values are included in the compiler-generated hash code algorithm for an anonymous type.</span></span>  
  
### <a name="equality"></a><span data-ttu-id="5c5dd-132">相等</span><span class="sxs-lookup"><span data-stu-id="5c5dd-132">Equality</span></span>  
 <span data-ttu-id="5c5dd-133">匿名類型的執行個體可以有相同的匿名型別的執行個體才會相等。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-133">Instances of anonymous types can be equal only if they are instances of the same anonymous type.</span></span> <span data-ttu-id="5c5dd-134">編譯器會將兩個執行個體與相同類型的執行個體，若符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="5c5dd-134">The compiler treats two instances as instances of the same type if they meet the following conditions:</span></span>  
  
-   <span data-ttu-id="5c5dd-135">宣告相同的組件。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-135">They are declared in the same assembly.</span></span>  
  
-   <span data-ttu-id="5c5dd-136">其屬性具有相同的名稱相同的推斷型別，並宣告以相同的順序。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-136">Their properties have the same names, the same inferred types, and are declared in the same order.</span></span> <span data-ttu-id="5c5dd-137">名稱比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-137">Name comparisons are not case-sensitive.</span></span>  
  
-   <span data-ttu-id="5c5dd-138">在每個相同的屬性標記為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-138">The same properties in each are marked as key properties.</span></span>  
  
-   <span data-ttu-id="5c5dd-139">每個宣告中的至少一個屬性是索引鍵內容。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-139">At least one property in each declaration is a key property.</span></span>  
  
 <span data-ttu-id="5c5dd-140">匿名型別沒有索引鍵屬性的執行個體等於只有本身。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-140">An instance of an anonymous types that has no key properties is equal only to itself.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 <span data-ttu-id="5c5dd-141">相同匿名類型的兩個執行個體相等的索引鍵屬性的值是否相等。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-141">Two instances of the same anonymous type are equal if the values of their key properties are equal.</span></span> <span data-ttu-id="5c5dd-142">下列範例說明如何測試相等。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-142">The following examples illustrate how equality is tested.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a><span data-ttu-id="5c5dd-143">唯讀的值</span><span class="sxs-lookup"><span data-stu-id="5c5dd-143">Read-Only Values</span></span>  
 <span data-ttu-id="5c5dd-144">無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-144">The values of key properties cannot be changed.</span></span> <span data-ttu-id="5c5dd-145">例如，在`prod8`在前一個範例中，`Name`和`Price`欄位`read-only`，但`OnHand`可以變更。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-145">For example, in `prod8` in the previous example, the `Name` and `Price` fields are `read-only`, but `OnHand` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a><span data-ttu-id="5c5dd-146">從查詢運算式的匿名型別</span><span class="sxs-lookup"><span data-stu-id="5c5dd-146">Anonymous Types from Query Expressions</span></span>  
 <span data-ttu-id="5c5dd-147">查詢運算式不一定需要建立匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-147">Query expressions do not always require the creation of anonymous types.</span></span> <span data-ttu-id="5c5dd-148">如果可能的話，他們會使用現有的類型來保存資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-148">When possible, they use an existing type to hold the column data.</span></span> <span data-ttu-id="5c5dd-149">會發生這種情況是當查詢傳回整筆記錄，從資料來源或只有一個欄位，從每個記錄。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-149">This occurs when the query returns either whole records from the data source, or only one field from each record.</span></span> <span data-ttu-id="5c5dd-150">下列程式碼範例中，`customers`是物件的集合`Customer`類別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-150">In the following code examples, `customers` is a collection of objects of a `Customer` class.</span></span> <span data-ttu-id="5c5dd-151">類別具有許多屬性，而且您可以在查詢結果中，依任何順序包含一或多個。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-151">The class has many properties, and you can include one or more of them in the query result, in any order.</span></span> <span data-ttu-id="5c5dd-152">在前兩個範例中，沒有匿名型別是必要的因為查詢選取的具名類型的項目：</span><span class="sxs-lookup"><span data-stu-id="5c5dd-152">In the first two examples, no anonymous types are required because the queries select elements of named types:</span></span>  
  
-   <span data-ttu-id="5c5dd-153">`custs1`包含字串的集合，因為`cust.Name`是字串。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-153">`custs1` contains a collection of strings, because `cust.Name` is a string.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   <span data-ttu-id="5c5dd-154">`custs2`包含集合`Customer`物件，因為每個項目`customers`是`Customer`查詢所選取物件，且整個項目。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-154">`custs2` contains a collection of `Customer` objects, because each element of `customers` is a `Customer` object, and the whole element is selected by the query.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 <span data-ttu-id="5c5dd-155">不過，適當具名型別並非永遠可用。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-155">However, appropriate named types are not always available.</span></span> <span data-ttu-id="5c5dd-156">您可以選取 客戶名稱和一個用途、 客戶 ID 編號和另一個位置的位址和客戶名稱、 位址，以及協力廠商的訂單記錄。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-156">You might want to select customer names and addresses for one purpose, customer ID numbers and locations for another, and customer names, addresses, and order histories for a third.</span></span> <span data-ttu-id="5c5dd-157">匿名類型可讓您以任何順序選取屬性的任何組合，而第一個宣告新的具名的類型，以保存結果。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-157">Anonymous types enable you to select any combination of properties, in any order, without first declaring a new named type to hold the result.</span></span> <span data-ttu-id="5c5dd-158">相反地，編譯器會建立每次編譯屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-158">Instead, the compiler creates an anonymous type for each compilation of properties.</span></span> <span data-ttu-id="5c5dd-159">下列查詢會選取只在客戶的名稱和 ID 編號從每個`Customer`物件存放至`customers`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-159">The following query selects only the customer's name and ID number from each `Customer` object in `customers`.</span></span> <span data-ttu-id="5c5dd-160">因此，編譯器會建立包含只有這兩個屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-160">Therefore, the compiler creates an anonymous type that contains only those two properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 <span data-ttu-id="5c5dd-161">名稱和資料類型的匿名型別中的屬性都取自的引數`Select`，`cust.Name`和`cust.ID`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-161">Both the names and the data types of the properties in the anonymous type are taken from the arguments to `Select`, `cust.Name` and `cust.ID`.</span></span> <span data-ttu-id="5c5dd-162">匿名型別所建立的查詢中的屬性一定是索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-162">The properties in an anonymous type that is created by a query are always key properties.</span></span> <span data-ttu-id="5c5dd-163">當`custs3`執行下列`For Each`迴圈，結果是具有兩個屬性的匿名類型的執行個體的集合`Name`和`ID`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-163">When `custs3` is executed in the following `For Each` loop, the result is a collection of instances of an anonymous type with two key properties, `Name` and `ID`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 <span data-ttu-id="5c5dd-164">所表示的集合中的項目`custs3`強型別，並瀏覽可用的屬性，並確認其類型，您可以使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-164">The elements in the collection represented by `custs3` are strongly typed, and you can use IntelliSense to navigate through the available properties and to verify their types.</span></span>  
  
 <span data-ttu-id="5c5dd-165">如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-165">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="deciding-whether-to-use-anonymous-types"></a><span data-ttu-id="5c5dd-166">決定是否要使用匿名型別</span><span class="sxs-lookup"><span data-stu-id="5c5dd-166">Deciding Whether to Use Anonymous Types</span></span>  
 <span data-ttu-id="5c5dd-167">當做匿名類別的執行個體建立物件之前，請考慮那是否最佳選項。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-167">Before you create an object as an instance of an anonymous class, consider whether that is the best option.</span></span> <span data-ttu-id="5c5dd-168">例如，如果您想要建立暫存物件來包含相關的資料，而且您不需要其他的欄位和方法，其中可能包含完整的類別，匿名型別會是很好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-168">For example, if you want to create a temporary object to contain related data, and you have no need for other fields and methods that a complete class might contain, an anonymous type is a good solution.</span></span> <span data-ttu-id="5c5dd-169">匿名類型也會很方便的如果您想要每個宣告中，選取不同的屬性，或您想要變更屬性的順序。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-169">Anonymous types are also convenient if you want a different selection of properties for each declaration, or if you want to change the order of the properties.</span></span> <span data-ttu-id="5c5dd-170">不過，如果您的專案包含數個物件具有相同的屬性，以固定的順序，您可以宣告它們更輕鬆地使用具名型別類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-170">However, if your project includes several objects that have the same properties, in a fixed order, you can declare them more easily by using a named type with a class constructor.</span></span> <span data-ttu-id="5c5dd-171">比方說，使用適當的建構函式，它是宣告數個執行個體的工作變得更容易`Product`類別比宣告匿名類型的數個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-171">For example, with an appropriate constructor, it is easier to declare several instances of a `Product` class than it is to declare several instances of an anonymous type.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 <span data-ttu-id="5c5dd-172">具名類型的另一個好處是，編譯器可以攔截的屬性名稱不小心輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-172">Another advantage of named types is that the compiler can catch an accidental mistyping of a property name.</span></span> <span data-ttu-id="5c5dd-173">在上一個範例中， `firstProd2`， `secondProd2`，和`thirdProd2`要作為相同匿名類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-173">In the previous examples, `firstProd2`, `secondProd2`, and `thirdProd2` are intended to be instances of the same anonymous type.</span></span> <span data-ttu-id="5c5dd-174">不過，如果您不小心將宣告`thirdProd2`中的下列方法之一，其類型會是不同的`firstProd2`和`secondProd2`。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-174">However, if you were to accidentally declare `thirdProd2` in one of the following ways, its type would be different from that of `firstProd2` and `secondProd2`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 <span data-ttu-id="5c5dd-175">更重要的是，有一些限制並不適用於具名類型的執行個體的匿名型別的使用。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-175">More importantly, there are limitations on the use of anonymous types that do not apply to instances of named types.</span></span> <span data-ttu-id="5c5dd-176">`firstProd2``secondProd2`，和`thirdProd2`是相同的匿名類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-176">`firstProd2`, `secondProd2`, and `thirdProd2` are instances of the same anonymous type.</span></span> <span data-ttu-id="5c5dd-177">不過，共用的匿名類型的名稱無法使用，不能出現在程式碼中預期的型別名稱的位置。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-177">However, the name for the shared anonymous type is not available and cannot appear where a type name is expected in your code.</span></span> <span data-ttu-id="5c5dd-178">例如，匿名類型無法用來定義方法簽章，若要宣告另一個變數或欄位，或任何類型宣告中。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-178">For example, an anonymous type cannot be used to define a method signature, to declare another variable or field, or in any type declaration.</span></span> <span data-ttu-id="5c5dd-179">如此一來，匿名型別時，不適合您需要在方法之間共用資訊。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-179">As a result, anonymous types are not appropriate when you have to share information across methods.</span></span>  
  
## <a name="an-anonymous-type-definition"></a><span data-ttu-id="5c5dd-180">匿名類型定義</span><span class="sxs-lookup"><span data-stu-id="5c5dd-180">An Anonymous Type Definition</span></span>  
 <span data-ttu-id="5c5dd-181">為了回應執行個體的匿名類型宣告，編譯器會建立新的類別定義，其中包含指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-181">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties.</span></span>  
  
 <span data-ttu-id="5c5dd-182">如果匿名型別包含至少一個索引鍵屬性，定義會覆寫繼承自的三個成員<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-182">If the anonymous type contains at least one key property, the definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="5c5dd-183">程式碼產生的測試相等，以及判斷雜湊碼值會考慮索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-183">The code produced for testing equality and determining the hash code value considers only the key properties.</span></span> <span data-ttu-id="5c5dd-184">如果匿名型別包含任何索引鍵屬性，只有<xref:System.Object.ToString%2A>會覆寫。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-184">If the anonymous type contains no key properties, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="5c5dd-185">明確命名的匿名類型屬性不能與這些產生的方法衝突。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-185">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="5c5dd-186">也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-186">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="5c5dd-187">匿名類型定義，至少有一個索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名類型的類型。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-187">Anonymous type definitions that have at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
 <span data-ttu-id="5c5dd-188">如需建立由編譯器和功能的覆寫方法的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="5c5dd-188">For more information about the code created by the compiler and the functionality of the overridden methods, see [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5dd-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c5dd-189">See Also</span></span>  
 [<span data-ttu-id="5c5dd-190">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="5c5dd-190">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="5c5dd-191">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="5c5dd-191">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="5c5dd-192">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="5c5dd-192">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="5c5dd-193">如何：在匿名類型宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="5c5dd-193">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="5c5dd-194">匿名類型定義</span><span class="sxs-lookup"><span data-stu-id="5c5dd-194">Anonymous Type Definition</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="5c5dd-195">Key</span><span class="sxs-lookup"><span data-stu-id="5c5dd-195">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
