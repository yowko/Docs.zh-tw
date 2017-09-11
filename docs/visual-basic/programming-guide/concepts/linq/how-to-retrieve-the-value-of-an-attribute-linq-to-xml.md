---
title: "如何︰ 擷取屬性 (LINQ to XML) 的值 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 6ecc1368832b9c98efeae65c95438efb80f164f6
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="22b19-102">如何︰ 擷取屬性 (LINQ to XML) 的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22b19-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="22b19-103">這個主題顯示如何取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="22b19-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="22b19-104">有兩種主要方式︰ 您可以轉型<xref:System.Xml.Linq.XAttribute>所需的型別; 明確的轉換運算子再將內容轉換的項目或屬性，以指定的型別。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="22b19-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="22b19-105">或者，您可以使用<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="22b19-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="22b19-106">不過，轉型通常是較好的方法。</span><span class="sxs-lookup"><span data-stu-id="22b19-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="22b19-107">如果您要將屬性轉型為可為 Null 的型別 (Nullable Type)，擷取可能存在或可能不存在之屬性的值時，程式碼比較容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="22b19-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="22b19-108">如需這項技術的範例，請參閱[How to︰ 擷取項目 (LINQ to XML) 的值 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="22b19-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22b19-109">範例</span><span class="sxs-lookup"><span data-stu-id="22b19-109">Example</span></span>  
 <span data-ttu-id="22b19-110">在 Visual Basic 中，您可以使用整合式屬性 (Attribute) 的屬性 (Property) 來擷取屬性 (Attribute) 的值。</span><span class="sxs-lookup"><span data-stu-id="22b19-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="22b19-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="22b19-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="22b19-112">範例</span><span class="sxs-lookup"><span data-stu-id="22b19-112">Example</span></span>  
 <span data-ttu-id="22b19-113">在 Visual Basic 中，您可以使用整合式屬性 (Attribute) 的屬性 (Property) 來設定屬性 (Attribute) 的值。</span><span class="sxs-lookup"><span data-stu-id="22b19-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="22b19-114">此外，如果您使用整合式屬性 (Attribute) 的屬性 (Property) 來設定不存在之屬性 (Attribute) 的值，將會建立這個屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="22b19-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="22b19-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="22b19-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="22b19-116">範例</span><span class="sxs-lookup"><span data-stu-id="22b19-116">Example</span></span>  
 <span data-ttu-id="22b19-117">下列範例顯示如何擷取屬性位於命名空間之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="22b19-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="22b19-118">如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="22b19-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="22b19-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="22b19-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="22b19-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22b19-120">See Also</span></span>  
 [<span data-ttu-id="22b19-121">LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22b19-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
