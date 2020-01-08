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
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="87646-102">如何使用 XmlSerializer 還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="87646-102">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="87646-103">當您還原序列化物件時，傳輸格式決定您會建立資料流或檔案物件。</span><span class="sxs-lookup"><span data-stu-id="87646-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="87646-104">決定傳輸格式後，您可視需要呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 或 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="87646-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="87646-105">還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="87646-105">To deserialize an object</span></span>

1. <span data-ttu-id="87646-106">使用要還原序列化的物件型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="87646-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="87646-107">呼叫 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> 方法以產生物件的複本。</span><span class="sxs-lookup"><span data-stu-id="87646-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="87646-108">還原序列化時，您必須將傳回的物件轉換為原始的類型，如下列範例所示，它會從檔案還原序列化物件（雖然也可以從資料流程還原序列化）。</span><span class="sxs-lookup"><span data-stu-id="87646-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="87646-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="87646-109">See also</span></span>

- [<span data-ttu-id="87646-110">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="87646-110">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="87646-111">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="87646-111">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
