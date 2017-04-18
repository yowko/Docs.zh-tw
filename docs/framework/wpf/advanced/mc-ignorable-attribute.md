---
title: "mc:Ignorable 屬性 | Microsoft Docs"
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
  - "mc XML 命名空間前置字元"
  - "mc:Ignorable 屬性"
  - "mc:ProcessContent 屬性"
  - "XAML, mc:Ignorable 屬性"
  - "XAML, mc:ProcessContent 屬性"
  - "XML, mc 命名空間前置字元"
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# mc:Ignorable 屬性
指定 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器可以忽略標記檔案中出現的哪些 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間前置字元。  `mc:Ignorable` 屬性 \(Attribute\) 可支援同時適用於自訂命名空間對應和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 版本控制的標記相容性。  
  
## XAML 屬性使用方式 \(單一前置字元\)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## XAML 屬性使用方式 \(兩個前置字元\)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*ignorablePrefix、ignorablePrefix1 等*|依據 XML 1.0 規格，任何有效的前置字串。|  
|*ignorableUri*|依據 XML 1.0 規格，用來指定命名空間的任何有效 URI。|  
|*ThisElementCanBeIgnored*|無法解析基礎型別時，[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 處理器實作可以忽略的項目。|  
  
## 備註  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間前置字元是對應 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 相容性命名空間 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] 時建議使用的前置字元慣例。  
  
 若項目或屬性中項目名稱的前置字元部分識別為 `mc:Ignorable`，則 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器並不會在處理這些項目或屬性時引發錯誤。  如果該屬性無法解析成基礎型別或程式設計建構，則會忽略該項目。  不過請注意，忽略的項目可能還是會產生其他項目需求的其他剖析錯誤，這也是沒有處理該項目的副作用。  例如，特定項目可能只需要一個子項目，但是如果指定的子項目包含在 `mc:Ignorable` 前置字元中，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器可能就不會引發錯誤。  
  
 `mc:Ignorable` 只適用於識別項字串的命名空間對應。  `mc:Ignorable` 不適用於組件的命名空間對應，其指定 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間和組件 \(或預設為目前做為組件的可執行檔\)。  
  
 如果您是實作 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器，則在受識別為 `mc:Ignorable` 之前置字元限定的任何項目或屬性上進行型別解析時，此處理器實作不能引發剖析或處理錯誤。  但是您的處理器實作仍然可以引發因為無法載入或處理項目而產生的次要例外狀況 \(Exception\)，例如前面提供的單一子項目範例。  
  
 根據預設，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器會忽略已忽略之項目的內容。  不過，您可以額外指定 [mc:ProcessContent 屬性](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)屬性，要求下一個可用的父項目繼續處理已忽略之項目的內容。  
  
 您可以使用一個或多個空白字元做為分隔符號，在屬性中指定多個前置字元，例如：`mc:Ignorable="ignore1 ignore2"`。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] 命名空間會定義[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 的這個區域內未記載的其他項目和屬性。  如需詳細資訊，請參閱 [XML 標記相容性規格](http://go.microsoft.com/fwlink/?LinkId=73824) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Markup.XamlReader>   
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)