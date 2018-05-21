---
title: 序列化包含 XElement 物件的物件圖形 (C#)
ms.date: 07/20/2015
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
ms.openlocfilehash: f51a026642563e1c1690d9a49220aae462840211
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="5b129-102">序列化包含 XElement 物件的物件圖形 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b129-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="5b129-103">本主題說明如何序列化包含型別 <xref:System.Xml.Linq.XElement> 之物件參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="5b129-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="5b129-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="5b129-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="5b129-105">請注意，只有 <xref:System.Xml.Linq.XElement> 類別 (Class) 會實作序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="5b129-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b129-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5b129-106">In This Section</span></span>  
  
|<span data-ttu-id="5b129-107">主題</span><span class="sxs-lookup"><span data-stu-id="5b129-107">Topic</span></span>|<span data-ttu-id="5b129-108">描述</span><span class="sxs-lookup"><span data-stu-id="5b129-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5b129-109">如何：使用 XmlSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b129-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="5b129-110">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="5b129-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="5b129-111">如何：使用 DataContractSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b129-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="5b129-112">示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="5b129-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b129-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b129-113">See Also</span></span>  
 [<span data-ttu-id="5b129-114">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b129-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
