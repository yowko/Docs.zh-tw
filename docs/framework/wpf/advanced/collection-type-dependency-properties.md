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
ms.openlocfilehash: dd268c0c132f4ecefe7b2336432442d9569ca38f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401565"
---
# <a name="collection-type-dependency-properties"></a>集合類型相依性屬性
本主題提供如何實作屬性類型為集合類型之相依性屬性的指引和建議模式。  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>實作集合類型相依性屬性  
 針對相依性屬性, 您所遵循的執行模式是定義 CLR 屬性包裝函式, 其中該屬性是由<xref:System.Windows.DependencyProperty>識別碼所支援, 而不是欄位或其他結構。 當您實作集合類型屬性時，您可以遵循此相同的模式。 不過, 每當集合中包含的類型本身<xref:System.Windows.DependencyObject>為或<xref:System.Windows.Freezable>衍生類別時, 集合類型屬性就會對模式帶來一些複雜性。  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>初始化超過預設值的集合  
 建立相依性屬性時，未指定屬性預設值為初始欄位值。 而是透過相依性屬性中繼資料指定預設值。 如果屬性是參考類型，則在相依性屬性中繼資料中指定的預設值不是每個執行個體的預設值，而是適用於所有類型執行個體的預設值。 因此您必須小心不要使用集合屬性中繼資料所定義的單一靜態集合，當成您類型新建執行個體的工作預設值。 您必須改確定刻意將唯一 (執行個體) 集合的集合值設定為類別建構函式邏輯的一部分。 否則會建立意外的單一類別。  
  
 請參考下列範例。 以下範例區段顯示類別 `Aquarium` 的定義。 類別會定義集合類型相依性屬性`AquariumObjects`, 它會使用具有<xref:System.Collections.Generic.List%601> <xref:System.Windows.FrameworkElement>類型條件約束的泛型型別。 在相依<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>性屬性的呼叫中, 中繼資料會將預設值建立為新的泛型<xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 不過，如果程式碼保持與範例一致，則單一清單預設值會供 `Aquarium` 的所有執行個體共用。 如果執行下列測試程式碼，它原是要示範如何具現化兩個不同的 `Aquarium` 執行個體，並為它們都新增單一不同的 `Fish`，您會看到令人驚訝的結果︰  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 不是每個集合都有一個計數，而是每個集合都有兩個計數！ 這是因為每個 `Aquarium` 都將自己的 `Fish` 新增至預設值集合，由中繼資料中的單一建構函式呼叫所致，因此在所有執行個體之間共用。 這種情況根本就不是您想要的。  
  
 若要修正這個問題，您必須將集合相依性屬性值重設為唯一的執行個體，當成類別建構函式呼叫的一部分。 因為屬性是唯讀相依性屬性, 所以您可以使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法來設定它, 其方式是<xref:System.Windows.DependencyPropertyKey>使用只能在類別中存取的。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 現在，如果再次執行相同的測試程式碼，您會看到更符合預期的結果，其中每個 `Aquarium` 都支援自己的唯一集合。  
  
 如果選擇讓您的集合屬性為可讀寫，則這個模式可能要略加修改。 在這種情況下, 您可以從函式呼叫公用 set 存取子來進行初始化, 這仍會使用公用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> <xref:System.Windows.DependencyProperty>識別碼, 在您的集合包裝函式內呼叫的非索引鍵簽章。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>報告集合屬性中的繫結值變更  
 本身為相依性屬性的集合屬性不會自動報告其子屬性變更。 如果您要建立集合繫結，這可以防止繫結報告變更，因而使某些資料繫結案例失效。 不過, 如果您使用集合型<xref:System.Windows.FreezableCollection%601>別做為集合型別, 就會正確地報告集合中包含之元素的子屬性變更, 而且系結會如預期般運作。  
  
 若要在相依性物件集合中啟用屬性 (property) 系結, <xref:System.Windows.FreezableCollection%601>請建立集合屬性做為類型, 並將<xref:System.Windows.DependencyObject>該集合的類型條件約束加入至任何衍生類別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FreezableCollection%601>
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
