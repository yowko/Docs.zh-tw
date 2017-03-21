---
title: "如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic) |Microsoft 文件"
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
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 146ccb7b1999049106d5f0be1ce78e740dfcf060
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic)
除非範例類別將物件寫入 XML 檔案中使用<xref:System.Xml.Serialization.XmlSerializer>類別。</xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="example"></a>範例  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個類別必須具有不含參數的公用建構函式。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   序列化的類別沒有公用的無參數建構函式。  
  
-   該檔案存在，而且是唯讀的 (<xref:System.IO.IOException>)。</xref:System.IO.IOException>  
  
-   路徑過長 (<xref:System.IO.PathTooLongException>)。</xref:System.IO.PathTooLongException>  
  
-   磁碟已滿 (<xref:System.IO.IOException>)。</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果檔案已經存在，這個範例會建立新的檔案。 如果必須建立檔案的應用程式，該應用程式需要`Create`資料夾的存取。 如果檔案已經存在，應用程式只需要`Write`存取，較低權限。 如果可行的話，會在部署期間，建立檔案，並僅授與更安全`Read`存取單一檔案，而非`Create`資料夾的存取權。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [序列化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
