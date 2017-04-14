---
title: "從類別匯出結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, 結構描述匯入和匯出"
  - "結構描述 [WCF], 從類別匯出"
  - "結構描述 [WCF]"
  - "XsdDataContractExporter 類別"
  - "XsdDataContractImporter 類別"
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 從類別匯出結構描述
如果要從用於資料合約模型中的類別產生 XML 結構描述定義語言 \(XSD\)，請使用 <xref:System.Runtime.Serialization.XsdDataContractExporter> 類別。 這個主題將說明建立結構描述的程序。  
  
## 匯出程序  
 結構描述匯出程序是以一個或多個類型開始，然後產生描述這些類型的 XML 規劃的 <xref:System.Xml.Schema.XmlSchemaSet>。  
  
 `XmlSchemaSet` 是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的結構描述物件模型 \(SOM\) 的一部分，代表一組 XSD 結構描述文件。 如果要從 `XmlSchemaSet` 建立 XSD 文件，請使用來自 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 類別之 `XmlSchemaSet` 屬性的結構描述集合。 然後使用 <xref:System.Xml.Schema.XmlSchema> 序列化各個 <xref:System.Xml.Serialization.XmlSerializer> 物件。  
  
#### 匯出結構描述  
  
1.  建立 <xref:System.Runtime.Serialization.XsdDataContractExporter> 的執行個體。  
  
2.  選擇項。 在建構函式中傳遞 <xref:System.Xml.Schema.XmlSchemaSet>。 在這種情況下，在結構描述匯出期間產生的結構描述會新增至這個 <xref:System.Xml.Schema.XmlSchemaSet> 執行個體，而不是從空白的 <xref:System.Xml.Schema.XmlSchemaSet> 開始。  
  
3.  選擇項。 呼叫其中一個 <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> 方法。 此方法會判斷是否可以匯出指定的類型。 此方法的多載和下一個步驟中的 `Export` 方法相同。  
  
4.  呼叫其中一個 <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> 方法。 有三種多載採用 <xref:System.Type>、<xref:System.Collections.Generic.List%601> 物件的 `Type` 或 <xref:System.Collections.Generic.List%601> 物件的 <xref:System.Reflection.Assembly>。 在最後一種情況中，會匯出所有指定組件中的所有類型。  
  
     `Export` 方法的多個呼叫會造成將多個項目新增至相同的 `XmlSchemaSet`。 如果型別已經存在，便不會產生至 `XmlSchemaSet` 中。 因此，如果要建立 `Export`  類別的多個執行個體，會偏好在相同的 `XsdDataContractExporter` 上呼叫多次 `XsdDataContractExporter`。 如此可避免產生重複的結構描述型別。  
  
    > [!NOTE]
    >  如果在匯出期間有失敗，`XmlSchemaSet` 將會處於不能預測的狀態。  
  
5.  請透過 <xref:System.Xml.Schema.XmlSchemaSet> 屬性存取 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A>。  
  
## 匯出選項  
 您可以將 <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> 之 <xref:System.Runtime.Serialization.XsdDataContractExporter> 屬性設定為 <xref:System.Runtime.Serialization.ExportOptions> 類別的執行個體，以控制匯出處理程序的各方面。 特別是，您可以設定下列選項：  
  
-   <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>.`Type` 的這個集合代表正在匯出之型別的已知型別  \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).\) 除了傳遞至 `Export` 方法的型別之外，每次呼叫 `Export` 也會匯出這些已知型別。  
  
-   <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>.<xref:System.Runtime.Serialization.IDataContractSurrogate> 可以透過將會自訂匯出程序的這個屬性來提供。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). 根據預設，不會使用 Surrogate。  
  
## Helper 方法  
 除了匯出結構描述的主要角色之外，`XsdDataContractExporter` 還提供數種有用的 Helper 方法，提供有關型別的資訊。 這些活動包括：  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> 方法。 這個方法會採用 `Type` 並傳回 <xref:System.Xml.XmlQualifiedName>，代表如果將這個型別序列化為根物件，會使用的根項目名稱和命名空間。  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> 方法。 這個方法會採用 `Type` 並傳回 <xref:System.Xml.XmlQualifiedName>，代表如果將這個型別匯出至結構描述，會使用的 XSD 結構描述型別的名稱。 對於在結構描述中表示為匿名型別的 <xref:System.Xml.Serialization.IXmlSerializable> 型別，這個方法會傳回 `null`。  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> 方法。 這個方法只能使用在結構描述中表示為匿名型別的 <xref:System.Xml.Serialization.IXmlSerializable> 型別，並為所有其他的型別傳回 `null`。 對於匿名型別，這個方法會傳回代表指定 <xref:System.Xml.Schema.XmlSchemaType> 的 `Type`。  
  
 匯出選項會影響所有這些方法。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 [結構描述匯入和匯出](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)   
 [匯入結構描述以產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)