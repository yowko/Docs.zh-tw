---
title: "如何：從 XML 檔案讀取物件資料 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c5f8c23a86c7a09d6f8d0b8c6f1684a38d0336a3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>如何：從 XML 檔案讀取物件資料 (C#)
此範例使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，讀取先前寫入 XML 檔案的物件資料。  
  
## <a name="example"></a>範例  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 以內含序列化資料之檔案的名稱取代檔案名稱 "c:\temp\SerializationOverview.xml"。 如需序列化資料的詳細資訊，請參閱[如何：將物件資料寫入 XML 檔案 (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)。  
  
 此類別必須有不具參數的公用建構函式。  
  
 只會還原序列化公用屬性和欄位。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   正在序列化的類別沒有公用的無參數建構函式。  
  
-   檔案中的資料不是來自要還原序列化之類別的資料。  
  
-   檔案不存在 (<xref:System.IO.IOException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 永遠會驗證輸入，而且絕不會還原序列化來自未受信任來源的資料。 重新建立的物件會以還原序列化該物件之程式碼的權限，在本機電腦上執行。 在應用程式中使用這些資料之前，請先驗證所有輸入值。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter>   
 [如何：將物件資料寫入 XML 檔案 (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [序列化 (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)   
 [C# 程式設計指南](../../../../csharp/programming-guide/index.md)
