---
title: "XAML 載入和相依性屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂相依性屬性"
  - "相依性屬性, XAML 載入和"
  - "載入 XML 資料"
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# XAML 載入和相依性屬性
目前 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的方式在本質上可以感知相依性屬性。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入二進位 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 及處理本身為相依性屬性 \(Property\) 的屬性 \(Attribute\) 時，都會使用相依性屬性 \(Property\) 的屬性 \(Property\) 系統方法。  這可有效略過屬性包裝函式。  當您實作自訂相依性屬性時，必須說明這個行為，而且除了屬性系統方法 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 以外，您應該避免將其他任何程式碼放在屬性包裝函式中。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解如何使用和撰寫相依性屬性，而且閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)和[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  另外您也應該已閱讀過 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)和 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
<a name="implementation"></a>   
## WPF XAML 載入器實作和效能  
 基於實作的考量，請將屬性識別為相依性屬性，並存取用來設定屬性的 <xref:System.Windows.DependencyObject.SetValue%2A> 方法，而不要使用屬性包裝函式及其 setter，以降低所需的運算成本。  這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器必須單就標記和各種字串結構所指定的已知型別與成員關係，推斷支援程式碼的完整物件模型。  
  
 型別是透過 xmlns 和組件 \(Assembly\) 屬性 \(Attribute\) 來查詢，但是識別成員、判斷何者可以設定為屬性 \(Attribute\)，以及解析屬性 \(Property\) 值支援之型別等作業，則需要使用 <xref:System.Reflection.PropertyInfo> 進行全面性的反映 \(Reflection\)。  因為指定之型別上的相依性屬性可以透過屬性系統存取成儲存表，所以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器時將會使用這個表格，並推斷只要使用相依性屬性識別項 *ABCProperty*，在包含 <xref:System.Windows.DependencyObject> 衍生型別 \(Derived Type\) 上呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>，即可更有效率地設定任何指定的屬性 *ABC*。  
  
<a name="implications"></a>   
## 自訂相依性屬性的含意  
 由於目前 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作屬性設定的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器行為會完全略過包裝函式，因此請勿將任何額外的邏輯放入自訂相依性屬性的包含函式集合定義。  如果您將這種邏輯放入集合定義中，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 而非程式碼中設定屬性時，並不會執行該邏輯。  
  
 同樣地，從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理取得屬性值的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器其他設定也可能會使用 <xref:System.Windows.DependencyObject.GetValue%2A>，而不會使用包裝函式。  因此，您也應該避免在 `get` 定義中包含 <xref:System.Windows.DependencyObject.GetValue%2A> 呼叫以外的其他任何實作。  
  
 下列範例是內含包裝函式的建議相依性屬性定義，其中的屬性識別項儲存為 `public` `static` `readonly` 欄位，而且除了用來定義相依性屬性支援的必要屬性系統方法以外，`get` 和 `set` 定義中並未包含其他程式碼。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## 請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [集合類型相依性屬性](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [DependencyObject 的安全建構函式模式](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)