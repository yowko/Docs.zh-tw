---
title: "將物件圖形序列化包含 XElement 物件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44a30e3c79eb1f68f968e83c50a55f24da9275cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="13c89-102">將物件圖形序列化包含 XElement 物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13c89-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="13c89-103">本主題說明如何序列化包含型別 <xref:System.Xml.Linq.XElement> 之物件參考的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="13c89-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="13c89-104">為了簡化這種類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="13c89-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="13c89-105">請注意，只有 <xref:System.Xml.Linq.XElement> 類別 (Class) 會實作序列化 (Serialization)。</span><span class="sxs-lookup"><span data-stu-id="13c89-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13c89-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="13c89-106">In This Section</span></span>  
  
|<span data-ttu-id="13c89-107">主題</span><span class="sxs-lookup"><span data-stu-id="13c89-107">Topic</span></span>|<span data-ttu-id="13c89-108">說明</span><span class="sxs-lookup"><span data-stu-id="13c89-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="13c89-109">如何： 序列化使用 XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13c89-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="13c89-110">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="13c89-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="13c89-111">如何： 序列化使用 DataContractSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13c89-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="13c89-112">示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化。</span><span class="sxs-lookup"><span data-stu-id="13c89-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13c89-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13c89-113">See Also</span></span>  
 [<span data-ttu-id="13c89-114">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13c89-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
