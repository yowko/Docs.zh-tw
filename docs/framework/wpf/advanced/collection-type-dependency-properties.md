---
title: "集合類型相依性屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e572bf7d404d0d824d3127789190ce81d4c98998
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="collection-type-dependency-properties"></a><span data-ttu-id="0d7bc-102">集合類型相依性屬性</span><span class="sxs-lookup"><span data-stu-id="0d7bc-102">Collection-Type Dependency Properties</span></span>
<span data-ttu-id="0d7bc-103">本主題提供如何實作屬性類型為集合類型之相依性屬性的指引和建議模式。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-103">This topic provides guidance and suggested patterns for how to implement a dependency property where the type of the property is a collection type.</span></span>  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a><span data-ttu-id="0d7bc-104">實作集合類型相依性屬性</span><span class="sxs-lookup"><span data-stu-id="0d7bc-104">Implementing a Collection-Type Dependency Property</span></span>  
 <span data-ttu-id="0d7bc-105">相依性屬性的一般實作模式所執行的是您定義[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性的包裝函式，其中該屬性受到<xref:System.Windows.DependencyProperty>識別項而不是欄位或其他建構。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-105">For a dependency property in general, the implementation pattern that you follow is that you define a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrapper, where that property is backed by a <xref:System.Windows.DependencyProperty> identifier rather than a field or other construct.</span></span> <span data-ttu-id="0d7bc-106">當您實作集合類型屬性時，您可以遵循此相同的模式。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-106">You follow this same pattern when you implement a collection-type property.</span></span> <span data-ttu-id="0d7bc-107">不過，會是集合型別屬性增添少許複雜性模式，只要包含在集合的型別本身<xref:System.Windows.DependencyObject>或<xref:System.Windows.Freezable>衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-107">However, a collection-type property introduces some complexity to the pattern whenever the type that is contained within the collection is itself a <xref:System.Windows.DependencyObject> or <xref:System.Windows.Freezable> derived class.</span></span>  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a><span data-ttu-id="0d7bc-108">初始化超過預設值的集合</span><span class="sxs-lookup"><span data-stu-id="0d7bc-108">Initializing the Collection Beyond the Default Value</span></span>  
 <span data-ttu-id="0d7bc-109">建立相依性屬性時，未指定屬性預設值為初始欄位值。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-109">When you create a dependency property, you do not specify the property default value as the initial field value.</span></span> <span data-ttu-id="0d7bc-110">而是透過相依性屬性中繼資料指定預設值。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-110">Instead, you specify the default value through the dependency property metadata.</span></span> <span data-ttu-id="0d7bc-111">如果屬性是參考類型，則在相依性屬性中繼資料中指定的預設值不是每個執行個體的預設值，而是適用於所有類型執行個體的預設值。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-111">If your property is a reference type, the default value specified in dependency property metadata is not a default value per instance; instead it is a default value that applies to all instances of the type.</span></span> <span data-ttu-id="0d7bc-112">因此您必須小心不要使用集合屬性中繼資料所定義的單一靜態集合，當成您類型新建執行個體的工作預設值。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-112">Therefore you must be careful to not use the singular static collection defined by the collection property metadata as the working default value for newly created instances of your type.</span></span> <span data-ttu-id="0d7bc-113">您必須改確定刻意將唯一 (執行個體) 集合的集合值設定為類別建構函式邏輯的一部分。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-113">Instead, you must make sure that you deliberately set the collection value to a unique (instance) collection as part of your class constructor logic.</span></span> <span data-ttu-id="0d7bc-114">否則會建立意外的單一類別。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-114">Otherwise you will have created an unintentional singleton class.</span></span>  
  
 <span data-ttu-id="0d7bc-115">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-115">Consider the following example.</span></span> <span data-ttu-id="0d7bc-116">以下範例區段顯示類別 `Aquarium` 的定義。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-116">The following section of the example shows the definition for a class `Aquarium`.</span></span> <span data-ttu-id="0d7bc-117">類別會定義集合類型的相依性屬性`AquariumObjects`，它會使用泛型<xref:System.Collections.Generic.List%601>類型與<xref:System.Windows.FrameworkElement>類型條件約束。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-117">The class defines the collection type dependency property `AquariumObjects`, which uses the generic <xref:System.Collections.Generic.List%601> type with a <xref:System.Windows.FrameworkElement> type constraint.</span></span> <span data-ttu-id="0d7bc-118">在<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>相依性屬性中繼資料的呼叫會建立預設值是新的泛型<xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-118">In the <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> call for the dependency property, the metadata establishes the default value to be a new generic <xref:System.Collections.Generic.List%601>.</span></span>  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 <span data-ttu-id="0d7bc-119">不過，如果程式碼保持與範例一致，則單一清單預設值會供 `Aquarium` 的所有執行個體共用。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-119">However, if you just left the code as shown, that single list default value is shared for all instances of `Aquarium`.</span></span> <span data-ttu-id="0d7bc-120">如果執行下列測試程式碼，它原是要示範如何具現化兩個不同的 `Aquarium` 執行個體，並為它們都新增單一不同的 `Fish`，您會看到令人驚訝的結果︰</span><span class="sxs-lookup"><span data-stu-id="0d7bc-120">If you ran the following test code, which is intended to show how you would instantiate two separate `Aquarium` instances and add a single different `Fish` to each of them, you would see a surprising result:</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 <span data-ttu-id="0d7bc-121">不是每個集合都有一個計數，而是每個集合都有兩個計數！</span><span class="sxs-lookup"><span data-stu-id="0d7bc-121">Instead of each collection having a count of one, each collection has a count of two!</span></span> <span data-ttu-id="0d7bc-122">這是因為每個 `Aquarium` 都將自己的 `Fish` 新增至預設值集合，由中繼資料中的單一建構函式呼叫所致，因此在所有執行個體之間共用。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-122">This is because each `Aquarium` added its `Fish` to the default value collection, which resulted from a single constructor call in the metadata and is therefore shared between all instances.</span></span> <span data-ttu-id="0d7bc-123">這種情況根本就不是您想要的。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-123">This situation is almost never what you want.</span></span>  
  
 <span data-ttu-id="0d7bc-124">若要修正這個問題，您必須將集合相依性屬性值重設為唯一的執行個體，當成類別建構函式呼叫的一部分。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-124">To correct this problem, you must reset the collection dependency property value to a unique instance, as part of the class constructor call.</span></span> <span data-ttu-id="0d7bc-125">因為屬性是唯讀的相依性屬性，您會使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法加以設定，使用<xref:System.Windows.DependencyPropertyKey>這只是在類別中存取。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-125">Because the property is a read-only dependency property, you use the <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> method to set it, using the <xref:System.Windows.DependencyPropertyKey> that is only accessible within the class.</span></span>  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 <span data-ttu-id="0d7bc-126">現在，如果再次執行相同的測試程式碼，您會看到更符合預期的結果，其中每個 `Aquarium` 都支援自己的唯一集合。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-126">Now, if you ran that same test code again, you could see more expected results, where each `Aquarium` supported its own unique collection.</span></span>  
  
 <span data-ttu-id="0d7bc-127">如果選擇讓您的集合屬性為可讀寫，則這個模式可能要略加修改。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-127">There would be a slight variation on this pattern if you chose to have your collection property be read-write.</span></span> <span data-ttu-id="0d7bc-128">在此情況下，您可以從以進行初始化，仍會呼叫非索引鍵的簽章的建構函式呼叫公用 set 存取子<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>內您組包裝函式，使用公用<xref:System.Windows.DependencyProperty>識別項。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-128">In that case, you could call the public set accessor from the constructor to do the initialization, which would still be calling the nonkey signature of <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> within your set wrapper, using a public <xref:System.Windows.DependencyProperty> identifier.</span></span>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a><span data-ttu-id="0d7bc-129">報告集合屬性中的繫結值變更</span><span class="sxs-lookup"><span data-stu-id="0d7bc-129">Reporting Binding Value Changes from Collection Properties</span></span>  
 <span data-ttu-id="0d7bc-130">本身為相依性屬性的集合屬性不會自動報告其子屬性變更。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-130">A collection property that is itself a dependency property does not automatically report changes to its subproperties.</span></span> <span data-ttu-id="0d7bc-131">如果您要建立集合繫結，這可以防止繫結報告變更，因而使某些資料繫結案例失效。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-131">If you are creating bindings into a collection, this can prevent the binding from reporting changes, thus invalidating some data binding scenarios.</span></span> <span data-ttu-id="0d7bc-132">不過，如果您使用集合類型<xref:System.Windows.FreezableCollection%601>作為集合類型，然後包含的項目集合中的子屬性變更會正確地報告，並如預期般運作的繫結。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-132">However, if you use the collection type <xref:System.Windows.FreezableCollection%601> as your collection type, then subproperty changes to contained elements in the collection are properly reported, and binding works as expected.</span></span>  
  
 <span data-ttu-id="0d7bc-133">若要啟用相依性物件的集合中的子屬性繫結，建立做為類型的集合屬性<xref:System.Windows.FreezableCollection%601>，使用任何該集合的類型條件約束<xref:System.Windows.DependencyObject>衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0d7bc-133">To enable subproperty binding in a dependency object collection, create the collection property as type <xref:System.Windows.FreezableCollection%601>, with a type constraint for that collection to any <xref:System.Windows.DependencyObject> derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7bc-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d7bc-134">See Also</span></span>  
 <xref:System.Windows.FreezableCollection%601>  
 [<span data-ttu-id="0d7bc-135">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="0d7bc-135">XAML and Custom Classes for WPF</span></span>](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [<span data-ttu-id="0d7bc-136">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="0d7bc-136">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0d7bc-137">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="0d7bc-137">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="0d7bc-138">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="0d7bc-138">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="0d7bc-139">相依性屬性中繼資料</span><span class="sxs-lookup"><span data-stu-id="0d7bc-139">Dependency Property Metadata</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
