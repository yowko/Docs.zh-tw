---
title: "xml:lang Handling in XAML | Microsoft Docs"
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
  - "XAML [XAML Services], xml:lang attribute"
  - "xml:lang attribute [XAML Services]"
  - "RFC 3066 standard [XAML Services]"
  - "standards [XAML Services], RFC 3066"
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:lang Handling in XAML
`xml:lang` 屬性是 [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] 定義的屬性，會宣告 XML 中項目的語言和文化特性資訊。 在 XAML 中有保存與這個屬性相同的意義，但仍須考量一些其他事項。  
  
## XAML Attribute Usage  
  
```  
<object xml:lang="rfc3066lang" />  
```  
  
## XAML 值  
  
|||  
|-|-|  
|*rfc3066lang*|衍生自 [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) 標準的字串，這個字串會識別語言或語言地區。 如果是後者，則語言和區域會由單一連字號分隔。 如需值和格式的詳細資訊，請參閱 <xref:System.Windows.Markup.XmlLanguage>。|  
  
## 備註  
 在 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 中，`xml:lang` 屬性的定義都是衍生自 `xml:lang`，該項目已經由 [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] 定義為 [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] 的「特殊屬性」。 項目在處理語言和文化特性時，其方式可能隨著不同的實作而改變，但是 `xml:lang` 屬性並沒有預設的 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 處理。  
  
 `xml:lang` 屬性的預設值在屬性層級為空字串。  
  
 `xml:lang` 屬性效果和屬性的值，通常由對 `xml:lang` 值作用的系統解譯時，就會以子項目的形式永存。  
  
 由 .NET Framework XAML 服務的 XAML 寫入器解譯時，`xml:lang` 值可能會以基礎物件表示法建立 <xref:System.Windows.Markup.XmlLanguage> 或 <xref:System.Globalization.CultureInfo> 物件，但是該行為取決於對 `xml:lang` 指定的值是否為這些類別的有效建構。  
  
 藉由將 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 套用至屬性，架構即可在架構定義的屬性和 XML 中 `xml:lang` 的意義之間建立關聯性。  
  
## WPF 使用量節點  
 若項目是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的衍生類別，您可以使用對等的 <xref:System.Windows.FrameworkElement.Language%2A> 相依性屬性 \(Property\)，而非 `xml:lang` 屬性 \(Attribute\)。 根據預設，如果沒有透過屬性 \(Property\) 或是透過處理 `xml:lang` 屬性 \(Attribute\) 另外設定，則 <xref:System.Windows.FrameworkElement.Language%2A> 屬性會使用 "en\-US"。  
  
## 請參閱  
 [WPF 的全球化](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)