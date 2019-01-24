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
ms.openlocfilehash: 21f260262d434ffe3685b226193f2d6cd2125549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548426"
---
# <a name="collection-type-dependency-properties"></a>集合類型相依性屬性
本主題提供如何實作屬性類型為集合類型之相依性屬性的指引和建議模式。  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>實作集合類型相依性屬性  
 相依性屬性在一般情況下，您所遵循的實作模式是您定義[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性包裝函式，其中該屬性做為後盾<xref:System.Windows.DependencyProperty>識別碼而不是欄位或其他建構。 當您實作集合類型屬性時，您可以遵循此相同的模式。 不過，會是集合型別屬性增添少許複雜性模式，每當集合中包含的型別本身<xref:System.Windows.DependencyObject>或<xref:System.Windows.Freezable>衍生的類別。  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>初始化超過預設值的集合  
 建立相依性屬性時，未指定屬性預設值為初始欄位值。 而是透過相依性屬性中繼資料指定預設值。 如果屬性是參考類型，則在相依性屬性中繼資料中指定的預設值不是每個執行個體的預設值，而是適用於所有類型執行個體的預設值。 因此您必須小心不要使用集合屬性中繼資料所定義的單一靜態集合，當成您類型新建執行個體的工作預設值。 您必須改確定刻意將唯一 (執行個體) 集合的集合值設定為類別建構函式邏輯的一部分。 否則會建立意外的單一類別。  
  
 請參考下列範例。 以下範例區段顯示類別 `Aquarium` 的定義。 類別會定義集合類型相依性屬性`AquariumObjects`，它會使用泛型<xref:System.Collections.Generic.List%601>型別與<xref:System.Windows.FrameworkElement>類型條件約束。 在 <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>相依性屬性中繼資料的呼叫會將預設值是新的泛型<xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 不過，如果程式碼保持與範例一致，則單一清單預設值會供 `Aquarium` 的所有執行個體共用。 如果執行下列測試程式碼，它原是要示範如何具現化兩個不同的 `Aquarium` 執行個體，並為它們都新增單一不同的 `Fish`，您會看到令人驚訝的結果︰  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 不是每個集合都有一個計數，而是每個集合都有兩個計數！ 這是因為每個 `Aquarium` 都將自己的 `Fish` 新增至預設值集合，由中繼資料中的單一建構函式呼叫所致，因此在所有執行個體之間共用。 這種情況根本就不是您想要的。  
  
 若要修正這個問題，您必須將集合相依性屬性值重設為唯一的執行個體，當成類別建構函式呼叫的一部分。 因為屬性是唯讀的相依性屬性，您會使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法來設定，使用<xref:System.Windows.DependencyPropertyKey>這只是在類別內存取。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 現在，如果再次執行相同的測試程式碼，您會看到更符合預期的結果，其中每個 `Aquarium` 都支援自己的唯一集合。  
  
 如果選擇讓您的集合屬性為可讀寫，則這個模式可能要略加修改。 在此情況下，您可以從執行初始化，仍會呼叫非索引鍵的簽章的建構函式呼叫公用 set 存取子<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29>內您 set 包裝函式中，使用公用<xref:System.Windows.DependencyProperty>識別項。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>報告集合屬性中的繫結值變更  
 本身為相依性屬性的集合屬性不會自動報告其子屬性變更。 如果您要建立集合繫結，這可以防止繫結報告變更，因而使某些資料繫結案例失效。 不過，如果您使用集合類型<xref:System.Windows.FreezableCollection%601>作為您的集合類型，然後在集合中包含的項目子屬性變更會正確報告，並繫結是否如預期運作。  
  
 若要啟用相依性物件集合中的子屬性繫結，建立 集合屬性做為類型<xref:System.Windows.FreezableCollection%601>，使用任何該集合的型別條件約束<xref:System.Windows.DependencyObject>衍生的類別。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FreezableCollection%601>
- [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
