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
# <a name="collection-type-dependency-properties"></a>集合類型相依性屬性
本主題提供如何實作屬性類型為集合類型之相依性屬性的指引和建議模式。  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>實作集合類型相依性屬性  
 對於依賴項屬性，您遵循的實現模式是定義 CLR 屬性包裝器，其中該屬性由<xref:System.Windows.DependencyProperty>識別碼而不是欄位或其他構造支援。 當您實作集合類型屬性時，您可以遵循此相同的模式。 但是，每當集合中包含的類型本身是或<xref:System.Windows.DependencyObject><xref:System.Windows.Freezable>派生類時，集合類型屬性都會給模式帶來一些複雜性。  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>初始化超過預設值的集合  
 建立相依性屬性時，未指定屬性預設值為初始欄位值。 而是透過相依性屬性中繼資料指定預設值。 如果屬性是參考類型，則在相依性屬性中繼資料中指定的預設值不是每個執行個體的預設值，而是適用於所有類型執行個體的預設值。 因此您必須小心不要使用集合屬性中繼資料所定義的單一靜態集合，當成您類型新建執行個體的工作預設值。 您必須改確定刻意將唯一 (執行個體) 集合的集合值設定為類別建構函式邏輯的一部分。 否則會建立意外的單一類別。  
  
 請思考一下下列範例。 示例的以下部分顯示了類`Aquarium`的定義，其中包含具有預設值的缺陷。 類定義集合類型依賴項屬性`AquariumObjects`，它使用泛型<xref:System.Collections.Generic.List%601>類型與<xref:System.Windows.FrameworkElement>類型約束。 在<xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>對依賴項屬性的調用中，中繼資料將預設值建立為新泛型<xref:System.Collections.Generic.List%601>。

> [!WARNING]
> 以下代碼的行為不正確。

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 不過，如果程式碼保持與範例一致，則單一清單預設值會供 `Aquarium` 的所有執行個體共用。 如果執行下列測試程式碼，它原是要示範如何具現化兩個不同的 `Aquarium` 執行個體，並為它們都新增單一不同的 `Fish`，您會看到令人驚訝的結果︰  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 不是每個集合都有一個計數，而是每個集合都有兩個計數！ 這是因為每個 `Aquarium` 都將自己的 `Fish` 新增至預設值集合，由中繼資料中的單一建構函式呼叫所致，因此在所有執行個體之間共用。 這種情況根本就不是您想要的。  
  
 若要修正這個問題，您必須將集合相依性屬性值重設為唯一的執行個體，當成類別建構函式呼叫的一部分。 由於該屬性是唯讀依賴項屬性，因此使用<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29>方法設置它，使用 僅在類<xref:System.Windows.DependencyPropertyKey>中可訪問的 。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 現在，如果再次執行相同的測試程式碼，您會看到更符合預期的結果，其中每個 `Aquarium` 都支援自己的唯一集合。  
  
 如果選擇讓您的集合屬性為可讀寫，則這個模式可能要略加修改。 在這種情況下，可以從建構函式調用公共集訪問器來執行初始化，該初始化仍將使用公共<xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29><xref:System.Windows.DependencyProperty>識別碼調用 set 包裝器中的非鍵簽名。  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>報告集合屬性中的繫結值變更  
 本身為相依性屬性的集合屬性不會自動報告其子屬性變更。 如果您要建立集合繫結，這可以防止繫結報告變更，因而使某些資料繫結案例失效。 但是，如果使用集合類型<xref:System.Windows.FreezableCollection%601>作為集合類型，則子屬性對集合中包含的元素的更改將正確報告，並且綁定按預期方式工作。  
  
 要在依賴項物件集合中啟用子屬性綁定，請將集合屬性創建<xref:System.Windows.FreezableCollection%601>為類型，該集合的類型約束為任何<xref:System.Windows.DependencyObject>派生類。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FreezableCollection%601>
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
