---
title: 使用 XPathNavigator 巡覽節點集
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618098"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>使用 XPathNavigator 巡覽節點集
您可以使用 <xref:System.Xml.XPath.XPathDocument> 類別的節點集巡覽方法，巡覽 <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XPath.XPathNavigator> 物件中的節點。 您可以巡覽所有節點或由 <xref:System.Xml.XPath.XPathNavigator> 類別的其中一個選取方法傳回的選定節點集。  
  
## <a name="element-node-set-navigation"></a>項目節點集巡覽  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供可用於巡覽項目節點的數種方法。 下表顯示可用的巡覽方法及其移動方式的說明；但不包括可用於巡覽屬性及命名空間節點的方法。  
  
 如需有關選取 <xref:System.Xml.XPath.XPathNavigator> 物件中之節點的詳細資訊，請參閱[使用 XPathNavigator 選取、評估與比對 XML 資料](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)。 如需有關巡覽屬性和命名空間節點的詳細資訊，請參閱[使用 XPathNavigator 巡覽屬性及命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)。  
  
|方法|說明|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至與指定之 <xref:System.Xml.XPath.XPathNavigator> 相同的位置。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的子節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的第一個同層級節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的第一個子節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至文件順序中指定的項目。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至屬性型別為 `ID` 且值符合給定 <xref:System.String> 的節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的下一個同層級節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的父節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至目前節點的前一個同層級節點。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|將 <xref:System.Xml.XPath.XPathNavigator> 移至 XML 文件的根節點。|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>註解及處理指示節點巡覽  
 下列 <xref:System.Xml.XPath.XPathNavigator> 類別方法適用於從 XML 文件中的其他節點移至註解或處理指示。  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [使用 XPathNavigator 導覽屬性和命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [使用 XPathNavigator 擷取 XML 資料](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 存取強型別 XML 資料](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
