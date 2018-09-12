---
title: HOW TO：序列化物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: e4d6e3edb15dbf5ba4b7ec7f8658fec1a618d315
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700540"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="103fd-102">HOW TO：序列化物件</span><span class="sxs-lookup"><span data-stu-id="103fd-102">How to: Serialize an Object</span></span>
<span data-ttu-id="103fd-103">若要序列化物件，首先建立要序列化的物件，並設定其公用屬性與欄位。</span><span class="sxs-lookup"><span data-stu-id="103fd-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="103fd-104">若要執行這項作業，您必須判斷 XML 資料流儲存 (無論是資料流或檔案) 的傳輸格式。</span><span class="sxs-lookup"><span data-stu-id="103fd-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="103fd-105">例如，若 XML 資料流必須以永久形式儲存，請建立 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="103fd-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="103fd-106">如需 XML 序列化的其他範例，請參閱 [XML 序列化的範例](../../../docs/standard/serialization/examples-of-xml-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="103fd-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="103fd-107">序列化物件</span><span class="sxs-lookup"><span data-stu-id="103fd-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="103fd-108">建立物件並設定其公用欄位與屬性。</span><span class="sxs-lookup"><span data-stu-id="103fd-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="103fd-109">使用物件的型別，建構 <xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="103fd-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="103fd-110">如需詳細資訊，請參閱 <xref:System.Xml.Serialization.XmlSerializer> 類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="103fd-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="103fd-111">呼叫 <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 方法，產生 XML 資料流或物件之公用屬性與欄位的檔案表示方式。</span><span class="sxs-lookup"><span data-stu-id="103fd-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="103fd-112">下列範例將建立檔案。</span><span class="sxs-lookup"><span data-stu-id="103fd-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="103fd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="103fd-113">See also</span></span>

- [<span data-ttu-id="103fd-114">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="103fd-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
- [<span data-ttu-id="103fd-115">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="103fd-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
