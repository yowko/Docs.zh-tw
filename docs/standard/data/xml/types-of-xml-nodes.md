---
title: XML 節點的型別
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623583f16c23b55c16f648fedcd039ca36f73b1f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45597611"
---
# <a name="types-of-xml-nodes"></a>XML 節點的型別
當 XML 文件讀入記憶體作為節點的樹狀時，節點建立時即會決定節點型別。 XML 文件物件模型 (DOM) 有許多種節點型別，由全球資訊網協會 (W3C) 決定並列示於＜1.1.1 DOM 架構模型＞(英文) 一節中。 下列表格會列出節點型別、指派給該節點類型的物件，以及每個節點型別的簡要說明。  
  
|DOM 節點型別|Object|描述|  
|-------------------|------------|-----------------|  
|文件|<xref:System.Xml.XmlDocument>|樹狀中所有節點的容器。 它也稱為文件根，不一定總是與根項目相同。|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|包含一或多個節點，而沒有樹狀的暫存封包。|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|表示 `<!DOCTYPE…>` 節點。|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|表示未擴充的實體參考文字。|  
|元素|<xref:System.Xml.XmlElement>|表示項目節點。|  
|Attr|<xref:System.Xml.XmlAttribute>|是項目的屬性。|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|是處理的指示節點。|  
|註解|<xref:System.Xml.XmlComment>|註解節點。|  
|Text|<xref:System.Xml.XmlText>|屬於項目或屬性的文字。|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|表示 CDATA。|  
|實體|<xref:System.Xml.XmlEntity>|表示 XML 文件中的 `<!ENTITY…>` 宣告，可能來自內部文件類型定義 (DTD) 子集，或來自外部 DTD 和參數實體。|  
|Notation|<xref:System.Xml.XmlNotation>|表示 DTD 中宣告的標記法。|  
  
 即使屬性 (*attr*) 在 W3C DOM Level 1 的 1.2 節＜Fundamental Interfaces＞中列示為節點，但仍不會將其視為任何項目節點的子系。  
  
 下表列出的是 W3C 未定義的其他節點型別，但您可以在 Microsoft .NET Framework 物件模型中將它們當作 **XmlNodeType** 列舉型別使用。 因此，這些節點型別沒有相符的 DOM 節點型別資料行。  
  
|節點類型|描述|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|表示宣告節點 `<?xml version="1.0"…>`。|  
|<xref:System.Xml.XmlSignificantWhitespace>|表示顯著的空白字元，這是混合內容中的空白字元。|  
|<xref:System.Xml.XmlWhitespace>|表示項目內容中的泛空白字元。|  
|EndElement|當 **XmlReader** 到達項目的結尾時返回。<br /><br /> 範例 XML：**\</item>**<br /><br /> 如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。|  
|EndEntity|由於呼叫 <xref:System.Xml.XmlReader.ResolveEntity%2A> 而使 **XmlReader** 到達實體取代的結尾時會返回。 如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。|  
  
 若要檢視可讀取 XML，且使用節點型別上的案例建構來列印節點和其內容相關資訊的程式碼範例，請參閱 <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>。  
  
 如需節點型別的物件階層架構和其對等的物件名稱之詳細資訊，請參閱 [XML 文件物件模型 (DOM) 階層架構](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)。 如需在節點樹狀結構中建立之物件的詳細資訊，請參閱[將物件階層架構對應至 XML 資料](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
