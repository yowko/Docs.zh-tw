---
title: 序列化包含 XElement 物件的物件圖形
ms.date: 07/20/2015
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
ms.openlocfilehash: 5390cfaa77229b60af6388fc643544c539c15fe9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360679"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="e8cf3-102">序列化包含 System.xml.linq.xelement> 物件的物件圖形（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8cf3-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="e8cf3-103">本主題說明如何序列化包含型別 <xref:System.Xml.Linq.XElement> 之物件參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="e8cf3-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e8cf3-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="e8cf3-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="e8cf3-105">請注意，只有 <xref:System.Xml.Linq.XElement> 類別 (Class) 會實作序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="e8cf3-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8cf3-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e8cf3-106">In This Section</span></span>  
  
|<span data-ttu-id="e8cf3-107">主題</span><span class="sxs-lookup"><span data-stu-id="e8cf3-107">Topic</span></span>|<span data-ttu-id="e8cf3-108">說明</span><span class="sxs-lookup"><span data-stu-id="e8cf3-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e8cf3-109">如何：使用 XmlSerializer 進行序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8cf3-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="e8cf3-110">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="e8cf3-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="e8cf3-111">如何：使用 DataContractSerializer 進行序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8cf3-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="e8cf3-112">示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="e8cf3-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8cf3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8cf3-113">See also</span></span>

- [<span data-ttu-id="e8cf3-114">Advanced LINQ to XML 程式設計（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8cf3-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
