---
title: 如何使用 XmlSerializer 還原序列化物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c24ba466a208fe5abdbf565169c41c4ee3f47482
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559894"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>如何使用 XmlSerializer 還原序列化物件

當您還原序列化物件時，傳輸格式決定您會建立資料流或檔案物件。 決定傳輸格式後，您可視需要呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。

## <a name="to-deserialize-an-object"></a>還原序列化物件

1. 使用要還原序列化的物件型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。

1. 呼叫 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以產生物件的複本。 還原序列化時，您必須將傳回的物件轉換為原始的類型，如下列範例所示，它會從檔案還原序列化物件（雖然也可以從資料流程還原序列化）。

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a>請參閱

- [XML 序列化簡介](introducing-xml-serialization.md)
- [如何：序列化物件](how-to-serialize-an-object.md)
