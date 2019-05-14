---
title: 在 XPath 查詢中辨識的節點型別
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa004f0def04c7efe2ba7450050a899760b0bbcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590198"
---
# <a name="node-types-recognized-with-xpath-queries"></a>在 XPath 查詢中辨識的節點型別
在 XPath 查詢中辨識的節點型別不同於在文件物件模型 (DOM) 中找到的節點型別。  
  
## <a name="w3c-xpath-node-types"></a>W3C XPath 節點型別  
 在 XPath 查詢中辨識的節點型別並非在文件物件模型 (DOM) 中找到的節點型別。 以下是由 <xref:System.Xml.XPath.XPathNodeType> 列舉表示的 XPath 節點型別。  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 這些節點型別以 XPath 資料模型為基礎，其中節點均衍生自 XML 資訊集。 <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> 及 <xref:System.Xml.XPath.XPathNodeType.Whitespace> 節點型別是 XPath 資料模型中所說明之基底節點型別的 Microsoft .NET Framework 擴充功能。  
  
 屬性節點型別在 XPath 資料模型中的使用方式與在 DOM 中的不同。 在 XPath 資料模型中，項目節點具有相關的屬性節點集，且項目節點是每個屬性節點的父代。 不過，在 DOM 中，項目節點是擁有者，並不是父代。 在這兩個模型中，屬性及命名空間節點都不被視為項目節點的子節點。  
  
 命名空間節點型別是 XPath 資料模型中的新加入型別，並不是可辨識的 DOM 節點型別。  
  
 如需有關巡覽項目、屬性和命名空間節點的詳細資訊，請參閱[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)以及[使用 XPathNavigator 巡覽屬性及命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)主題。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [使用 XPathNavigator 選取 XML 資料](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 評估 XPath 運算式](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [使用 XPathNavigator 比對節點](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [XPath 查詢和命名空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [編譯 XPath 運算式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
