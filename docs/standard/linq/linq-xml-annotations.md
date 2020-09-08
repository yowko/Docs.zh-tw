---
title: 批註-LINQ to XML
description: 瞭解如何使用 LINQ to XML 中的注釋，將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552240"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a>LINQ to XML 注釋 (LINQ to XML) 

LINQ to XML 中的批註可讓您將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。

若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。 您可以按照型別擷取附註。

請注意，批註不是 XML 資訊集的一部分;它們未序列化或還原序列化。

## <a name="methods"></a>方法

使用附註時，您可以使用下列方法：

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。|
