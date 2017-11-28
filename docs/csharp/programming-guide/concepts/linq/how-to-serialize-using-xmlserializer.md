---
title: "如何：使用 XmlSerializer 進行序列化 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2e0a0bbc-c548-4fe2-8741-be5a9ccd0cbb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87a8bdff6e33644b2078c18ace3e512bfe6e177a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-serialize-using-xmlserializer-c"></a><span data-ttu-id="55bcd-102">如何：使用 XmlSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="55bcd-102">How to: Serialize Using XmlSerializer (C#)</span></span>
<span data-ttu-id="55bcd-103">本主題顯示的範例會使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="55bcd-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55bcd-104">範例</span><span class="sxs-lookup"><span data-stu-id="55bcd-104">Example</span></span>  
 <span data-ttu-id="55bcd-105">下列範例會建立多個包含 <xref:System.Xml.Linq.XElement> 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="55bcd-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="55bcd-106">接著，它會將這些物件序列化為記憶體資料流，然後從記憶體資料流還原序列化。</span><span class="sxs-lookup"><span data-stu-id="55bcd-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Linq;  
  
public class XElementContainer  
{  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
  
    public override string ToString()  
    {  
        return member.ToString();  
    }  
}  
  
public class XElementNullContainer  
{  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
    }  
}  
  
class XLinqTest  
{  
    static void Main(string[] args)  
    {  
        Test<XElementNullContainer>(new XElementNullContainer());  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
    }  
  
    public static XElement CreateXElement()  
    {  
        XNamespace ns = "http://www.adventure-works.com";  
        return new XElement(ns + "aw");  
    }  
  
    static void Test<T>(T obj)  
    {  
        using (MemoryStream stream = new MemoryStream())  
        {  
            XmlSerializer s = new XmlSerializer(typeof(T));  
            Console.WriteLine("Testing for type: {0}", typeof(T));  
            s.Serialize(XmlWriter.Create(stream), obj);  
            stream.Flush();  
            stream.Seek(0, SeekOrigin.Begin);  
            object o = s.Deserialize(XmlReader.Create(stream));  
            Console.WriteLine("  Deserialized type: {0}", o.GetType());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="55bcd-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="55bcd-107">This example produces the following output:</span></span>  
  
```  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="55bcd-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55bcd-108">See Also</span></span>  
 [<span data-ttu-id="55bcd-109">序列化包含 XElement 物件的物件圖形 (C#)</span><span class="sxs-lookup"><span data-stu-id="55bcd-109">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)
