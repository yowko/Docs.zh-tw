---
title: 使用 XPathNavigator 巡覽屬性及命名空間節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd3b1cacc73743622aaaad72bfd4edb26dc26390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740472"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>使用 XPathNavigator 巡覽屬性及命名空間節點
<xref:System.Xml.XPath.XPathNavigator> 類別提供兩組巡覽方法，第一組 (可在[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)主題中找到) 用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的*節點集*。 第二組 (在本主題中說明) 用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的「屬性及命名空間節點」。  
  
## <a name="attribute-node-navigation"></a>屬性節點巡覽  
 屬性 (Attribute) 是項目的屬性 (Property)，而不是項目的子系。 這個差別是很重要的，因為這關係到用來巡覽同層級節點、父節點及子節點之 <xref:System.Xml.XPath.XPathNavigator> 類別的方法。  
  
 例如，<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 方法無法用來從項目巡覽到屬性，或在屬性之間巡覽。 應改用不同的方法來巡覽屬性。  
  
 以下是 <xref:System.Xml.XPath.XPathNavigator> 類別的屬性巡覽方法。  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 當目前的節點為項目時，您可以使用 <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> 屬性 (Property)，來查看是否有與項目相關的屬性 (Attribute)。 一旦知道項目有屬性，就有多種存取屬性的方法。 若要從項目擷取單一屬性，請使用 <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> 方法。 若要將 <xref:System.Xml.XPath.XPathNavigator> 移至特定的屬性，請使用 <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> 方法。 您還可以重複處理項目的每個屬性，方法是使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> 方法，然後多次呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> 方法。  
  
> [!NOTE]
>  當 <xref:System.Xml.XPath.XPathNavigator> 物件定位於屬性或命名空間節點上時，<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 和 <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 方法一律會傳回 `false`，且對 <xref:System.Xml.XPath.XPathNavigator> 的位置毫無影響。 <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> 方法則例外。  
  
## <a name="namespace-node-navigation"></a>命名空間節點巡覽  
 每個項目都有一組相關聯的命名空間節點，一個用於每個與此項目範圍內命名空間 URI 繫結的個別命名空間前置詞 (包括繫結至 `http://www.w3.org/XML/1998/namespace` 命名空間的 XML 前置詞，其在每個 XML 文件中隱含宣告)，另一個用於預設命名空間 (若命名空間節點位於此項目的範圍內)。 此項目為上述每個命名空間節點的父代；但命名空間節點並非其父項目的子系。  
  
 與屬性一樣，<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 方法無法用來從項目巡覽到命名空間節點，或在命名空間節點之間巡覽。 而是命名空間節點具有不同的巡覽方法。  
  
 以下是 <xref:System.Xml.XPath.XPathNavigator> 類別的命名空間巡覽方法。  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 在 XML 文件中，任何項目的範圍內總是至少有一個命名空間節點。 此命名空間節點具有前置詞 `xml` 及命名空間 URI `http://www.w3.org/XML/1998/namespace`。 若要在給定特定前置詞的情況下，擷取範圍內的命名空間 URI，請使用 <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> 方法。 若要將 <xref:System.Xml.XPath.XPathNavigator> 物件移至特定的命名空間節點，請使用 <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> 方法。 您還可以重複處理項目範圍內的每個命名空間節點，方法是使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法，然後多次呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 方法。  
  
> [!NOTE]
>  當 <xref:System.Xml.XPath.XPathNavigator> 物件定位於屬性或命名空間節點上時，<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 和 <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 方法一律會傳回 `false`，且對 <xref:System.Xml.XPath.XPathNavigator> 的位置毫無影響。 <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> 方法則例外。  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope 列舉型別  
 巡覽命名空間節點時，可使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 參數呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 及 <xref:System.Xml.XPath.XPathNamespaceScope> 方法。 這些方法的行為模式，與其不使用參數呼叫的對應方法不同。 <xref:System.Xml.XPath.XPathNamespaceScope> 列舉型別具有值 <xref:System.Xml.XPath.XPathNamespaceScope.All>、<xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> 或 <xref:System.Xml.XPath.XPathNamespaceScope.Local>。  
  
 下列範例顯示在 XML 文件的不同範圍由 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 方法傳回的命名空間。  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 命名空間序列 (在呼叫 <xref:System.Xml.XPath.XPathNavigator> 方法，然後對 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法進行一系列呼叫之後，<xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 所在的命名空間) 如下所示。  
  
-   當定位於 `element2` 上時：`xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` 和 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。  
  
-   當定位於 `element1` 上時：`xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` 和 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。  
  
-   當定位於 `root` 上時：`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> 類別會以反向的文件順序傳回命名空間節點。 因此，<xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 實際上會移至目前範圍中的最後一個命名空間節點。  
  
 下列範例顯示在 XML 文件的不同範圍指定了 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 列舉型別時，由 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 及 <xref:System.Xml.XPath.XPathNamespaceScope> 方法傳回的命名空間。  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 當定位於 `child2` 時，命名空間序列 (在呼叫 <xref:System.Xml.XPath.XPathNavigator> 方法，然後對 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法進行一系列呼叫之後，<xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 所在的命名空間) 如下所示。  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All>：`xmlns:c="urn:c"`、`xmlns:a="urn:a"`、`xmlns=""`、`xmlns:b="http://www.contoso.com/b"`、`xmlns:a="http://www.contoso.com/a"`、`xmlns="http://www.contoso.com"` 及 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>：`xmlns:c="urn:c"`、`xmlns:a="urn:a"`、`xmlns=""`、`xmlns:b="http://www.contoso.com/b"`、`xmlns:a="http://www.contoso.com/a"` 及 `xmlns="http://www.contoso.com"`。  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> 類別會以反向的文件順序傳回命名空間節點。 因此，<xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 實際上會移至目前範圍中的最後一個命名空間節點。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [使用 XPathNavigator 導覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [使用 XPathNavigator 擷取 XML 資料](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [使用 XPathNavigator 存取強型別 XML 資料](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
