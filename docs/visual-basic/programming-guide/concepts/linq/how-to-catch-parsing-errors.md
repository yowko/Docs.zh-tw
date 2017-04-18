---
title: "如何︰ 攔截剖析錯誤 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
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
ms.openlocfilehash: 0c4ba619d1f269352b3288f6cadf3b6f37a0dc2d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>如何︰ 攔截剖析錯誤 (Visual Basic)
這個主題顯示如何偵測格式錯誤或無效的 XML。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]使用<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>實作 如果將格式錯誤或無效的 XML 傳遞到[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，基礎<xref:System.Xml.XmlReader>類別將會擲回例外狀況。</xref:System.Xml.XmlReader> 這類剖析 XML 的各種方法<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>，不會攔截例外狀況，然後根據您的應用程式攔截例外狀況。</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
 請注意，如果您使用 XML 常值，就無法取得剖析錯誤。 Visual Basic 編譯器將會攔截格式錯誤或無效 XML 的錯誤。  
  
## <a name="example"></a>範例  
 下列程式碼嘗試剖析無效的 XML：  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 執行此程式碼時，它會擲回例外狀況：  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 如需有關您可以預期的例外狀況資訊<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>， <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>， <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>，和<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>方法擲回，請參閱<xref:System.Xml.XmlReader>文件。</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
