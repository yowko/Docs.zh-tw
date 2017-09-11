---
title: "序列化包含 XElement 物件 (Visual Basic) 的物件圖形 |Microsoft 文件"
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
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ce026e68aa95e6d02b46f9b985ee9ee3a268efb3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="45464-102">序列化包含 XElement 物件 (Visual Basic) 的物件圖形</span><span class="sxs-lookup"><span data-stu-id="45464-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="45464-103">本主題將介紹如何序列化包含型別<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>之物件參考的物件圖形</span><span class="sxs-lookup"><span data-stu-id="45464-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="45464-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement>實作<xref:System.Xml.Serialization.IXmlSerializable>介面。</xref:System.Xml.Serialization.IXmlSerializable> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="45464-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="45464-105">請注意，只有<xref:System.Xml.Linq.XElement>類別會實作序列化。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="45464-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45464-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="45464-106">In This Section</span></span>  
  
|<span data-ttu-id="45464-107">主題</span><span class="sxs-lookup"><span data-stu-id="45464-107">Topic</span></span>|<span data-ttu-id="45464-108">說明</span><span class="sxs-lookup"><span data-stu-id="45464-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="45464-109">如何︰ 使用 xmlserializer (Visual Basic) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="45464-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="45464-110">示範如何使用<xref:System.Xml.Serialization.XmlSerializer>.</xref:System.Xml.Serialization.XmlSerializer>序列化</span><span class="sxs-lookup"><span data-stu-id="45464-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="45464-111">如何︰ 使用 datacontractserializer (Visual Basic) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="45464-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="45464-112">示範如何使用<xref:System.Runtime.Serialization.DataContractSerializer>.</xref:System.Runtime.Serialization.DataContractSerializer>序列化</span><span class="sxs-lookup"><span data-stu-id="45464-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45464-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45464-113">See Also</span></span>  
 [<span data-ttu-id="45464-114">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45464-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
