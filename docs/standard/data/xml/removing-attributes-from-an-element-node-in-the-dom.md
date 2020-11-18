---
title: 移除 DOM 中項目節點的屬性
ms.date: 03/30/2017
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: bd0e07f9587567de9f3023cdeda9dafde8ce7b26
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823715"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>移除 DOM 中項目節點的屬性
有許多方法可用來移除屬性。 其中一種技術是從屬性集合中移除它們。 若要如此做，請執行下列步驟：  
  
1. 使用 `XmlAttributeCollection attrs = elem.Attributes;`，從項目取得屬性集合。  
  
2. 使用下列三種方法之一，從屬性集合移除屬性：  
  
    - 使用 <xref:System.Xml.XmlAttributeCollection.Remove%2A> 移除特定屬性。  
  
    - 使用 <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> 從集合中移除所有的屬性，並保留不具屬性的項目。  
  
    - 使用 <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A>，並透過屬性的索引編號，從屬性集合中移除屬性。  
  
 下列方法可從項目節點移除屬性。  
  
- 使用 <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> 移除屬性集合。  
  
- 使用 <xref:System.Xml.XmlElement.RemoveAttribute%2A>，依名稱從集合移除單一屬性。  
  
- 使用 <xref:System.Xml.XmlElement.RemoveAttributeAt%2A>，依索引編號從集合移除單一屬性。  
  
 還有另一種替代方案是取得項目，再從屬性集合取得屬性，然後直接移除該屬性節點。 若要從屬性集合取得屬性，可以使用名稱 `XmlAttribute attr = attrs["attr_name"];` 及索引 `XmlAttribute attr = attrs[0];`，或是使用命名空間 `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]` 來完整限定名稱。  
  
 無論使用何種方法移除屬性，對移除定義為文件類型定義 (DTD) 中預設屬性的屬性都有特殊限制。 除非移除預設屬性的所屬項目，否則無法移除預設屬性。 針對已宣告預設屬性的項目，其預設屬性會永遠存在。 從 <xref:System.Xml.XmlAttributeCollection> 或 <xref:System.Xml.XmlElement> 中移除預設屬性時，會將取代屬性插入至項目的 <xref:System.Xml.XmlAttributeCollection>，並初始化為已宣告的預設值。 如果您的項目定義為 `<book att1="1" att2="2" att3="3"></book>`，則 `book` 項目會具有三個已宣告的預設屬性。 XML 文件物件模型 (DOM) 實作可保證只要此 `book` 項目存在，它就會具有三個預設屬性：`att1`、`att2` 及 `att3`。  
  
 當使用 <xref:System.Xml.XmlAttribute> 呼叫時，<xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> 方法會將屬性值設為 String.Empty，因為屬性一定要有值。  
  
## <a name="see-also"></a>請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)
