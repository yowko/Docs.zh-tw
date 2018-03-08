---
title: "撰寫自訂屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d3fb814d6b458de90d684a3ac92e22a62e290a9a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="3e127-102">撰寫自訂屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-102">Writing Custom Attributes</span></span>
<span data-ttu-id="3e127-103">若要設計您自己的自訂屬性，並不需要精通很多新概念。</span><span class="sxs-lookup"><span data-stu-id="3e127-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="3e127-104">假如您擅長物件導向的程式設計，且瞭解如何設計類別，那麼您就已經擁有大部分所需的知識。</span><span class="sxs-lookup"><span data-stu-id="3e127-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="3e127-105">自訂屬性基本上是一種直接或間接衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的傳統類別。</span><span class="sxs-lookup"><span data-stu-id="3e127-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e127-106">自訂屬性就像傳統類別一樣，含有儲存和擷取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="3e127-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="3e127-107">正確設計自訂屬性的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3e127-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="3e127-108">套用 AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="3e127-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="3e127-109">宣告屬性類別</span><span class="sxs-lookup"><span data-stu-id="3e127-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="3e127-110">宣告建構函式</span><span class="sxs-lookup"><span data-stu-id="3e127-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="3e127-111">宣告屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="3e127-112">本節會一一說明每個步驟，並於結尾提供 [自訂屬性範例](#cpconcustomattributeexample)。</span><span class="sxs-lookup"><span data-stu-id="3e127-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="3e127-113">套用 AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="3e127-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="3e127-114">自訂屬性宣告的開頭為 **AttributeUsageAttribute**，其定義您某些屬性類別的索引鍵特性。</span><span class="sxs-lookup"><span data-stu-id="3e127-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="3e127-115">例如，您可以指定屬性是否可由其他類別繼承或指定屬性可以套用至哪一個項目。</span><span class="sxs-lookup"><span data-stu-id="3e127-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="3e127-116">下列程式碼片段將示範如何使用 **AttributeUsageAttribute**。</span><span class="sxs-lookup"><span data-stu-id="3e127-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="3e127-117"><xref:System.AttributeUsageAttribute?displayProperty=nameWithType> 有三個建立自訂屬性所需的重要成員：[AttributeTargets](#cpconwritingcustomattributesanchor1)、[Inherited](#cpconwritingcustomattributesanchor2) 及 [AllowMultiple](#cpconwritingcustomattributesanchor3)。</span><span class="sxs-lookup"><span data-stu-id="3e127-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="3e127-118">AttributeTargets 成員</span><span class="sxs-lookup"><span data-stu-id="3e127-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="3e127-119">在上述範例中，指定了 **AttributeTargets.All** ，指出此屬性可以套用到所有程式項目。</span><span class="sxs-lookup"><span data-stu-id="3e127-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="3e127-120">或者，您也可以指定 **AttributeTargets.Class**，指出您的屬性可以套用到類別，或指定 **AttributeTargets.Method**，指出屬性只能套用至方法。</span><span class="sxs-lookup"><span data-stu-id="3e127-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="3e127-121">所有的程式項目都可以用這種方式透過自訂屬性標示為描述。</span><span class="sxs-lookup"><span data-stu-id="3e127-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="3e127-122">您也可以傳遞多個 <xref:System.AttributeTargets>的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e127-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="3e127-123">下列程式碼片段指定自訂屬性可以套用至任何類別或方法。</span><span class="sxs-lookup"><span data-stu-id="3e127-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="3e127-124">Inherited 屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-124">Inherited Property</span></span>  
 <span data-ttu-id="3e127-125"><xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性會指出，衍生自套用您屬性之類別的類別，是否可繼承您的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="3e127-126">此屬性會接受 **true** (預設值) 或 **false** 旗標。</span><span class="sxs-lookup"><span data-stu-id="3e127-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="3e127-127">例如，在下列範例中， `MyAttribute` 的 <xref:System.AttributeUsageAttribute.Inherited%2A> 預設值為 **true**，而 `YourAttribute` 的 <xref:System.AttributeUsageAttribute.Inherited%2A> 值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="3e127-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="3e127-128">兩個屬性接著會套用到基底類別 `MyClass` 中的方法。</span><span class="sxs-lookup"><span data-stu-id="3e127-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="3e127-129">最後，會從基底類別 `YourClass` 繼承類別 `MyClass`。</span><span class="sxs-lookup"><span data-stu-id="3e127-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="3e127-130">此方法 `MyMethod` 顯示 `MyAttribute`，但不是 `YourAttribute`。</span><span class="sxs-lookup"><span data-stu-id="3e127-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="3e127-131">AllowMultiple 屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="3e127-132"><xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> 屬性會指出項目上是否可以有您屬性的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e127-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="3e127-133">如果設定為 **true**，則允許多個執行個體；如果設為 **false** (預設值)，則只允許有一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e127-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="3e127-134">在下列範例中， `MyAttribute` 的 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 預設值為 **false**，而 `YourAttribute` 的值為 **true**。</span><span class="sxs-lookup"><span data-stu-id="3e127-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="3e127-135">當套用這些屬性的多個執行個體時， `MyAttribute` 會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="3e127-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="3e127-136">下列程式碼範例示範有效的 `YourAttribute` 用法和無效的 `MyAttribute` 用法。</span><span class="sxs-lookup"><span data-stu-id="3e127-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="3e127-137">如果兩個 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 屬性和 <xref:System.AttributeUsageAttribute.Inherited%2A> 屬性都設為 **true**，繼承自另一個類別的類別可以繼承屬性，並在同一個子類別中套用同一屬性的另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e127-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="3e127-138">如果 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 設為 **false**，父類別中任何屬性的值，都會被子類別中相同屬性的新執行個體覆寫。</span><span class="sxs-lookup"><span data-stu-id="3e127-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="3e127-139">宣告屬性類別</span><span class="sxs-lookup"><span data-stu-id="3e127-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="3e127-140">在套用 <xref:System.AttributeUsageAttribute>之後，您可以開始定義屬性的細節。</span><span class="sxs-lookup"><span data-stu-id="3e127-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="3e127-141">如下列程式碼所示，屬性類別的宣告看起來類似傳統類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="3e127-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="3e127-142">這個屬性的定義會顯示下列要點：</span><span class="sxs-lookup"><span data-stu-id="3e127-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="3e127-143">屬性類別必須宣告為公用類別。</span><span class="sxs-lookup"><span data-stu-id="3e127-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="3e127-144">依慣例，屬性類別的名稱會以這個字 **Attribute**結尾。</span><span class="sxs-lookup"><span data-stu-id="3e127-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="3e127-145">雖然並非必要，不過建議您遵照這個慣例以提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="3e127-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="3e127-146">當屬性已套用時，要不要包含 Attribute 這個字都可以。</span><span class="sxs-lookup"><span data-stu-id="3e127-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="3e127-147">所有的屬性類別必須直接或間接繼承自 **System.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="3e127-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="3e127-148">在 Microsoft Visual Basic 中，所有自訂屬性的類別都必須有 **AttributeUsageAttribute** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="3e127-149">宣告建構函式</span><span class="sxs-lookup"><span data-stu-id="3e127-149">Declaring Constructors</span></span>  
 <span data-ttu-id="3e127-150">屬性使用建構函式進行初始化的方式，與傳統的類別相同。</span><span class="sxs-lookup"><span data-stu-id="3e127-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="3e127-151">下列程式碼片段說明典型的屬性建構函式。</span><span class="sxs-lookup"><span data-stu-id="3e127-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="3e127-152">這個公用建構函式會接受一個參數並將其值設定為等於成員變數。</span><span class="sxs-lookup"><span data-stu-id="3e127-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="3e127-153">您可以多載建構函式以容納不同的值組合。</span><span class="sxs-lookup"><span data-stu-id="3e127-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="3e127-154">如果您也為自訂的屬性類別定義 [屬性](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) ，您可以在初始化屬性時使用具名和位置參數的組合。</span><span class="sxs-lookup"><span data-stu-id="3e127-154">If you also define a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="3e127-155">通常您會將所有必要的參數定義為位置，而所有選擇性參數則定義為名稱。</span><span class="sxs-lookup"><span data-stu-id="3e127-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="3e127-156">在此情況下，屬性沒有必要的參數就無法初始化。</span><span class="sxs-lookup"><span data-stu-id="3e127-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="3e127-157">所有其他參數皆為選擇性使用。</span><span class="sxs-lookup"><span data-stu-id="3e127-157">All other parameters are optional.</span></span> <span data-ttu-id="3e127-158">請注意在 Visual Basic 中，屬性類別的建構函式不應使用 ParamArray 引數。</span><span class="sxs-lookup"><span data-stu-id="3e127-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="3e127-159">下列程式碼範例示範如何使用選擇性和必要的參數，來套用使用先前建構函示的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="3e127-160">這項作業會假設屬性有一個必要的布林值和一個選擇性的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="3e127-161">宣告屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-161">Declaring Properties</span></span>  
 <span data-ttu-id="3e127-162">如果您想要定義具名的參數或提供簡單的方式，來傳回屬性所儲存的值，請宣告 [屬性](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)。</span><span class="sxs-lookup"><span data-stu-id="3e127-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="3e127-163">屬性的屬性應該宣告為公用實體，並具有將傳回之資料類型的描述。</span><span class="sxs-lookup"><span data-stu-id="3e127-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="3e127-164">定義會保存您屬性值的變數，並將其與 **get** 和 **set** 方法建立關聯。</span><span class="sxs-lookup"><span data-stu-id="3e127-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="3e127-165">下列程式碼範例示範如何在您的屬性中實作簡單的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="3e127-166">自訂屬性範例</span><span class="sxs-lookup"><span data-stu-id="3e127-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="3e127-167">本節包含先前的資訊，並說明如何設計簡單的屬性，記錄某一段程式碼的作者相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e127-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="3e127-168">此範例中的屬性儲存程式設計人員的名字和層級，以及此程式碼是否經過審閱。</span><span class="sxs-lookup"><span data-stu-id="3e127-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="3e127-169">它會使用三個私用變數來儲存要儲存的實際值。</span><span class="sxs-lookup"><span data-stu-id="3e127-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="3e127-170">每個變數都會以取得和設定值的公用屬性來表示。</span><span class="sxs-lookup"><span data-stu-id="3e127-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="3e127-171">最後，建構函式會以兩個必要參數來定義。</span><span class="sxs-lookup"><span data-stu-id="3e127-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="3e127-172">您可以用下列其中一種方式，也就是使用完整名稱 `DeveloperAttribute`，或使用縮寫名稱 `Developer`，來套用此屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="3e127-173">第一個範例示範只套用了必要具名參數的屬性，而第二個範例則示範同時套用了必要和選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e127-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e127-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e127-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="3e127-175">屬性</span><span class="sxs-lookup"><span data-stu-id="3e127-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)
