---
title: "x:Type 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a>x:Type 標記延伸
提供 CLR<xref:System.Type>是指定的 XAML 類型的基礎類型的物件。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`prefix`|選擇性。 將非預設 XAML 命名空間對應前置詞。 指定前置詞通常是不必要。 請參閱＜備註＞。|  
|`typeNameValue`|必要。 型別名稱解析成目前的預設 XAML 命名空間;或指定的對應前置詞，如果`prefix`提供。|  
  
## <a name="remarks"></a>備註  
 `x:Type`標記延伸可以類似的函式來`typeof()`中的運算子[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)]或`GetType`中的運算子[!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]。  
  
 `x:Type`標記延伸提供針對接受的類型屬性，從字串轉換行為<xref:System.Type>。 輸入是 XAML 類型。 輸入的 XAML 型別與 CLR 的輸出之間的關聯性<xref:System.Type>在於輸出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>輸入的<xref:System.Xaml.XamlType>之後查閱所需之,<xref:System.Xaml.XamlType>根據 XAML 結構描述內容和<xref:System.Windows.Markup.IXamlTypeResolver>內容提供的服務。  
  
 在.NET Framework XAML 服務，此標記延伸處理由定義<xref:System.Windows.Markup.TypeExtension>類別。  
  
 在特定架構實作中，有些屬性可接受<xref:System.Type>值可以直接接受類型的名稱 (類型的字串值`Name`)。 不過，實作這種行為是複雜的案例。 如需範例，請參閱 < WPF 使用量注意事項 > 一節。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。 在預設 XAML 結構描述內容，針對.NET Framework XAML 服務，此作業取決於 CLR 型別，這個屬性的值是<xref:System.Reflection.MemberInfo.Name%2A>所需的型別，或包含的<xref:System.Reflection.MemberInfo.Name%2A>加上前置詞為非預設 XAML 命名空間對應。  
  
 `x:Type`標記延伸可用於物件項目語法。 在此情況下，指定的值<xref:System.Windows.Markup.TypeExtension.TypeName%2A>屬性才能正確地初始化擴充功能。  
  
 `x:Type`標記延伸也可用做為詳細資訊的屬性; 不過此，請使用不是標準： `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>預設 XAML 命名空間和型別對應  
 WPF 程式設計的預設 XAML 命名空間包含大部分的一般 XAML 情節; 所需的 XAML 型別因此，您通常可以避免前置詞時參考 XAML 類型的值。 您可能需要對應前置詞，如果您從自訂組件或類型存在於 WPF 組件但未對應的預設 XAML 命名空間到 CLR 命名空間的參考型別。 如需有關前置詞、 XAML 命名空間和對應的 CLR 命名空間的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
### <a name="type-properties-that-support-typename-as-string"></a>輸入屬性的支援類型名稱做為-字串  
 WPF 支援技術可讓您指定的類型的某些內容值<xref:System.Type>而不需要`x:Type`標記延伸使用方式。 相反地，您可以指定值為命名類型的字串。 此範例<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>和<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>。 未透過型別轉換子或標記延伸提供支援這種行為。 相反地，這是透過實作延遲行為<xref:System.Windows.FrameworkElementFactory>。  
  
 Silverlight 支援類似的慣例。 事實上，Silverlight 目前不支援`{x:Type}`中其 XAML 語言支援，而且不接受`{x:Type}`在某些情況下，為了支援 WPF Silverlight XAML 移轉之外的使用方式。 因此，類型名稱做為字串行為是內建於所有的 Silverlight 原生屬性評估其中<xref:System.Type>的值。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 支援其他的泛型類型，並修改功能行為的`x:TypeArguments`和`x:Type`提供這項支援。  
  
-   `x:TypeArguments`它的泛型物件具現化的相關聯的物件項目可以是根目錄以外的項目上。 如需詳細資訊，請參閱的 < XAML 2009 > 一節[X:typearguments 指示詞](../../../docs/framework/xaml-services/x-typearguments-directive.md)。  
  
-   XAML 2009 支援語法標記中指定的泛型類型條件約束。 這可由`x:TypeArguments`、 藉由`x:Type`，或結合兩個功能。  
  
-   WPF XAML 實作處理 XAML 2009 的負載也會將這項功能加入至特定 framework 內容的使用類型的隱含類型轉換行為時<xref:System.Type>。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但是僅針對鬆散的 XAML (未標記編譯 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Style>  
 [樣式設定和範本化](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
