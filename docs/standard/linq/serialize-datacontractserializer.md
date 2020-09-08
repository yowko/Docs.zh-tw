---
title: 如何使用 DataContractSerializer 序列化-LINQ to XML
description: 瞭解如何使用 DataContractSerializer 序列化和還原序列化。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 6fcc8f725855386fe987589fe4dde74b06ed60a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552213"
---
# <a name="how-to-serialize-using-datacontractserializer-linq-to-xml"></a><span data-ttu-id="63a05-103">如何使用 DataContractSerializer (LINQ to XML) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="63a05-103">How to serialize using DataContractSerializer (LINQ to XML)</span></span>

<span data-ttu-id="63a05-104">本文顯示使用 <xref:System.Runtime.Serialization.DataContractSerializer> c # 和 Visual Basic 序列化和還原序列化的範例。</span><span class="sxs-lookup"><span data-stu-id="63a05-104">This article shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer> in C# and Visual Basic.</span></span>

## <a name="example-create-objects-that-contain-xelement-objects-then-serialize-and-deserialize-them"></a><span data-ttu-id="63a05-105">範例：建立包含物件的物件 `XElement` ，然後將它們序列化和還原序列化</span><span class="sxs-lookup"><span data-stu-id="63a05-105">Example: Create objects that contain `XElement` objects, then serialize and deserialize them</span></span>

<span data-ttu-id="63a05-106">下列範例會建立多個包含 <xref:System.Xml.Linq.XElement> 物件的物件。</span><span class="sxs-lookup"><span data-stu-id="63a05-106">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="63a05-107">接著，它會將這些物件序列化為文字檔，然後從文字檔還原序列化。</span><span class="sxs-lookup"><span data-stu-id="63a05-107">It then serializes them to text files, and then deserializes them from the text files.</span></span>

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

```vb
Imports System
Imports System.Xml
Imports System.Xml.Linq
Imports System.IO
Imports System.Runtime.Serialization

Public Class XLinqTest
    Shared Sub Main()
        Test(Of XElement)(CreateXElement())
        Test(Of XElementContainer)(New XElementContainer())
        Test(Of XElementNullContainer)(New XElementNullContainer())
    End Sub

    Public Shared Sub Test(Of T)(ByRef obj)
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)
            Console.WriteLine("Testing for type: {0}", GetType(T))
            s.WriteObject(fs, obj)
        End Using

        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)
            Dim s2 As Object = s.ReadObject(fs)
            If s2 Is Nothing Then
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")
            Else
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())
            End If
        End Using
    End Sub

    Public Shared Function CreateXElement() As XElement
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))
    End Function
End Class

<DataContract()> _
Public Class XElementContainer
    <DataMember()> _
    Public member As XElement

    Public Sub XElementContainer()
        member = XLinqTest.CreateXElement()
    End Sub
End Class

<DataContract()> _
Public Class XElementNullContainer
    <DataMember()> _
    Public member As XElement

    Public Sub XElementNullContainer()
        member = Nothing
    End Sub
End Class
```

 <span data-ttu-id="63a05-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="63a05-108">This example produces the following output:</span></span>

```output
Testing for type: System.Xml.Linq.XElement
  Deserialized type: System.Xml.Linq.XElement
Testing for type: XElementContainer
  Deserialized type: XElementContainer
Testing for type: XElementNullContainer
  Deserialized type: XElementNullContainer
```
