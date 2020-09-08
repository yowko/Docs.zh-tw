---
title: LINQ to XML 軸總覽-LINQ to XML
description: 使用 System.xml.linq.xelement>、XDocument 和 IEnumerable 類別中的座標軸方法來尋找 XML 樹狀結構中的元素，並取出其值。
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: dd4018bbce52000bece4f737368b3807d229714a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552235"
---
# <a name="linq-to-xml-axes-overview"></a>LINQ to XML 軸總覽

當您建立 XML 樹狀結構，或將 XML 檔載入至 XML 樹狀結構之後，您可以查詢它來尋找元素和屬性，並取得其值。 您可以透過「座標軸方法」** 擷取集合，也稱為「座標軸」**。 有些座標軸是 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中，傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合的方法。 有些座標軸是 <xref:System.Xml.Linq.Extensions> 類別中的擴充方法。 實作為擴充方法的座標軸會在集合和傳回集合上運作。

如 [system.xml.linq.xelement> 類別總覽](xelement-class-overview.md)中所述， <xref:System.Xml.Linq.XElement> 物件代表單一元素節點。 項目的內容可能很複雜 (有時候稱為結構化的內容)，或者，它可能是簡單的項目。 簡單的項目可以是空的，也可以包含值。 如果節點包含結構化的內容，您可以使用各種座標軸方法來擷取子代項目的列舉。 最常使用的座標軸方法為 <xref:System.Xml.Linq.XContainer.Elements%2A> 和 <xref:System.Xml.Linq.XContainer.Descendants%2A>。

除了會傳回集合的座標軸方法之外，還有兩種方法，您通常會在 LINQ to XML 查詢中使用這些方法。 <xref:System.Xml.Linq.XContainer.Element%2A> 方法會傳回單一的 <xref:System.Xml.Linq.XElement>。 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法會傳回單一的 <xref:System.Xml.Linq.XAttribute>。

基於許多用途，LINQ 查詢提供最強大的方式來檢查樹狀結構、從中解壓縮資料，以及轉換它。 LINQ 查詢會在執行的物件上運作 <xref:System.Collections.Generic.IEnumerable%601> ，而且會傳回集合的 LINQ to XML 軸和集合的集合 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> 。 您需要這些集合來進行查詢。

除了擷取項目和屬性之集合的座標軸方法之外，還有其他座標軸方法可讓您仔細逐一查看樹狀結構。 例如，您可以使用樹狀結構的節點，而不是處理項目和屬性。 這些節點是比項目和屬性還要細微的位移單位等級。 使用節點時，您可以檢查 XML 註解、文字節點、處理指示等等。 這個功能對於撰寫字組處理器與想要將文件另存為 XML 之類的人而言，相當重要。 不過，多數的 XML 程式設計人員關心的都是項目、屬性及其值。

## <a name="methods-for-retrieving-a-collection-of-elements"></a>用來取得元素集合的方法

下列為 <xref:System.Xml.Linq.XElement> 類別 (或其基礎類別) 之方法的摘要，您可以在 <xref:System.Xml.Linq.XElement> 上呼叫這些方法來傳回項目的集合。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|傳回此項目祖系之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回其祖系具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|傳回此項目子代之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回其子代具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|傳回此項目的子項目之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回其子項目具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|傳回此項目後的項目之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的這個項目後之項目的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|傳回此項目前的項目之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的這個項目前之項目的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|傳回此項目及其祖系之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回其項目具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|傳回此項目及其子代之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>。 多載會傳回其項目具有指定之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 之 <xref:System.Xml.Linq.XName>。|

## <a name="method-for-retrieving-a-single-element"></a>用來取得單一元素的方法

下列方法會從 <xref:System.Xml.Linq.XElement> 物件擷取單一子系。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|傳回具有指定之 <xref:System.Xml.Linq.XElement> 的第一個 <xref:System.Xml.Linq.XName> 子物件。|

## <a name="method-for-retrieving-a-collection-of-attributes"></a>用來取得屬性集合的方法

下列方法會從 <xref:System.Xml.Linq.XElement> 物件擷取屬性。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|傳回所有屬性之 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XAttribute>。|

## <a name="method-for-retrieving-a-single-attribute"></a>用於取出單一屬性的方法

下列方法會從 <xref:System.Xml.Linq.XElement> 物件擷取單一屬性。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|傳回具有指定之 <xref:System.Xml.Linq.XAttribute> 的 <xref:System.Xml.Linq.XName>。|
