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
ms.openlocfilehash: 52a9e1bf4c9442bd42beb55b133a185c4a42148d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288561"
---
# <a name="schema-import-and-export"></a>結構描述匯入和匯出

Windows Communication Foundation (WCF) 包含新的序列化引擎 <xref:System.Runtime.Serialization.DataContractSerializer> 。 `DataContractSerializer`在 .NET Framework 物件和 XML (的雙向轉譯) 。 除了序列化程式本身之外，WCF 還包含相關聯的架構匯入和架構匯出機制。 *架構* 是序列化程式所產生或還原序列化程式可以存取之 XML 圖形的正式、精確和機器可讀取的描述。 WCF 使用全球資訊網協會 (W3C) XML 架構定義語言 (XSD) 做為其架構標記法，這與許多協力廠商平臺有很大的互通性。  
  
 架構匯入元件 <xref:System.Runtime.Serialization.XsdDataContractImporter> 會採用 XSD 架構檔，並產生 (一般資料合約類別的 .NET Framework 類別) 讓序列化的表單對應到指定的架構。  
  
 例如，下列結構描述片段：  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 會產生下列型別 (已因應提高可讀性而稍微簡化)。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 請注意，產生的型別會遵循數種資料合約最佳做法 (在 [最佳做法中找到：資料合約版本](../best-practices-data-contract-versioning.md) 設定) ：  
  
- 此型別會實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。 如需詳細資訊，請參閱[向前相容資料合約](forward-compatible-data-contracts.md)。  
  
- 資料成員會實作為包裝私用欄位的公用屬性。  
  
- 此類別是部份類別，而且透過不需要修改產生之程式碼來新增項目。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> 讓您能夠進行相反的動作，也就是接受可使用 `DataContractSerializer` 序列化的型別，並產生 XSD 結構描述文件。  
  
## <a name="fidelity-is-not-guaranteed"></a>不保證精確度  

 這個類別不保證結構描述或型別在來回行程中絕對保有完整的精確度   (*來回行程* 表示匯入架構以建立一組類別，並匯出結果以再次建立架構 ) 。可能不會傳回相同的架構。 反向進行此程序時也不能保證維持精確度  (匯出型別以產生其結構描述，然後再將該型別匯入回來。 不太可能會傳回相同的型別)。  
  
## <a name="supported-types"></a>支援的型別  

 資料合約模型只支援有限的 WC3 結構描述子集。 不符合這個子集的任何結構描述，都會在匯入程序進行時造成例外狀況。 例如，沒有任何方式能夠指定資料合約的成員應該要序列化為 XML 屬性。 這樣一來，因為不可能以正確的 XML 規劃來產生資料合約，所以就不會支援需要使用 XML 屬性的結構描述，進而會在匯入期間造成例外狀況。  
  
 例如，下列結構描述片段無法使用預設的匯入設定來進行匯入。  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 如需詳細資訊，請參閱 [資料合約架構參考](data-contract-schema-reference.md)。 如果結構描述不符合資料合約規則，請使用不同的序列化引擎。 例如，<xref:System.Xml.Serialization.XmlSerializer> 會使用自己的個別結構描述匯入機制。 另外，還有一種可用來擴充受支援結構描述之範圍的特殊匯入模式。 如需詳細資訊，請參閱在匯 <xref:System.Xml.Serialization.IXmlSerializable> 入架構中產生類型 [以產生類別](importing-schema-to-generate-classes.md)一節。  
  
 `XsdDataContractExporter`支援任何可利用序列化的 .NET Framework 類型 `DataContractSerializer` 。 如需詳細資訊，請參閱 [資料合約序列化程式支援的類型](types-supported-by-the-data-contract-serializer.md)。 請注意，使用 `XsdDataContractExporter` 產生的型別，通常是 `XsdDataContractImporter` 可使用的有效資料 (除非 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 是用於自訂結構描述)。  
  
 如需使用的詳細資訊 <xref:System.Runtime.Serialization.XsdDataContractImporter> ，請參閱匯 [入架構以產生類別](importing-schema-to-generate-classes.md)。  
  
 如需使用的詳細資訊 <xref:System.Runtime.Serialization.XsdDataContractExporter> ，請參閱 [從類別匯出架構](exporting-schemas-from-classes.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [匯入結構描述以產生類別](importing-schema-to-generate-classes.md)
- [從類別匯出結構描述](exporting-schemas-from-classes.md)
