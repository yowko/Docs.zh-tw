---
title: 如何：擷取單一屬性 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 55da36099af72259a4e72205f142ab855f000c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="8caf6-102">如何：擷取單一屬性 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8caf6-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8caf6-103">這個主題會說明如何擷取項目的單一屬性 (如果有屬性名稱)。</span><span class="sxs-lookup"><span data-stu-id="8caf6-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="8caf6-104">這在撰寫您要尋找具有特定屬性之項目的查詢運算式時，相當實用。</span><span class="sxs-lookup"><span data-stu-id="8caf6-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="8caf6-105"><xref:System.Xml.Linq.XElement.Attribute%2A> 類別的 <xref:System.Xml.Linq.XElement> 方法會傳回具有指定之名稱的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="8caf6-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8caf6-106">範例</span><span class="sxs-lookup"><span data-stu-id="8caf6-106">Example</span></span>  
 <span data-ttu-id="8caf6-107">下列範例使用 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8caf6-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="8caf6-108">此範例將尋找名為 `Phone` 樹狀結構中所有的子代，然後尋找名為 `type` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="8caf6-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="8caf6-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8caf6-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="8caf6-110">範例</span><span class="sxs-lookup"><span data-stu-id="8caf6-110">Example</span></span>  
 <span data-ttu-id="8caf6-111">如果您要擷取屬性的值，您可以進行轉型，如同將 <xref:System.Xml.Linq.XElement> 物件轉型。</span><span class="sxs-lookup"><span data-stu-id="8caf6-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8caf6-112">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="8caf6-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="8caf6-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8caf6-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8caf6-114"> 提供了 <xref:System.Xml.Linq.XAttribute> 類別至 `string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 及 `GUID?` 的明確轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="8caf6-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8caf6-115">範例</span><span class="sxs-lookup"><span data-stu-id="8caf6-115">Example</span></span>  
 <span data-ttu-id="8caf6-116">下列範例顯示命名空間中之屬性的相同程式碼。</span><span class="sxs-lookup"><span data-stu-id="8caf6-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="8caf6-117">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="8caf6-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="8caf6-118">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8caf6-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="8caf6-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="8caf6-119">See Also</span></span>  
 [<span data-ttu-id="8caf6-120">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="8caf6-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
