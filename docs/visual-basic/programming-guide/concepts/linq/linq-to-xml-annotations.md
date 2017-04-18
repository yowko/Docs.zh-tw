---
title: "LINQ to XML Annotations2 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f2e5bea1cde74548daa1697b6a0a819e3eba3e4
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>LINQ to XML 註釋
中的註解[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]可讓您將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。  
  
 若要將註解加入到 XML 元件，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>，您呼叫<xref:System.Xml.Linq.XObject.AddAnnotation%2A>方法。</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 您可以按照型別擷取附註。  
  
 請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。  
  
## <a name="methods"></a>方法  
 使用附註時，您可以使用下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A>|將物件加入至<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>註解清單|  
|<xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A>|取得指定之型別的第一個附註物件從<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A>|取得指定之型別的附註集合<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|從<xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>移除指定之型別的附註|  
  
## <a name="see-also"></a>另請參閱  
 [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
