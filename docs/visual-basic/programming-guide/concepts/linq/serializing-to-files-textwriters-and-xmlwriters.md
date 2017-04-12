---
title: "序列化至檔案、 Textwriter 和 XmlWriters3 |Microsoft 文件"
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 98662b8d84459ed051d048084c2755fa7aaf8247
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>序列化至 File、TextWriter 和 XmlWriter
您可以序列化到 XML 樹狀結構<xref:System.IO.File>、 <xref:System.IO.TextWriter>，或<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 您可以將序列化的任何 XML 元件，包括<xref:System.Xml.Linq.XDocument>和<xref:System.Xml.Linq.XElement>，使用字串`ToString`方法。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 如果您想要序列化為字串時隱藏格式，您可以使用<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>  
  
 當序列化至檔案的 Thedefault 行為是格式化 （縮排） 所產生的 XML 文件。 當您縮排時，不會保留 XML 樹狀中的無效空白字元。 若要使用格式序列化，請使用未採用下列方法的多載<xref:System.Xml.Linq.SaveOptions>做為引數︰</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 如果您想要選擇不縮排和不保留空白字元 XML 樹狀結構中，使用其中一個會採用下列方法的多載<xref:System.Xml.Linq.SaveOptions>做為引數︰</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 如需範例，請參閱適當的參考主題。  
  
## <a name="see-also"></a>另請參閱  
 [序列化 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
