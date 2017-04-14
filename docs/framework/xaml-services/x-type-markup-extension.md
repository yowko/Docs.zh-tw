---
title: "x:Type Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "x:TypeExtension"
  - "Type"
  - "x:Type"
  - "xType"
  - "TypeExtension"
helpviewer_keywords: 
  - "x:Type markup extension [XAML Services]"
  - "XAML [XAML Services], x:Type markup extension"
  - "XAML [XAML Services], TargetType attribute"
  - "TargetType attribute [XAML Services]"
  - "Type markup extension in XAML [XAML Services]"
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Type Markup Extension
提供 CLR <xref:System.Type> 物件，這是所指定 XAML 型別的基礎型別。  
  
## XAML Attribute Usage  
  
```  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## XAML 物件項目用法  
  
```  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`prefix`|選擇項。  對應非預設 XAML 命名空間的前置詞。  通常不需要指定前置字元。  請參閱＜備註＞。|  
|`typeNameValue`|必要項。  可解析為目前預設 XAML 命名空間的型別名稱，如果已提供 `prefix`，則為指定的對應前置詞。|  
  
## 備註  
 `x:Type` 標記延伸與 [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] 中的 `typeof()` 運算子，或是 [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] 中的 `GetType` 運算子具有相似的功能。  
  
 `x:Type` 標記延伸針對採用 <xref:System.Type> 型別之屬性提供從字串轉換行為。  輸入是 XAML 型別。  輸入 XAML 型別和輸出 CLR <xref:System.Type> 之間的關聯性為，在根據 XAML 結構描述內容和內容提供的 <xref:System.Windows.Markup.IXamlTypeResolver> 服務，查閱必要 <xref:System.Xaml.XamlType> 之後，輸出 <xref:System.Type> 會是 輸入 <xref:System.Xaml.XamlType> 的 <xref:System.Xaml.XamlType.UnderlyingType%2A>。  
  
 在 .NET Framework XAML 服務實作中，這個標記延伸的處理是由 <xref:System.Windows.Markup.TypeExtension> 類別定義的。  
  
 在特定的架構實作中，採取 <xref:System.Type> 做為值的一些屬性都可以直接接受型別名稱 \(型別之 `Name` 的字串值\)。  不過，實作這個行為是複雜的情節。  如需範例，請參閱下列的「WPF 使用注意事項」一節。  
  
 屬性 \(Attribute\) 語法是最常配合這個標記延伸使用的語法。  `x:Type` 識別項字串後提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension> 延伸類別的 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 值。  在 .NET Framework XAML Services 的預設 XAML 結構描述內容下，也就是以 CLR 型別為基礎，這個屬性的值不是需要之型別的 <xref:System.Reflection.MemberInfo.Name%2A>，就是包含該 <xref:System.Reflection.MemberInfo.Name%2A>，並在之前有非預設 XAML 命名空間對應的前置詞。  
  
 `x:Type` 標記延伸可用於物件項目語法。  在這個情況下，必須要指定 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 屬性的值，才能適當初始化延伸。  
  
 `x:Type` 標記延伸也可以當做詳細資訊屬性使用，但是這種用法並不常見：`<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## WPF 使用注意事項  
  
### 預設 XAML 命名空間和型別對應  
 WPF 程式設計的預設 XAML 命名空間包含您在一般 XAML 案例所需要的大多數 XAML 型別，因此您通常可以在參考 XAML 型別值時避免使用前置詞。  如果您所參考的型別來自於自訂組件，或是當型別存在於 WPF 組件中，卻位於沒有對應至預設 XAML 命名空間的 CLR 命名空間內，就可能需要對應前置詞。  如需前置詞、XAML 命名空間和對應 CLR 命名空間的詳細資訊，請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
### 支援以字串形式表示之型別名稱的型別屬性  
 WPF 支援指定 <xref:System.Type> 型別的一些屬性的值，而不需要 `x:Type` 標記延伸使用方式的技術。  您可以改成將值指定為命名型別的字串。  此項的範例為 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=fullName> 和 <xref:System.Windows.Style.TargetType%2A?displayProperty=fullName>。  沒有透過型別轉換子或標記延伸提供這項行為的支援。  而是透過 <xref:System.Windows.FrameworkElementFactory> 所實作的延遲行為。  
  
 Silverlight 支援類似的慣例。  事實上，Silverlight 目前的 XAML 語言支援中不支援`{x:Type}`，而且不接受 `{x:Type}` 使用方式，除了用於支援 WPF\-Silverlight XAML 移轉的少數情況以外。  因此，將型別名稱當做字串的行為是內建於所有 Silverlight 原生屬性評估，其中 <xref:System.Type> 即是該值。  
  
## XAML 2009  
 XAML 2009 為泛型型別提供額外的支援，並且修改 `x:TypeArguments` 和 `x:Type` 的功能行為，以提供這項支援。  
  
-   `x:TypeArguments` 和泛型物件執行個體化的相關物件項目可以在根以外的項目上進行。  如需詳細資訊，請參閱 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)的＜XAML 2009＞一節。  
  
-   XAML 2009 支援在標記中指定泛型型別條件約束的語法。  可由 `x:TypeArguments`、`x:Type`，或是這兩種功能的組合使用。  
  
-   處理負載的 XAML 2009 時，WPF XAML 實作也會將這項功能加入到使用型別 <xref:System.Type> 之特定架構屬性的型別轉換行為。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用於寬鬆 XAML \(未以標記編譯的 XAML\)。  WPF 的標記編譯 XAML 以及 XAML 的 BAML 表單目前不支援 XAML 2009 關鍵字和功能。  
  
## 請參閱  
 <xref:System.Windows.Style>   
 [設定樣式和範本](../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML 概觀 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)