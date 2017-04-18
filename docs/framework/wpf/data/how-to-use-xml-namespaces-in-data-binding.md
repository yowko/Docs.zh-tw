---
title: "如何：在資料繫結中使用 XML 命名空間 | Microsoft Docs"
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
  - "資料繫結, XML 命名空間"
  - "命名空間, XML"
  - "XML, 命名空間"
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：在資料繫結中使用 XML 命名空間
## 範例  
 這個範例顯示如何處理 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] [繫結來源](GTMT) \(Binding Source\) 中指定的命名空間。  
  
 如果您的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料具有下列 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間定義：  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping> 項目將命名空間對應至 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>，如同下列範例所示。  然後可以使用 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 參考 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間。  這個範例中的 <xref:System.Windows.Controls.ListBox> 會顯示每個 *item* 的 *title* 和 *dc:date*。  
  
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/xaml/VS_Snippets_Wpf/XmlnsBind/XAML/Window1.xaml#xmlnamespacemapping)]
 [!code-xml[XmlnsBind#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBind/CS/Window1.xaml#xmlnamespacemapping)]  
  
 請注意，您指定的 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 不需要符合 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 來源中使用的前置字元，如果 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 來源中的前置字元變更，您的對應仍然有效。  
  
 在這個特定範例中，[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料來自 Web 服務，不過 <xref:System.Windows.Data.XmlNamespaceMapping> 項目也能與內嵌 \(Inline\) [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 或內嵌檔案中的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料一同運作。  
  
## 請參閱  
 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)