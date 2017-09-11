---
title: "如何︰ 使用 XmlSerializer (Visual Basic) 序列化 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: cace24eb-0f43-4016-8e4b-199e5ef73a1c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 9cb53837ea2d272efa6bbb9b9f64231c84c42274
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-serialize-using-xmlserializer-visual-basic"></a><span data-ttu-id="b2fde-102">如何︰ 使用 xmlserializer (Visual Basic) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="b2fde-102">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>
<span data-ttu-id="b2fde-103">本主題顯示的範例會序列化和還原序列化使用<xref:System.Xml.Serialization.XmlSerializer>。</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="b2fde-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2fde-104">範例</span><span class="sxs-lookup"><span data-stu-id="b2fde-104">Example</span></span>  
 <span data-ttu-id="b2fde-105">下列範例會建立包含的物件數目<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b2fde-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b2fde-106">接著，它會將這些物件序列化為記憶體資料流，然後從記憶體資料流還原序列化。</span><span class="sxs-lookup"><span data-stu-id="b2fde-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
Imports System.Xml.Serialization  
  
Public Class XElementContainer  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
  
    Overrides Function ToString() As String  
        Return member.ToString()  
    End Function  
End Class  
  
Public Class XElementNullContainer  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Dim ns As XNamespace = "http://www.adventure-works.com"  
        Return New XElement(ns + "aw")  
    End Function  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Using stream As New MemoryStream()  
            Dim s As XmlSerializer = New XmlSerializer(GetType(T))  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.Serialize(XmlWriter.Create(stream), obj)  
            stream.Flush()  
            stream.Seek(0, SeekOrigin.Begin)  
            Dim o As Object = s.Deserialize(XmlReader.Create(stream))  
            Console.WriteLine("  Deserialized type: {0}", o.GetType())  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="b2fde-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b2fde-107">This example produces the following output:</span></span>  
  
```  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2fde-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2fde-108">See Also</span></span>  
 [<span data-ttu-id="b2fde-109">序列化包含 XElement 物件 (Visual Basic) 的物件圖形</span><span class="sxs-lookup"><span data-stu-id="b2fde-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)

