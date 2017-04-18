---
title: "集合類型相依性屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "集合類型屬性"
  - "相依性屬性"
  - "屬性, 集合類型"
  - "屬性, dependency"
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 集合類型相依性屬性
本主題提供如何實作屬性型別為集合型別之[相依性屬性](GTMT)的方針與建議模式。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="implementing"></a>   
## 實作集合型別相依性屬性  
 對於一般相依性屬性，您所遵循的實作模式是您會定義 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性包裝函式，而其中該屬性是受 <xref:System.Windows.DependencyProperty> 識別項支援，而非欄位或其他建構。  您在實作集合型別屬性時也會遵循相同的模式。  不過，每當集合內含的型別本身是 <xref:System.Windows.DependencyObject> 或 <xref:System.Windows.Freezable> 衍生類別 \(Derived Class\) 時，集合型別屬性都會增加此模式的些許複雜度。  
  
<a name="initializing"></a>   
## 不使用預設值初始化集合  
 建立相依性屬性時，您不會指定屬性預設值做為初始欄位值，  而會透過相依性屬性中繼資料指定預設值。  如果您的屬性是參考型別 \(Reference Type\)，相依性屬性中繼資料中指定的預設值不是每個執行個體 一個預設值，而是一個預設值適用於該型別的所有執行個體。  因此，您必須小心，避免使用集合型別屬性中繼資料所定義的單一靜態集合，做為新建立之型別執行個體的工作預設值。  您必須刻意將集合值設定為唯一 \(執行個體\) 集合，做為類別建構函式邏輯的一部分，  否則將會建立非預期的單一類別。  
  
 參考下列範例：  下列範例區段顯示 `Aquarium` 類別的定義。  此類別定義集合型別相依性屬性 `AquariumObjects`，這個屬性使用具有 <xref:System.Windows.FrameworkElement> 型別條件約束的泛型 <xref:System.Collections.Generic.List%601> 型別。  在相依性屬性的 <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> 呼叫中，中繼資料會將預設值建立為新的泛型 <xref:System.Collections.Generic.List%601>。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemdefinition)]  
[!code-csharp[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemendb)]
[!code-vb[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemendb)]  
  
 不過，若您保留顯示的程式碼不變，`Aquarium` 的所有執行個體會共用單一清單預設值。  如果執行下列測試程式碼，您會看到意外的結果 \(這個測試程式碼的目的是要顯示如何具現化 \(Instantiate\) 兩個個別 `Aquarium` 執行個體，並將不同的單一 `Fish` 加入至每個執行個體\)：  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 每個集合擁有的計數不是一，而是二！\!  這是因為每個 `Aquarium` 都會將其 `Fish` 加入至預設值集合，而這是中繼資料中單一建構函式呼叫所產生的結果，因此會在所有的執行個體間共用。  這種情況應該不是您想要的結果。  
  
 若要更正這個問題，您必須將集合相依性屬性值重設成唯一執行個體，做為類別建構函式邏輯呼叫的一部分。  因為屬性是唯讀的相依性屬性，所以您必須使用 <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> 方法，利用只能在類別內存取的 <xref:System.Windows.DependencyPropertyKey> 來設定此屬性。  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 現在，如果重新執行相同的測試程式碼，您就可以看到預期的結果，也就是每個 `Aquarium` 都支援其本身的唯一集合。  
  
 如果您選擇讓集合屬性變成讀寫集合，這個模式可能稍有不同。  在這種情況下，您可以從建構函式呼叫公用 \(Public\) set 存取子 \(Accessor\) 來執行初始設定，而初始設定仍會使用公用 <xref:System.Windows.DependencyProperty> 識別項，在您的 set 包裝函式內呼叫 <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> 的非索引鍵簽章 \(Signature\)。  
  
## 報告集合屬性中的繫結值變更  
 本身為相依性屬性的集合屬性並不會自動報告其子屬性的變更。  如果您要在集合中建立繫結，這可能會讓該繫結無法報告變更，因而導致某些資料繫結 \(Data Binding\) 案例失效。  不過，如果您使用集合型別 <xref:System.Windows.FreezableCollection%601> 做為集合型別，便可正確報告集合中內含項目的子屬性變更，而且繫結也可如預期般運作。  
  
 若要在相依性物件集合中啟用子屬性繫結，請使用該集合對任何 <xref:System.Windows.DependencyObject> 衍生類別的型別條件約束，將集合屬性建立成型別 <xref:System.Windows.FreezableCollection%601>。  
  
## 請參閱  
 <xref:System.Windows.FreezableCollection%601>   
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)