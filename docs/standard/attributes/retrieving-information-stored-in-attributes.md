---
title: 擷取儲存於屬性中的資訊
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 298ac8eae0a8b125ddf5f1ff35658f426f6b10aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968588"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="b3889-102">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="b3889-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="b3889-103">擷取自訂屬性是一個簡單的程序。</span><span class="sxs-lookup"><span data-stu-id="b3889-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="b3889-104">首先，對想要擷取的屬性宣告執行個體。</span><span class="sxs-lookup"><span data-stu-id="b3889-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="b3889-105">然後，使用 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> 方法將新屬性初始化為所要擷取之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b3889-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="b3889-106">在將新屬性 (Attribute) 初始化之後，只要使用其屬性 (Poperty) 即可取得值。</span><span class="sxs-lookup"><span data-stu-id="b3889-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b3889-107">本文說明如何針對載入到執行內容的程式碼擷取屬性。</span><span class="sxs-lookup"><span data-stu-id="b3889-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="b3889-108">若要對載入僅限反射內容中的程式碼擷取屬性，您必須使用 <xref:System.Reflection.CustomAttributeData> 類別，如以下連結所示：[如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。</span><span class="sxs-lookup"><span data-stu-id="b3889-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="b3889-109">本節說明下列擷取屬性的方式：</span><span class="sxs-lookup"><span data-stu-id="b3889-109">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="b3889-110">擷取單一屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="b3889-111">擷取套用至相同範圍的多個屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="b3889-112">擷取套用至不同範圍的多個屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="b3889-113">擷取單一屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="b3889-114">在下列範例中，`DeveloperAttribute` (上節所述) 會在類別層級上套用至 `MainApp` 類別。</span><span class="sxs-lookup"><span data-stu-id="b3889-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="b3889-115">`GetAttribute` 方法會先使用 **GetCustomAttribute** 來擷取類別層級上的 `DeveloperAttribute` 中所儲存的值，再顯示於主控台。</span><span class="sxs-lookup"><span data-stu-id="b3889-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="b3889-116">此程式會在執行後顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="b3889-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="b3889-117">如果找不到屬性，**GetCustomAttribute**方法會將 `MyAttribute` 初始化為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="b3889-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="b3889-118">此範例會檢查 `MyAttribute` 是否有此類執行個體，並在找不到屬性時通知使用者。</span><span class="sxs-lookup"><span data-stu-id="b3889-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="b3889-119">如果在類別範圍中找不到 `DeveloperAttribute`，會在主控台顯示下列訊息。</span><span class="sxs-lookup"><span data-stu-id="b3889-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="b3889-120">此範例會假設屬性定義在目前的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="b3889-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="b3889-121">如果屬性定義不在目前的命名空間中，請記得匯入屬性定義所在的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b3889-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="b3889-122">擷取套用至相同範圍的多個屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="b3889-123">在上述範例中，要檢查的類別和要尋找的特定屬性都會傳遞至 <xref:System.Attribute.GetCustomAttribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="b3889-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="b3889-124">如果類別層級上只套用一個屬性執行個體，該程式碼可以運作良好。</span><span class="sxs-lookup"><span data-stu-id="b3889-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="b3889-125">不過，如果在相同的類別層級上套用多個屬性執行個體，**GetCustomAttribute** 方法不會擷取所有資訊。</span><span class="sxs-lookup"><span data-stu-id="b3889-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="b3889-126">在相同屬性的多個執行個體都套用至相同範圍的情況下，您可以使用 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> 將屬性的所有執行個體放入陣列。</span><span class="sxs-lookup"><span data-stu-id="b3889-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="b3889-127">例如，如果在相同類別的類別層級上套用 `DeveloperAttribute` 的兩個執行個體，可修改 `GetAttribute` 方法以顯示在兩個屬性中找到的資訊。</span><span class="sxs-lookup"><span data-stu-id="b3889-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="b3889-128">請記住，若要在相同層級上套用多個屬性，屬性必須使用 <xref:System.AttributeUsageAttribute> 中設定為 **true** 的 **AllowMultiple** 屬性來定義。</span><span class="sxs-lookup"><span data-stu-id="b3889-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="b3889-129">下列程式碼範例會示範如何使用 **GetCustomAttributes** 方法，來建立會參考任何指定類別中所有 `DeveloperAttribute` 執行個體的陣列。</span><span class="sxs-lookup"><span data-stu-id="b3889-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="b3889-130">所有屬性的值隨即顯示在主控台。</span><span class="sxs-lookup"><span data-stu-id="b3889-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="b3889-131">如果找不到任何屬性，此程式碼會警示使用者。</span><span class="sxs-lookup"><span data-stu-id="b3889-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="b3889-132">否則，`DeveloperAttribute` 的兩個執行個體中所包含的資訊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="b3889-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="b3889-133">擷取套用至不同範圍的多個屬性執行個體</span><span class="sxs-lookup"><span data-stu-id="b3889-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="b3889-134"><xref:System.Attribute.GetCustomAttributes%2A> 和 <xref:System.Attribute.GetCustomAttribute%2A> 方法不會搜尋整個類別，然後傳回該類別中屬性的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="b3889-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="b3889-135">而會一次只搜尋一個指定的方法或成員。</span><span class="sxs-lookup"><span data-stu-id="b3889-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="b3889-136">如果您有每個成員都套用相同屬性的類別，並想要擷取所有套用至那些成員的屬性值，就必須將每個方法或成員個別提供給 **GetCustomAttributes** 和 **GetCustomAttribute**。</span><span class="sxs-lookup"><span data-stu-id="b3889-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="b3889-137">下列程式碼範例會將類別視為參數，並在類別層級和該類別的每一個方法搜尋 `DeveloperAttribute` (先前所定義)。</span><span class="sxs-lookup"><span data-stu-id="b3889-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="b3889-138">如果在方法層級或類別層級上找不到任何 `DeveloperAttribute` 的執行個體，`GetAttribute` 會通知使用者找不到任何屬性，並顯示不包含該屬性的方法或類別名稱。</span><span class="sxs-lookup"><span data-stu-id="b3889-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="b3889-139">如果找到屬性，會在主控台顯示 `Name`、`Level` 及 `Reviewed` 欄位。</span><span class="sxs-lookup"><span data-stu-id="b3889-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="b3889-140">您可以使用 <xref:System.Type> 類別的成員來取得所傳遞類別中的個別方法和成員。</span><span class="sxs-lookup"><span data-stu-id="b3889-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="b3889-141">此範例會先查詢 **Type** 物件以取得類別層級的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="b3889-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="b3889-142">接著，它會使用 <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> 以將所有方法的執行個體置入 <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> 物件的陣列，以擷取方法層級的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="b3889-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="b3889-143">您也可以使用 <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> 方法來檢查屬性層級上的屬性，或使用 <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> 來檢查建構函式層級上的屬性。</span><span class="sxs-lookup"><span data-stu-id="b3889-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3889-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3889-144">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b3889-145">屬性</span><span class="sxs-lookup"><span data-stu-id="b3889-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
