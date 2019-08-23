---
title: 作法：序列化物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928976"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="42e9c-102">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="42e9c-102">How to: Serialize an Object</span></span>
<span data-ttu-id="42e9c-103">若要序列化物件，首先建立要序列化的物件，並設定其公用屬性與欄位。</span><span class="sxs-lookup"><span data-stu-id="42e9c-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="42e9c-104">若要執行這項作業，您必須判斷 XML 資料流儲存 (無論是資料流或檔案) 的傳輸格式。</span><span class="sxs-lookup"><span data-stu-id="42e9c-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="42e9c-105">例如，若 XML 資料流必須以永久形式儲存，請建立 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="42e9c-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42e9c-106">如需 XML 序列化的其他範例，請參閱 [XML 序列化的範例](../../../docs/standard/serialization/examples-of-xml-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="42e9c-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="42e9c-107">序列化物件</span><span class="sxs-lookup"><span data-stu-id="42e9c-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="42e9c-108">建立物件並設定其公用欄位與屬性。</span><span class="sxs-lookup"><span data-stu-id="42e9c-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="42e9c-109">使用物件的型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="42e9c-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="42e9c-110">如需詳細資訊，請參閱 <xref:System.Xml.Serialization.XmlSerializer> 類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="42e9c-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="42e9c-111">呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 方法，產生 XML 資料流或物件之公用屬性與欄位的檔案表示方式。</span><span class="sxs-lookup"><span data-stu-id="42e9c-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="42e9c-112">下列範例將建立檔案。</span><span class="sxs-lookup"><span data-stu-id="42e9c-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="42e9c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42e9c-113">See also</span></span>

- [<span data-ttu-id="42e9c-114">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="42e9c-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="42e9c-115">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="42e9c-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
