---
title: 作法：將物件還原序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e1a960d39319beee1c3c257fcd3ade207de11010
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881132"
---
# <a name="how-to-deserialize-an-object"></a>作法：將物件還原序列化
當您還原序列化物件時，傳輸格式決定您會建立資料流或檔案物件。 決定傳輸格式後，您可視需要呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。  
  
### <a name="to-deserialize-an-object"></a>還原序列化物件  
  
1. 使用要還原序列化的物件型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。  
  
2. 呼叫 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以產生物件的複本。 還原序列化時，您必須先轉換原始的型別傳回的物件，如下列的範例中，（雖然它也可還原序列化從資料流），還原序列化的物件，從檔案中所示。  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>另請參閱

- [XML 序列化簡介](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [如何：將物件序列化](../../../docs/standard/serialization/how-to-serialize-an-object.md)
