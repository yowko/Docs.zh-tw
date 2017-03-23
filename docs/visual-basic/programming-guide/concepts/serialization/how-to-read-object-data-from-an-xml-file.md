---
title: "如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料 |Microsoft 文件"
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
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
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
ms.openlocfilehash: c448d79a88517925712f79ed061aa90933e3f6d1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>如何︰ 讀取 XML 檔案 (Visual Basic) 的物件資料
這個範例會讀取物件資料的先前寫入 XML 檔案中使用<xref:System.Xml.Serialization.XmlSerializer>類別。</xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="example"></a>範例  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 包含序列化的資料的檔案名稱來取代檔案名稱"c:\temp\SerializationOverview.xml"。 如需序列化資料的詳細資訊，請參閱[How to︰ 將物件資料寫入至 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。  
  
 這個類別必須具有不含參數的公用建構函式。  
  
 只有公用屬性和欄位會還原序列化。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   序列化的類別沒有公用的無參數建構函式。  
  
-   檔案中的資料不代表類別，以還原序列化的資料。  
  
-   檔案不存在 (<xref:System.IO.IOException>)。</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 永遠會先驗證輸入，並永遠不會還原序列化來自不受信任來源的資料。 重新建立的物件會還原序列化它的程式碼的權限的本機電腦上執行。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [如何︰ 將物件資料寫入至 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [序列化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)
