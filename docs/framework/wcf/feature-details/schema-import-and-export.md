---
title: 結構描述匯入和匯出
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: a14ee9e5916133be3979650055cf3e57899a4cca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591806"
---
# <a name="schema-import-and-export"></a>結構描述匯入和匯出
Windows Communication Foundation (WCF) 包含新的序列化引擎， <xref:System.Runtime.Serialization.DataContractSerializer>。 `DataContractSerializer` .NET Framework 物件與 XML 之間轉譯 （兩個方向）。 除了本身的序列化程式，WCF 會包含相關聯的結構描述匯入和結構描述匯出機制。 *結構描述*是的 XML 序列化程式產生或還原序列化程式可以存取的形狀的正式、 精確及電腦可讀取描述。 WCF 會使用 World Wide Web Consortium (W3C) XML 結構描述定義語言 (XSD) 做為其結構描述表示，也就是許多第三方平台廣泛互通。  
  
 結構描述匯入元件<xref:System.Runtime.Serialization.XsdDataContractImporter>、 採用的 XSD 結構描述文件，並產生.NET Framework 類別 （通常資料合約類別），使已序列化的表單對應至指定的結構描述。  
  
 例如，下列結構描述片段：  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 會產生下列型別 (已因應提高可讀性而稍微簡化)。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 請注意，產生的型別會遵循數個資料合約最佳做法 (位於[最佳做法：資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
- 此型別會實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
- 資料成員會實作為包裝私用欄位的公用屬性。  
  
- 此類別是部份類別，而且透過不需要修改產生之程式碼來新增項目。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> 讓您能夠進行相反的動作，也就是接受可使用 `DataContractSerializer` 序列化的型別，並產生 XSD 結構描述文件。  
  
## <a name="fidelity-is-not-guaranteed"></a>不保證精確度  
 這個類別不保證結構描述或型別在來回行程中絕對保有完整的精確度  (A*來回行程*表示匯入結構描述來建立一組類別，並匯出結果，以重新建立結構描述。)不一定會傳回相同的結構描述。 反向進行此程序時也不能保證維持精確度  (匯出型別以產生其結構描述，然後再將該型別匯入回來。 不太可能會傳回相同的型別)。  
  
## <a name="supported-types"></a>支援的型別  
 資料合約模型只支援有限的 WC3 結構描述子集。 不符合這個子集的任何結構描述，都會在匯入程序進行時造成例外狀況。 例如，沒有任何方式能夠指定資料合約的成員應該要序列化為 XML 屬性。 這樣一來，因為不可能以正確的 XML 規劃來產生資料合約，所以就不會支援需要使用 XML 屬性的結構描述，進而會在匯入期間造成例外狀況。  
  
 例如，下列結構描述片段無法使用預設的匯入設定來進行匯入。  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 如需詳細資訊，請參閱 < [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 如果結構描述不符合資料合約規則，請使用不同的序列化引擎。 例如，<xref:System.Xml.Serialization.XmlSerializer> 會使用自己的個別結構描述匯入機制。 另外，還有一種可用來擴充受支援結構描述之範圍的特殊匯入模式。 如需詳細資訊，請參閱關於產生章節<xref:System.Xml.Serialization.IXmlSerializable>中的型別[匯入結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。  
  
 `XsdDataContractExporter`支援任何.NET Framework 型別可以序列化的`DataContractSerializer`。 如需詳細資訊，請參閱 < [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。 請注意，使用 `XsdDataContractExporter` 產生的型別，通常是 `XsdDataContractImporter` 可使用的有效資料 (除非 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 是用於自訂結構描述)。  
  
 如需使用詳細資訊<xref:System.Runtime.Serialization.XsdDataContractImporter>，請參閱 <<c2> [ 匯入結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。  
  
 如需使用詳細資訊<xref:System.Runtime.Serialization.XsdDataContractExporter>，請參閱 <<c2> [ 從類別匯出的結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [匯入結構描述以產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [從類別匯出結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
