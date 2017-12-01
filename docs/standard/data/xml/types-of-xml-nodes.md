---
title: "XML 節點的型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a>XML 節點的型別
當 XML 文件讀入記憶體作為節點的樹狀時，節點建立時即會決定節點型別。 XML 文件物件模型 (DOM) 有許多種節點型別，由全球資訊網協會 (W3C) 決定並列示於＜1.1.1 DOM 架構模型＞(英文) 一節中。 下列表格會列出節點型別、指派給該節點類型的物件，以及每個節點型別的簡要說明。  
  
|DOM 節點型別|物件|描述|  
|-------------------|------------|-----------------|  
|文件|<xref:System.Xml.XmlDocument>|樹狀中所有節點的容器。 它也稱為文件根，不一定總是與根項目相同。|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|包含一或多個節點，而沒有樹狀的暫存封包。|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|表示 `<!DOCTYPE…>` 節點。|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|表示未擴充的實體參考文字。|  
|項目|<xref:System.Xml.XmlElement>|表示項目節點。|  
|Attr|<xref:System.Xml.XmlAttribute>|是項目的屬性。|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|是處理的指示節點。|  
|註解|<xref:System.Xml.XmlComment>|註解節點。|  
|Text|<xref:System.Xml.XmlText>|屬於項目或屬性的文字。|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|表示 CDATA。|  
|實體|<xref:System.Xml.XmlEntity>|表示 XML 文件中的 `<!ENTITY…>` 宣告，可能來自內部文件類型定義 (DTD) 子集，或來自外部 DTD 和參數實體。|  
|Notation|<xref:System.Xml.XmlNotation>|表示 DTD 中宣告的標記法。|  
  
 即使屬性 (*attr*) 會列在 W3C DOM 層級 1 1.2 節 < Fundamental Interfaces > 的節點，其會被視為任何項目節點的子系。  
  
 下表顯示 w3c 未定義的其他節點型別，但在可供使用，做為 Microsoft.NET Framework 物件模型中**XmlNodeType**列舉型別。 因此，這些節點型別沒有相符的 DOM 節點型別資料行。  
  
|節點類型|描述|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|表示宣告節點 `<?xml version="1.0"…>`。|  
|<xref:System.Xml.XmlSignificantWhitespace>|表示顯著的空白字元，這是混合內容中的空白字元。|  
|<xref:System.Xml.XmlWhitespace>|表示項目內容中的泛空白字元。|  
|EndElement|傳回當**XmlReader**取得項目的結尾。<br /><br /> 範例 XML:  **\< /項目 >**<br /><br /> 如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。|  
|EndEntity|傳回當**XmlReader**到達實體取代，由於呼叫的結尾<xref:System.Xml.XmlReader.ResolveEntity%2A>。 如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。|  
  
 若要檢視來讀取 XML，並使用的案例建構來列印節點和其內容的相關資訊的節點型別上的程式碼範例，請參閱<xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>。  
  
 節點型別和其對等的物件名稱的物件階層架構資訊，請參閱[XML 文件物件模型 (DOM) 階層](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)。 如需在節點樹狀目錄中建立之物件的詳細資訊，請參閱[將物件階層架構對應至 XML 資料](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
