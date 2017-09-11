---
title: "集合初始設定式 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CollectionInitializer
dev_langs:
- VB
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 72ca6506d0bd867efa60ba73ecda72c32def129e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="collection-initializers-visual-basic"></a><span data-ttu-id="d2ac6-102">集合初始設定式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2ac6-102">Collection Initializers (Visual Basic)</span></span>
<span data-ttu-id="d2ac6-103">「集合初始設定式」提供簡短的語法，以讓您建立集合，並填入一組初始值。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-103">*Collection initializers* provide a shortened syntax that enables you to create a collection and populate it with an initial set of values.</span></span> <span data-ttu-id="d2ac6-104">當您透過一組已知值來建立集合時，集合初始設定式十分有用，例如，一份功能表選項或類別清單、一組初始數值、一份日期或月份名稱這類靜態字串清單，或用於驗證的這類省市清單的地理位置。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-104">Collection initializers are useful when you are creating a collection from a set of known values, for example, a list of menu options or categories, an initial set of numeric values, a static list of strings such as day or month names, or geographic locations such as a list of states that is used for validation.</span></span>  
  
 <span data-ttu-id="d2ac6-105">如需集合的詳細資訊，請參閱[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-105">For more information about collections, see [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).</span></span>  
  
 <span data-ttu-id="d2ac6-106">您可以使用後面接著大括弧 (`{}`) 的 `From` 關鍵字，來識別集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-106">You identify a collection initializer by using the `From` keyword followed by braces (`{}`).</span></span> <span data-ttu-id="d2ac6-107">這類似[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)中所述的陣列常值語法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-107">This is similar to the array literal syntax that is described in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span> <span data-ttu-id="d2ac6-108">下列範例顯示使用集合初始設定式建立集合的各種方式。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-108">The following examples show various ways to use collection initializers to create collections.</span></span>  
  
 <span data-ttu-id="d2ac6-109">[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-109">[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2ac6-110">C# 也提供集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-110">C# also provides collection initializers.</span></span> <span data-ttu-id="d2ac6-111">C# 集合初始設定式所提供的功能與 Visual Basic 集合初始設定式相同。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-111">C# collection initializers provide the same functionality as Visual Basic collection initializers.</span></span> <span data-ttu-id="d2ac6-112">如需 C# 集合初始設定式的詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-112">For more information about C# collection initializers, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ac6-113">語法</span><span class="sxs-lookup"><span data-stu-id="d2ac6-113">Syntax</span></span>  
 <span data-ttu-id="d2ac6-114">集合初始設定式包含逗號分隔值清單，而這些值以大括弧 (`{}`) 括住而且前面加上 `From` 關鍵字，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-114">A collection initializer consists of a list of comma-separated values that are enclosed in braces (`{}`), preceded by the `From` keyword, as shown in the following code.</span></span>  
  
 <span data-ttu-id="d2ac6-115">[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-115">[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]</span></span>  
  
 <span data-ttu-id="d2ac6-116">當您建立 <xref:System.Collections.Generic.List%601> 或 <xref:System.Collections.Generic.Dictionary%602> 這類集合時，必須在集合初始設定式之前提供集合類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-116">When you create a collection, such as a <xref:System.Collections.Generic.List%601> or a <xref:System.Collections.Generic.Dictionary%602>, you must supply the collection type before the collection initializer, as shown in the following code.</span></span>  
  
 <span data-ttu-id="d2ac6-117">[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-117">[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2ac6-118">您無法合併使用集合初始設定式與物件初始設定式來初始化相同的集合物件。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-118">You cannot combine both a collection initializer and an object initializer to initialize the same collection object.</span></span> <span data-ttu-id="d2ac6-119">您可以使用物件初始設定式來初始化集合初始設定式中的物件。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-119">You can use object initializers to initialize objects in a collection initializer.</span></span>  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a><span data-ttu-id="d2ac6-120">使用集合初始設定式來建立集合</span><span class="sxs-lookup"><span data-stu-id="d2ac6-120">Creating a Collection by Using a Collection Intializer</span></span>  
 <span data-ttu-id="d2ac6-121">當您使用集合初始設定式建立集合時，集合初始設定式中所提供的每個值都會傳遞給集合的適當 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-121">When you create a collection by using a collection initializer, each value that is supplied in the collection initializer is passed to the appropriate `Add` method of the collection.</span></span> <span data-ttu-id="d2ac6-122">例如，如果您使用集合初始設定式建立 <xref:System.Collections.Generic.List%601>，則會將集合初始設定式中的每個字串值傳遞給 <xref:System.Collections.Generic.List%601.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-122">For example, if you create a <xref:System.Collections.Generic.List%601> by using a collection initializer, each string value in the collection initializer is passed to the <xref:System.Collections.Generic.List%601.Add%2A> method.</span></span> <span data-ttu-id="d2ac6-123">如果您想要使用集合初始設定式建立集合，則指定的類型必須是有效的集合類型。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-123">If you want to create a collection by using a collection initializer, the specified type must be valid collection type.</span></span> <span data-ttu-id="d2ac6-124">有效集合類型的範例包括可實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或繼承 <xref:System.Collections.CollectionBase> 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-124">Examples of valid collection types include classes that implement the <xref:System.Collections.Generic.IEnumerable%601> interface or inherit the <xref:System.Collections.CollectionBase> class.</span></span> <span data-ttu-id="d2ac6-125">指定的類型也必須公開符合下列準則的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-125">The specified type must also expose an `Add` method that meets the following criteria.</span></span>  
  
-   <span data-ttu-id="d2ac6-126">`Add` 方法必須可從將在其中呼叫集合初始設定式的範圍使用。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-126">The `Add` method must be available from the scope in which the collection initializer is being called.</span></span> <span data-ttu-id="d2ac6-127">如果您在可存取集合之非公開方法的情況下使用集合初始設定式，則 `Add` 方法不一定要是公開的。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-127">The `Add` method does not have to be public if you are using the collection initializer in a scenario where non-public methods of the collection can be accessed.</span></span>  
  
-   <span data-ttu-id="d2ac6-128">`Add` 方法必須是集合類別的執行個體成員或 `Shared` 成員或是擴充方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-128">The `Add` method must be an instance member or `Shared` member of the collection class, or an extension method.</span></span>  
  
-   <span data-ttu-id="d2ac6-129">根據多載解析規則，`Add` 方法必須要符合集合初始設定式中所提供的類型。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-129">An `Add` method must exist that can be matched, based on overload resolution rules, to the types that are supplied in the collection initializer.</span></span>  
  
 <span data-ttu-id="d2ac6-130">例如，下列程式碼範例示範如何使用集合初始設定式，來建立 `List(Of Customer)` 集合。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-130">For example, the following code example shows how to create a `List(Of Customer)` collection by using a collection initializer.</span></span> <span data-ttu-id="d2ac6-131">程式碼執行時，每個 `Customer` 物件都會傳遞給泛型清單的 `Add(Customer)` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-131">When the code is run, each `Customer` object is passed to the `Add(Customer)` method of the generic list.</span></span>  
  
 <span data-ttu-id="d2ac6-132">[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-132">[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]</span></span>  
  
 <span data-ttu-id="d2ac6-133">下列程式碼範例示範未使用集合初始設定式的對等程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-133">The following code example shows equivalent code that does not use a collection initializer.</span></span>  
  
 <span data-ttu-id="d2ac6-134">[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-134">[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]</span></span>  
  
 <span data-ttu-id="d2ac6-135">如果集合的 `Add` 方法具有與 `Customer` 物件建構函式相符的參數，則可以將 `Add` 方法的參數值巢狀在集合初始設定式內，如下節所述。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-135">If the collection has an `Add` method that has parameters that match the constructor for the `Customer` object, you could nest parameter values for the `Add` method within collection initializers, as discussed in the next section.</span></span> <span data-ttu-id="d2ac6-136">如果集合沒有這類 `Add` 方法，您可以建立此方法作為擴充方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-136">If the collection does not have such an `Add` method, you can create one as an extension method.</span></span> <span data-ttu-id="d2ac6-137">如需如何建立 `Add` 方法作為集合之擴充方法的範例，請參閱[如何：建立集合初始設定式所使用的 Add 擴充方法](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-137">For an example of how to create an `Add` method as an extension method for a collection, see [How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).</span></span> <span data-ttu-id="d2ac6-138">如需如何建立可與集合初始設定式搭配使用之自訂集合的範例，請參閱[如何：建立集合初始設定式所使用的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-138">For an example of how to create a custom collection that can be used with a collection initializer, see [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).</span></span>  
  
## <a name="nesting-collection-initializers"></a><span data-ttu-id="d2ac6-139">巢狀集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="d2ac6-139">Nesting Collection Initializers</span></span>  
 <span data-ttu-id="d2ac6-140">您可以將值巢狀在集合初始設定式內，以識別所建立集合之 `Add` 方法的特定多載。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-140">You can nest values within a collection initializer to identify a specific overload of an `Add` method for the collection that is being created.</span></span> <span data-ttu-id="d2ac6-141">傳遞給 `Add` 方法的值必須以逗號區隔，並用大括弧 (`{}`) 括住，就像在陣列常值或集合初始設定式中一樣。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-141">The values passed to the `Add` method must be separated by commas and enclosed in braces (`{}`), like you would do in an array literal or collection initializer.</span></span>  
  
 <span data-ttu-id="d2ac6-142">當您使用巢狀值來建立集合時，巢狀值清單的每個項目都會傳遞為符合項目類型之 `Add` 方法的引數。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-142">When you create a collection by using nested values, each element of the nested value list is passed as an argument to the `Add` method that matches the element types.</span></span> <span data-ttu-id="d2ac6-143">例如，下列程式碼範例會建立 <xref:System.Collections.Generic.Dictionary%602>其中，索引鍵的類型為 `Integer`，而值的類型為 `String`。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-143">For example, the following code example creates a <xref:System.Collections.Generic.Dictionary%602> in which the keys are of type `Integer` and the values are of type `String`.</span></span> <span data-ttu-id="d2ac6-144">每個巢狀值清單都會對應到 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-144">Each of the nested value lists is matched to the <xref:System.Collections.Generic.Dictionary%602.Add%2A> method for the `Dictionary`.</span></span>  
  
 <span data-ttu-id="d2ac6-145">[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-145">[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]</span></span>  
  
 <span data-ttu-id="d2ac6-146">先前的程式碼範例等同於下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-146">The previous code example is equivalent to the following code.</span></span>  
  
 <span data-ttu-id="d2ac6-147">[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="d2ac6-147">[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]</span></span>  
  
 <span data-ttu-id="d2ac6-148">只會將第一層巢狀層的巢狀值清單傳送至集合類型的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-148">Only nested value lists from the first level of nesting are sent to the `Add` method for the collection type.</span></span> <span data-ttu-id="d2ac6-149">更深入的巢狀層會視為陣列常值，而且巢狀值清單不會對應到任何集合的 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-149">Deeper levels of nesting are treated as array literals and the nested value lists are not matched to the `Add` method of any collection.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="d2ac6-150">相關主題</span><span class="sxs-lookup"><span data-stu-id="d2ac6-150">Related Topics</span></span>  
  
|<span data-ttu-id="d2ac6-151">標題</span><span class="sxs-lookup"><span data-stu-id="d2ac6-151">Title</span></span>|<span data-ttu-id="d2ac6-152">說明</span><span class="sxs-lookup"><span data-stu-id="d2ac6-152">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="d2ac6-153">如何：建立集合初始設定式所使用的 Add 擴充方法</span><span class="sxs-lookup"><span data-stu-id="d2ac6-153">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|<span data-ttu-id="d2ac6-154">示範如何建立稱為 `Add` 的擴充方法，以用來將集合初始設定式中的值填入集合。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-154">Shows how to create an extension method called `Add` that can be used to populate a collection with values from a collection initializer.</span></span>|  
|[<span data-ttu-id="d2ac6-155">如何：建立集合初始設定式所使用的集合</span><span class="sxs-lookup"><span data-stu-id="d2ac6-155">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|<span data-ttu-id="d2ac6-156">示範如何將 `Add` 方法包括在可實作 `IEnumerable` 的集合類別中，以啟用集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="d2ac6-156">Shows how to enable use of a collection initializer by including an `Add` method in a collection class that implements `IEnumerable`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2ac6-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2ac6-157">See Also</span></span>  
 <span data-ttu-id="d2ac6-158">[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-158">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
 <span data-ttu-id="d2ac6-159">[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-159">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
 <span data-ttu-id="d2ac6-160">[物件初始設定式：具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-160">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
 <span data-ttu-id="d2ac6-161">[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-161">[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
 <span data-ttu-id="d2ac6-162">[自動實作的屬性](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-162">[Auto-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
 <span data-ttu-id="d2ac6-163">[如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-163">[How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) </span></span>  
 <span data-ttu-id="d2ac6-164">[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-164">[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
 <span data-ttu-id="d2ac6-165">[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-165">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
 <span data-ttu-id="d2ac6-166">[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d2ac6-166">[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
 [<span data-ttu-id="d2ac6-167">如何：建立項目清單</span><span class="sxs-lookup"><span data-stu-id="d2ac6-167">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)

