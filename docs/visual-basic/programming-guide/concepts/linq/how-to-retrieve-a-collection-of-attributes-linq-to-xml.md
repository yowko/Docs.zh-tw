---
title: HOW TO：擷取集合的屬性 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: 691ec9edda6051ba1f598891dfb9331b85ceb278
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716607"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="38f72-102">HOW TO：擷取集合的屬性 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38f72-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="38f72-103">本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="38f72-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="38f72-104">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="38f72-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38f72-105">範例</span><span class="sxs-lookup"><span data-stu-id="38f72-105">Example</span></span>  
 <span data-ttu-id="38f72-106">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="38f72-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="38f72-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="38f72-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="38f72-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38f72-108">See also</span></span>
- [<span data-ttu-id="38f72-109">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38f72-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
