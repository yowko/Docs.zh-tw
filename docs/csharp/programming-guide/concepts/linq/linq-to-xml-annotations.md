---
title: LINQ to XML 註釋
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 8b8e03b0174ad2bf044c21eb9a9d3391da37fb7f
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960695"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML 註釋
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的註釋可讓您將任意型別的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。  
  
 若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。 您可以按照型別擷取附註。  
  
 請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。  
  
## <a name="methods"></a>方法  
 使用附註時，您可以使用下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。|  
  
## <a name="see-also"></a>請參閱  
 [進階 LINQ to XML 程式設計 (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
