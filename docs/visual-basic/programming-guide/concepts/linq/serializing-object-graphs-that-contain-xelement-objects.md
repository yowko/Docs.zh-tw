---
title: 序列化包含 XElement 物件的物件圖形
ms.date: 07/20/2015
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
ms.openlocfilehash: caf594fc23eee15cc79cfad47e62a057518f62dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349363"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="6adbc-102">序列化包含 System.xml.linq.xelement> 物件的物件圖形（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6adbc-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="6adbc-103">本主題說明如何序列化包含型別 <xref:System.Xml.Linq.XElement> 之物件參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="6adbc-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6adbc-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="6adbc-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="6adbc-105">請注意，只有 <xref:System.Xml.Linq.XElement> 類別 (Class) 會實作序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="6adbc-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6adbc-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="6adbc-106">In This Section</span></span>  
  
|<span data-ttu-id="6adbc-107">主題</span><span class="sxs-lookup"><span data-stu-id="6adbc-107">Topic</span></span>|<span data-ttu-id="6adbc-108">描述</span><span class="sxs-lookup"><span data-stu-id="6adbc-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6adbc-109">如何：使用 XmlSerializer 進行序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6adbc-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="6adbc-110">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="6adbc-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="6adbc-111">如何：使用 DataContractSerializer 進行序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6adbc-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="6adbc-112">示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="6adbc-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6adbc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6adbc-113">See also</span></span>

- [<span data-ttu-id="6adbc-114">Advanced LINQ to XML 程式設計（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6adbc-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
