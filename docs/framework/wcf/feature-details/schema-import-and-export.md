---
title: 結構描述匯入和匯出
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8489c0bf20d3d62501db269c5a72de657bcbbc97
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="schema-import-and-export"></a>結構描述匯入和匯出
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 包含新的序列化 (Serialization) 引擎， <xref:System.Runtime.Serialization.DataContractSerializer>。 `DataContractSerializer` 會在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件與 XML 之間轉譯 (雙向)。 除了序列化程式本身，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 還包含關聯的結構描述匯入與結構描述匯出機制。 *結構描述*是正式、 精確且可供電腦讀取或還原序列化程式可以存取之序列化程式所產生之 XML 的外觀的描述。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用「全球資訊網協會」(W3C) XML 結構描述定義 (XSD) 語言做為其結構描述表示，該語言可廣泛地在許多協力廠商平台互通。  
  
 結構描述匯入元件 <xref:System.Runtime.Serialization.XsdDataContractImporter> 會接受 XSD 結構描述文件，並產生 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類別 (通常是資料合約類別)，讓序列化的表單對應至指定的結構描述。  
  
 例如，下列結構描述片段：  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 會產生下列型別 (已因應提高可讀性而稍微簡化)。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 請注意，產生的型別會遵循數個資料合約最佳做法 (位於[最佳做法： 資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   此型別會實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
-   資料成員會實作為包裝私用欄位的公用屬性。  
  
-   此類別是部份類別，而且透過不需要修改產生之程式碼來新增項目。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> 讓您能夠進行相反的動作，也就是接受可使用 `DataContractSerializer` 序列化的型別，並產生 XSD 結構描述文件。  
  
## <a name="fidelity-is-not-guaranteed"></a>不保證精確度  
 這個類別不保證結構描述或型別在來回行程中絕對保有完整的精確度  (A*來回行程*表示匯入結構描述來建立一組類別，並將結果匯出以再度建立結構描述。)不一定會傳回相同的結構描述。 反向進行此程序時也不能保證維持精確度  (匯出型別以產生其結構描述，然後再將該型別匯入回來。 不太可能會傳回相同的型別)。  
  
## <a name="supported-types"></a>支援的型別  
 資料合約模型只支援有限的 WC3 結構描述子集。 不符合這個子集的任何結構描述，都會在匯入程序進行時造成例外狀況。 例如，沒有任何方式能夠指定資料合約的成員應該要序列化為 XML 屬性。 這樣一來，因為不可能以正確的 XML 規劃來產生資料合約，所以就不會支援需要使用 XML 屬性的結構描述，進而會在匯入期間造成例外狀況。  
  
 例如，下列結構描述片段無法使用預設的匯入設定來進行匯入。  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 如需詳細資訊，請參閱[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 如果結構描述不符合資料合約規則，請使用不同的序列化引擎。 例如，<xref:System.Xml.Serialization.XmlSerializer> 會使用自己的個別結構描述匯入機制。 另外，還有一種可用來擴充受支援結構描述之範圍的特殊匯入模式。 如需詳細資訊，請參閱有關產生節<xref:System.Xml.Serialization.IXmlSerializable>中的型別[匯入的結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。  
  
 `XsdDataContractExporter` 會支援可用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 序列化的任何 `DataContractSerializer` 型別。 如需詳細資訊，請參閱[資料合約序列化程式所支援的型別](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。 請注意，使用 `XsdDataContractExporter` 產生的型別，通常是 `XsdDataContractImporter` 可使用的有效資料 (除非 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 是用於自訂結構描述)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 使用<xref:System.Runtime.Serialization.XsdDataContractImporter>，請參閱[匯入的結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 使用<xref:System.Runtime.Serialization.XsdDataContractExporter>，請參閱[匯出類別中的結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [匯入結構描述以產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)  
 [從類別匯出結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
