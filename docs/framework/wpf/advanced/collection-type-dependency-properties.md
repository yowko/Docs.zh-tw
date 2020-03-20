---
title: 集合類型相依性屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141532"
---
# <a name="collection-type-dependency-properties"></a><span data-ttu-id="e92ac-102">集合類型相依性屬性</span><span class="sxs-lookup"><span data-stu-id="e92ac-102">Collection-Type Dependency Properties</span></span>
<span data-ttu-id="e92ac-103">本主題提供如何實作屬性類型為集合類型之相依性屬性的指引和建議模式。</span><span class="sxs-lookup"><span data-stu-id="e92ac-103">This topic provides guidance and suggested patterns for how to implement a dependency property where the type of the property is a collection type.</span></span>  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a><span data-ttu-id="e92ac-104">實作集合類型相依性屬性</span><span class="sxs-lookup"><span data-stu-id="e92ac-104">Implementing a Collection-Type Dependency Property</span></span>  
 <span data-ttu-id="e92ac-105">對於依賴項屬性，您遵循的實現模式是定義 CLR 屬性包裝器，其中該屬性由<xref:System.Windows.DependencyProperty>識別碼而不是欄位或其他構造支援。</span><span class="sxs-lookup"><span data-stu-id="e92ac-105">For a dependency property in general, the implementation pattern that you follow is that you define a CLR property wrapper, where that property is backed by a <xref:System.Windows.DependencyProperty> identifier rather than a field or other construct.</span></span> <span data-ttu-id="e92ac-106">當您實作集合類型屬性時，您可以遵循此相同的模式。</span><span class="sxs-lookup"><span data-stu-id="e92ac-106">You follow this same pattern when you implement a collection-type property.</span></span> <span data-ttu-id="e92ac-107">但是，每當集合中包含的類型本身是或<xref:System.Windows.DependencyObject><xref:System.Windows.Freezable>派生類時，集合類型屬性都會給模式帶來一些複雜性。</span><span class="sxs-lookup"><span data-stu-id="e92ac-107">However, a collection-type property introduces some complexity to the pattern whenever the type that is contained within the collection is itself a <xref:System.Windows.DependencyObject> or <xref:System.Windows.Freezable> derived class.</span></span>  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a><span data-ttu-id="e92ac-108">初始化超過預設值的集合</span><span class="sxs-lookup"><span data-stu-id="e92ac-108">Initializing the Collection Beyond the Default Value</span></span>  
 <span data-ttu-id="e92ac-109">建立相依性屬性時，未指定屬性預設值為初始欄位值。</span><span class="sxs-lookup"><span data-stu-id="e92ac-109">When you create a dependency property, you do not specify the property default value as the initial field value.</span></span> <span data-ttu-id="e92ac-110">而是透過相依性屬性中繼資料指定預設值。</span><span class="sxs-lookup"><span data-stu-id="e92ac-110">Instead, you specify the default value through the dependency property metadata.</span></span> <span data-ttu-id="e92ac-111">如果屬性是參考類型，則在相依性屬性中繼資料中指定的預設值不是每個執行個體的預設值，而是適用於所有類型執行個體的預設值。</span><span class="sxs-lookup"><span data-stu-id="e92ac-111">If your property is a reference type, the default value specified in dependency property metadata is not a default value per instance; instead it is a default value that applies to all instances of the type.</span></span> <span data-ttu-id="e92ac-112">因此您必須小心不要使用集合屬性中繼資料所定義的單一靜態集合，當成您類型新建執行個體的工作預設值。</span><span class="sxs-lookup"><span data-stu-id="e92ac-112">Therefore you must be careful to not use the singular static collection defined by the collection property metadata as the working default value for newly created instances of your type.</span></span> <span data-ttu-id="e92ac-113">您必須改確定刻意將唯一 (執行個體) 集合的集合值設定為類別建構函式邏輯的一部分。</span><span class="sxs-lookup"><span data-stu-id="e92ac-113">Instead, you must make sure that you deliberately set the collection value to a unique (instance) collection as part of your class constructor logic.</span></span> <span data-ttu-id="e92ac-114">否則會建立意外的單一類別。</span><span class="sxs-lookup"><span data-stu-id="e92ac-114">Otherwise you will have created an unintentional singleton class.</span></span>  
  
 <span data-ttu-id="e92ac-115">請思考一下下列範例。</span><span class="sxs-lookup"><span data-stu-id="e92ac-115">Consider the following example.</span></span> <span data-ttu-id="e92ac-116">示例的以下部分顯示了類`Aquarium`的定義，其中包含具有預設值的缺陷。</span><span class="sxs-lookup"><span data-stu-id="e92ac-116">The following section of the example shows the definition for a class `Aquarium`, which contains a flaw with the default value.</span></span> <span data-ttu-id="e92ac-117">類定義集合類型依賴項屬性`AquariumObjects`，它使用泛型<xref:System.Collections.Generic.List%601>類型與<xref:System.Windows.FrameworkElement>類型約束。</span><span class="sxs-lookup"><span data-stu-id="e92ac-117">The class defines the collection type dependency property `AquariumObjects`, which uses the generic <xref:System.Collections.Generic.List%601> type with a <xref:System.Windows.FrameworkElement> type constraint.</span></span> <span data-ttu-id="e92ac-118">在<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>對依賴項屬性的調用中，中繼資料將預設值建立為新泛型<xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="e92ac-118">In the <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> call for the dependency property, the metadata establishes the default value to be a new generic <xref:System.Collections.Generic.List%601>.</span></span>

> [!WARNING]
> <span data-ttu-id="e92ac-119">以下代碼的行為不正確。</span><span class="sxs-lookup"><span data-stu-id="e92ac-119">The following code does not behave correctly.</span></span>

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 <span data-ttu-id="e92ac-120">不過，如果程式碼保持與範例一致，則單一清單預設值會供 `Aquarium` 的所有執行個體共用。</span><span class="sxs-lookup"><span data-stu-id="e92ac-120">However, if you just left the code as shown, that single list default value is shared for all instances of `Aquarium`.</span></span> <span data-ttu-id="e92ac-121">如果執行下列測試程式碼，它原是要示範如何具現化兩個不同的 `Aquarium` 執行個體，並為它們都新增單一不同的 `Fish`，您會看到令人驚訝的結果︰</span><span class="sxs-lookup"><span data-stu-id="e92ac-121">If you ran the following test code, which is intended to show how you would instantiate two separate `Aquarium` instances and add a single different `Fish` to each of them, you would see a surprising result:</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 <span data-ttu-id="e92ac-122">不是每個集合都有一個計數，而是每個集合都有兩個計數！</span><span class="sxs-lookup"><span data-stu-id="e92ac-122">Instead of each collection having a count of one, each collection has a count of two!</span></span> <span data-ttu-id="e92ac-123">這是因為每個 `Aquarium` 都將自己的 `Fish` 新增至預設值集合，由中繼資料中的單一建構函式呼叫所致，因此在所有執行個體之間共用。</span><span class="sxs-lookup"><span data-stu-id="e92ac-123">This is because each `Aquarium` added its `Fish` to the default value collection, which resulted from a single constructor call in the metadata and is therefore shared between all instances.</span></span> <span data-ttu-id="e92ac-124">這種情況根本就不是您想要的。</span><span class="sxs-lookup"><span data-stu-id="e92ac-124">This situation is almost never what you want.</span></span>  
  
 <span data-ttu-id="e92ac-125">若要修正這個問題，您必須將集合相依性屬性值重設為唯一的執行個體，當成類別建構函式呼叫的一部分。</span><span class="sxs-lookup"><span data-stu-id="e92ac-125">To correct this problem, you must reset the collection dependency property value to a unique instance, as part of the class constructor call.</span></span> <span data-ttu-id="e92ac-126">由於該屬性是唯讀依賴項屬性，因此使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法設置它，使用 僅在類<xref:System.Windows.DependencyPropertyKey>中可訪問的 。</span><span class="sxs-lookup"><span data-stu-id="e92ac-126">Because the property is a read-only dependency property, you use the <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> method to set it, using the <xref:System.Windows.DependencyPropertyKey> that is only accessible within the class.</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 <span data-ttu-id="e92ac-127">現在，如果再次執行相同的測試程式碼，您會看到更符合預期的結果，其中每個 `Aquarium` 都支援自己的唯一集合。</span><span class="sxs-lookup"><span data-stu-id="e92ac-127">Now, if you ran that same test code again, you could see more expected results, where each `Aquarium` supported its own unique collection.</span></span>  
  
 <span data-ttu-id="e92ac-128">如果選擇讓您的集合屬性為可讀寫，則這個模式可能要略加修改。</span><span class="sxs-lookup"><span data-stu-id="e92ac-128">There would be a slight variation on this pattern if you chose to have your collection property be read-write.</span></span> <span data-ttu-id="e92ac-129">在這種情況下，可以從建構函式調用公共集訪問器來執行初始化，該初始化仍將使用公共<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29><xref:System.Windows.DependencyProperty>識別碼調用 set 包裝器中的非鍵簽名。</span><span class="sxs-lookup"><span data-stu-id="e92ac-129">In that case, you could call the public set accessor from the constructor to do the initialization, which would still be calling the nonkey signature of <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> within your set wrapper, using a public <xref:System.Windows.DependencyProperty> identifier.</span></span>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a><span data-ttu-id="e92ac-130">報告集合屬性中的繫結值變更</span><span class="sxs-lookup"><span data-stu-id="e92ac-130">Reporting Binding Value Changes from Collection Properties</span></span>  
 <span data-ttu-id="e92ac-131">本身為相依性屬性的集合屬性不會自動報告其子屬性變更。</span><span class="sxs-lookup"><span data-stu-id="e92ac-131">A collection property that is itself a dependency property does not automatically report changes to its subproperties.</span></span> <span data-ttu-id="e92ac-132">如果您要建立集合繫結，這可以防止繫結報告變更，因而使某些資料繫結案例失效。</span><span class="sxs-lookup"><span data-stu-id="e92ac-132">If you are creating bindings into a collection, this can prevent the binding from reporting changes, thus invalidating some data binding scenarios.</span></span> <span data-ttu-id="e92ac-133">但是，如果使用集合類型<xref:System.Windows.FreezableCollection%601>作為集合類型，則子屬性對集合中包含的元素的更改將正確報告，並且綁定按預期方式工作。</span><span class="sxs-lookup"><span data-stu-id="e92ac-133">However, if you use the collection type <xref:System.Windows.FreezableCollection%601> as your collection type, then subproperty changes to contained elements in the collection are properly reported, and binding works as expected.</span></span>  
  
 <span data-ttu-id="e92ac-134">要在依賴項物件集合中啟用子屬性綁定，請將集合屬性創建<xref:System.Windows.FreezableCollection%601>為類型，該集合的類型約束為任何<xref:System.Windows.DependencyObject>派生類。</span><span class="sxs-lookup"><span data-stu-id="e92ac-134">To enable subproperty binding in a dependency object collection, create the collection property as type <xref:System.Windows.FreezableCollection%601>, with a type constraint for that collection to any <xref:System.Windows.DependencyObject> derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92ac-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e92ac-135">See also</span></span>

- <xref:System.Windows.FreezableCollection%601>
- [<span data-ttu-id="e92ac-136">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="e92ac-136">XAML and Custom Classes for WPF</span></span>](xaml-and-custom-classes-for-wpf.md)
- [<span data-ttu-id="e92ac-137">資料繫結概述</span><span class="sxs-lookup"><span data-stu-id="e92ac-137">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e92ac-138">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="e92ac-138">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="e92ac-139">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="e92ac-139">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="e92ac-140">相依性屬性中繼資料</span><span class="sxs-lookup"><span data-stu-id="e92ac-140">Dependency Property Metadata</span></span>](dependency-property-metadata.md)
