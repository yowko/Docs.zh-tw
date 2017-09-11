---
title: "序列化包含 XElement 物件的物件圖形 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4e7b1d6365eb27596477de39577caa4144aa3501
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a><span data-ttu-id="4177f-102">序列化包含 XElement 物件的物件圖形 (C#)</span><span class="sxs-lookup"><span data-stu-id="4177f-102">Serializing Object Graphs that Contain XElement Objects (C#)</span></span>
<span data-ttu-id="4177f-103">本主題說明如何序列化包含型別 <xref:System.Xml.Linq.XElement> 之物件參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="4177f-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="4177f-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="4177f-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="4177f-105">請注意，只有 <xref:System.Xml.Linq.XElement> 類別 (Class) 會實作序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="4177f-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4177f-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="4177f-106">In This Section</span></span>  
  
|<span data-ttu-id="4177f-107">主題</span><span class="sxs-lookup"><span data-stu-id="4177f-107">Topic</span></span>|<span data-ttu-id="4177f-108">說明</span><span class="sxs-lookup"><span data-stu-id="4177f-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4177f-109">如何：使用 XmlSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="4177f-109">How to: Serialize Using XmlSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="4177f-110">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="4177f-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="4177f-111">如何：使用 DataContractSerializer 進行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="4177f-111">How to: Serialize Using DataContractSerializer (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="4177f-112">示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="4177f-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4177f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4177f-113">See Also</span></span>  
 [<span data-ttu-id="4177f-114">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="4177f-114">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

