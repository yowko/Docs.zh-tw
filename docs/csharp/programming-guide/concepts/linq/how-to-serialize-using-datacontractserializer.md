---
title: '如何使用 DataContractSerializer 序列化（c #）'
description: 瞭解如何使用 DataContractSerializer 序列化物件。 請參閱建立物件、將其序列化為文字檔，然後將它們還原序列化的範例。
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: b713f36cde594f7cd7011073345d33c6f46585e0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301524"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="1c1cf-104">如何使用 DataContractSerializer 序列化（c #）</span><span class="sxs-lookup"><span data-stu-id="1c1cf-104">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="1c1cf-105">本主題顯示的範例會使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1c1cf-105">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c1cf-106">範例</span><span class="sxs-lookup"><span data-stu-id="1c1cf-106">Example</span></span>  
 <span data-ttu-id="1c1cf-107">下列範例會建立多個包含 <xref:System.Xml.Linq.XElement> 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="1c1cf-107">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1c1cf-108">接著，它會將這些物件序列化為文字檔，然後從文字檔還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1c1cf-108">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="1c1cf-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1c1cf-109">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
