---
title: "如何︰ 擷取屬性 (LINQ to XML) 的集合 (Visual Basic) |Microsoft 文件"
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
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 696cb1c41d38cfc7f3d739265bf79af62ff456fe
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="ac515-102">如何︰ 擷取屬性 (LINQ to XML) 的集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac515-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ac515-103">本主題將介紹<xref:System.Xml.Linq.XElement.Attributes%2A>方法。</xref:System.Xml.Linq.XElement.Attributes%2A></span><span class="sxs-lookup"><span data-stu-id="ac515-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="ac515-104">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ac515-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac515-105">範例</span><span class="sxs-lookup"><span data-stu-id="ac515-105">Example</span></span>  
 <span data-ttu-id="ac515-106">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="ac515-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="ac515-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ac515-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac515-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac515-108">See Also</span></span>  
 [<span data-ttu-id="ac515-109">LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac515-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
