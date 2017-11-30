---
title: "擷取儲存於屬性中的資訊"
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
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="99d9f-102">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="99d9f-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="99d9f-103">擷取自訂屬性是簡單的程序。</span><span class="sxs-lookup"><span data-stu-id="99d9f-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="99d9f-104">首先，宣告您想要擷取之屬性的執行個體。</span><span class="sxs-lookup"><span data-stu-id="99d9f-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="99d9f-105">然後，使用<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>方法來初始化新的屬性，為您想要擷取之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="99d9f-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="99d9f-106">一旦完成初始化新的屬性，您只要使用其屬性以取得的值。</span><span class="sxs-lookup"><span data-stu-id="99d9f-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99d9f-107">本主題描述如何擷取屬性的執行內容所載入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="99d9f-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="99d9f-108">若要擷取的程式碼載入至僅限反映的內容屬性，您必須使用<xref:System.Reflection.CustomAttributeData>類別，如中所示[如何： 載入組件放入 Reflection-Only 內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。</span><span class="sxs-lookup"><span data-stu-id="99d9f-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="99d9f-109">本章節描述下列方式來擷取屬性：</span><span class="sxs-lookup"><span data-stu-id="99d9f-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="99d9f-110">擷取屬性的單一執行個體</span><span class="sxs-lookup"><span data-stu-id="99d9f-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="99d9f-111">擷取多個執行個體的屬性套用至相同的範圍</span><span class="sxs-lookup"><span data-stu-id="99d9f-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="99d9f-112">擷取多個執行個體的屬性套用至不同的範圍</span><span class="sxs-lookup"><span data-stu-id="99d9f-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="99d9f-113">擷取屬性的單一執行個體</span><span class="sxs-lookup"><span data-stu-id="99d9f-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="99d9f-114">在下列範例中， `DeveloperAttribute` （如上一節中所述） 套用至`MainApp`類別層級上的類別。</span><span class="sxs-lookup"><span data-stu-id="99d9f-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="99d9f-115">`GetAttribute`方法會使用**GetCustomAttribute**擷取中所儲存值`DeveloperAttribute`類別層級之後，它們顯示在主控台上。</span><span class="sxs-lookup"><span data-stu-id="99d9f-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="99d9f-116">此程式會顯示下列文字時執行。</span><span class="sxs-lookup"><span data-stu-id="99d9f-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="99d9f-117">如果找不到屬性， **GetCustomAttribute**方法初始化`MyAttribute`為 null 值。</span><span class="sxs-lookup"><span data-stu-id="99d9f-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="99d9f-118">這個範例會檢查`MyAttribute`這類執行個體，並通知使用者，如果不找到任何屬性。</span><span class="sxs-lookup"><span data-stu-id="99d9f-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="99d9f-119">如果`DeveloperAttribute`找不到在類別範圍中，下列訊息顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="99d9f-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="99d9f-120">這個範例會假設屬性定義為目前的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="99d9f-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="99d9f-121">請記住，如果不是目前的命名空間中，將屬性定義的所在的命名空間匯入。</span><span class="sxs-lookup"><span data-stu-id="99d9f-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="99d9f-122">擷取多個執行個體的屬性套用至相同的範圍</span><span class="sxs-lookup"><span data-stu-id="99d9f-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="99d9f-123">在上述範例中，若要檢查的類別與要尋找特定的屬性會傳遞至<xref:System.Attribute.GetCustomAttribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="99d9f-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="99d9f-124">該程式碼可以運作良好如果只有一個執行個體的屬性會套用至類別層級。</span><span class="sxs-lookup"><span data-stu-id="99d9f-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="99d9f-125">不過，如果多個執行個體的屬性會在相同的類別層級，套用**GetCustomAttribute**方法不會擷取所有的資訊。</span><span class="sxs-lookup"><span data-stu-id="99d9f-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="99d9f-126">在多個執行個體相同的屬性會套用至相同範圍的情況，您可以使用<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>將放入陣列屬性的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="99d9f-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="99d9f-127">比方說，如果兩個執行個體`DeveloperAttribute`相同類別的類別層級上套用`GetAttribute`方法可以修改以顯示這兩個屬性中找到的資訊。</span><span class="sxs-lookup"><span data-stu-id="99d9f-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="99d9f-128">請記住，在相同的層級上套用多個屬性的屬性都必須定義**AllowMultiple**屬性設定為**true**中<xref:System.AttributeUsageAttribute>。</span><span class="sxs-lookup"><span data-stu-id="99d9f-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="99d9f-129">下列程式碼範例示範如何使用**GetCustomAttributes**方法來建立陣列所參考的所有執行個體`DeveloperAttribute`在任何指定的類別。</span><span class="sxs-lookup"><span data-stu-id="99d9f-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="99d9f-130">所有屬性的值隨即顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="99d9f-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="99d9f-131">如果找不到任何屬性，此程式碼會提醒使用者。</span><span class="sxs-lookup"><span data-stu-id="99d9f-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="99d9f-132">否則，所包含的資訊中的兩個執行個體`DeveloperAttribute`隨即出現。</span><span class="sxs-lookup"><span data-stu-id="99d9f-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="99d9f-133">擷取多個執行個體的屬性套用至不同的範圍</span><span class="sxs-lookup"><span data-stu-id="99d9f-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="99d9f-134"><xref:System.Attribute.GetCustomAttributes%2A>和<xref:System.Attribute.GetCustomAttribute%2A>方法不搜尋整個類別，並傳回該類別中的所有執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="99d9f-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="99d9f-135">相反地，它們會一次搜尋只能有一個指定的方法或成員。</span><span class="sxs-lookup"><span data-stu-id="99d9f-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="99d9f-136">如果您擁有的類別具有相同的屬性套用至每個成員，而且您想要擷取套用至這些成員的所有屬性的值，您必須提供每個方法或成員為個別**GetCustomAttributes**和**GetCustomAttribute**。</span><span class="sxs-lookup"><span data-stu-id="99d9f-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="99d9f-137">下列程式碼範例會採用做為參數的類別，並搜尋`DeveloperAttribute`（已定義的先前） 和每個個別的方法，該類別的類別層級上。</span><span class="sxs-lookup"><span data-stu-id="99d9f-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="99d9f-138">如果沒有執行個體的`DeveloperAttribute`方法層級或類別層級上找到`GetAttribute`方法通知使用者，找不到任何屬性，並顯示方法或類別不包含屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="99d9f-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="99d9f-139">如果找到屬性， `Name`， `Level`，和`Reviewed`欄位會顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="99d9f-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="99d9f-140">您可以使用的成員<xref:System.Type>傳遞的類別中取得的個別方法和成員的類別。</span><span class="sxs-lookup"><span data-stu-id="99d9f-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="99d9f-141">下列範例會先查詢**類型**取得類別層級的屬性資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="99d9f-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="99d9f-142">接著，它會使用<xref:System.Type.GetMethods%2A?displayProperty=nameWithType>放置成陣列的所有方法的執行個體<xref:System.Reflection.MemberInfo?displayProperty=nameWithType>擷取的方法層級的屬性資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="99d9f-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="99d9f-143">您也可以使用<xref:System.Type.GetProperties%2A?displayProperty=nameWithType>方法來檢查屬性層級上的屬性或<xref:System.Type.GetConstructors%2A?displayProperty=nameWithType>檢查建構函式層級上的屬性。</span><span class="sxs-lookup"><span data-stu-id="99d9f-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d9f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99d9f-144">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="99d9f-145">屬性</span><span class="sxs-lookup"><span data-stu-id="99d9f-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
