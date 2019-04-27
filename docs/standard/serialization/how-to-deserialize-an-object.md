---
title: HOW TO：將物件還原序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: 53b4a3e3848c1aa92bfa9fbd80bb031125257fc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922716"
---
# <a name="how-to-deserialize-an-object"></a><span data-ttu-id="f7af9-102">HOW TO：將物件還原序列化</span><span class="sxs-lookup"><span data-stu-id="f7af9-102">How to: Deserialize an Object</span></span>
<span data-ttu-id="f7af9-103">當您還原序列化物件時，傳輸格式決定您會建立資料流或檔案物件。</span><span class="sxs-lookup"><span data-stu-id="f7af9-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="f7af9-104">決定傳輸格式後，您可視需要呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f7af9-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="f7af9-105">還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="f7af9-105">To deserialize an object</span></span>  
  
1. <span data-ttu-id="f7af9-106">使用要還原序列化的物件型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="f7af9-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>  
  
2. <span data-ttu-id="f7af9-107">呼叫 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以產生物件的複本。</span><span class="sxs-lookup"><span data-stu-id="f7af9-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="f7af9-108">在還原序列化時，您必須將傳回之物件轉換為原始的型別，如下面的範例所示，將物件還原序列化為檔案 (不過它也能還原序列化成資料流)。</span><span class="sxs-lookup"><span data-stu-id="f7af9-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object into a file (although it could also be deserialized into a stream).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7af9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7af9-109">See also</span></span>

- [<span data-ttu-id="f7af9-110">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="f7af9-110">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="f7af9-111">如何：將物件序列化</span><span class="sxs-lookup"><span data-stu-id="f7af9-111">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
