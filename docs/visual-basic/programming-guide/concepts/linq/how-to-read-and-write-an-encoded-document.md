---
title: "如何︰ 讀取和寫入編碼的文件 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
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
ms.openlocfilehash: 3247af177066e9b50d5028766f99e7bf6589050f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>如何︰ 讀取和寫入編碼的文件 (Visual Basic)
若要建立編碼的 XML 文件，您將新增<xref:System.Xml.Linq.XDeclaration>XML 樹狀結構中，設定為所要的字碼頁名稱編碼。</xref:System.Xml.Linq.XDeclaration>  
  
 傳回的任何值<xref:System.Text.Encoding.WebName%2A>是有效的值。</xref:System.Text.Encoding.WebName%2A>  
  
 如果您讀過編碼的文件，<xref:System.Xml.Linq.XDeclaration.Encoding%2A>屬性會設定為字碼頁名稱。</xref:System.Xml.Linq.XDeclaration.Encoding%2A>  
  
 如果您設定<xref:System.Xml.Linq.XDeclaration.Encoding%2A>為有效的字碼頁名稱，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]會使用指定的編碼方式序列化。</xref:System.Xml.Linq.XDeclaration.Encoding%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立兩個文件，其中一個編碼為 utf-8，而另一個編碼為 utf-16。 然後，會載入文件並將編碼方式列印至主控台。  
  
```vb  
Console.WriteLine("Creating a document with utf-8 encoding")  
Dim encodedDoc8 As XDocument = _  
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>  
        <Root>Content</Root>   
  
encodedDoc8.Save("EncodedUtf8.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Console.WriteLine("Creating a document with utf-16 encoding")  
Dim encodedDoc16 As XDocument = _  
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>  
        <Root>Content</Root>  
  
encodedDoc16.Save("EncodedUtf16.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)  
```  
  
 這個範例會產生下列輸出：  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName></xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName>   
 [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
