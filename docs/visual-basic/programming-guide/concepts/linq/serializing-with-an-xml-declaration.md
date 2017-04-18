---
title: "序列化使用 XML 宣告 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
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
ms.openlocfilehash: 373df9b28ae7434d33ae81eba701d289cf1aa4f7
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>使用 XML 宣告 (Visual Basic) 進行序列化
這個主題描述如何控制序列化是否產生 XML 宣告。  
  
## <a name="xml-declaration-generation"></a>XML 宣告產生  
 序列化至<xref:System.IO.File>或<xref:System.IO.TextWriter>使用<xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>方法或<xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>方法會產生 XML 宣告。</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> </xref:System.IO.TextWriter> </xref:System.IO.File> 當您序列化<xref:System.Xml.XmlWriter>，寫入器設定 (在指定<xref:System.Xml.XmlWriterSettings>物件) 決定是否產生 XML 宣告。</xref:System.Xml.XmlWriterSettings> </xref:System.Xml.XmlWriter>  
  
 如果您要使用 `ToString` 方法序列化為字串，所產生的 XML 將不會包含 XML 宣告。  
  
### <a name="serializing-with-an-xml-declaration"></a>使用 XML 宣告進行序列化  
 下列範例會建立<xref:System.Xml.Linq.XElement>，將文件儲存至檔案，然後會列印到主控台檔案︰</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>不使用 XML 宣告序列化  
 下列範例顯示如何將儲存<xref:System.Xml.Linq.XElement>至<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XElement>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>另請參閱  
 [序列化 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
