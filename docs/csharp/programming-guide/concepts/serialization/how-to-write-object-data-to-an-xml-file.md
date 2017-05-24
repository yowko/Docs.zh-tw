---
title: "如何：將物件資料寫入 XML 檔案 (C#) | Microsoft Docs"
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
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 197e91be6d3785e437cb33541b2b4c9b4a2cbb84
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>如何：將物件資料寫入 XML 檔案 (C#)
此範例使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。  
  
## <a name="example"></a>範例  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 此類別必須有不具參數的公用建構函式。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   正在序列化的類別沒有公用的無參數建構函式。  
  
-   此檔案存在而且是唯讀 (<xref:System.IO.IOException>)。  
  
-   路徑太長 (<xref:System.IO.PathTooLongException>)。  
  
-   磁碟已滿 (<xref:System.IO.IOException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。 如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter>   
 [如何：從 XML 檔案讀取物件資料 (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [序列化 (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)
