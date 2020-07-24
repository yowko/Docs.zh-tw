---
title: 函數式建構 (LINQ to XML) (C#)
description: '瞭解 LINQ to XML 程式設計介面如何啟用功能結構，也就是在 c # 的單一語句中建立 XML 樹狀結構的功能。'
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103778"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="c8269-103">函數式建構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8269-103">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c8269-104">提供一種強大的方式來建立 XML 元素，稱為「函數式建構」\*\*。</span><span class="sxs-lookup"><span data-stu-id="c8269-104">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="c8269-105">功能結構是在單一陳述式中建立 XML 樹狀結構的能力。</span><span class="sxs-lookup"><span data-stu-id="c8269-105">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="c8269-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 程式介面有數種主要功能可以使用功能結構：</span><span class="sxs-lookup"><span data-stu-id="c8269-106">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="c8269-107"><xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。</span><span class="sxs-lookup"><span data-stu-id="c8269-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="c8269-108">例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="c8269-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="c8269-109">您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="c8269-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="c8269-110">或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="c8269-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="c8269-111"><xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。</span><span class="sxs-lookup"><span data-stu-id="c8269-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="c8269-112">這可讓您建立包含複雜內容的項目。</span><span class="sxs-lookup"><span data-stu-id="c8269-112">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="c8269-113">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="c8269-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="c8269-114">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="c8269-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="c8269-115">這很重要，因為它可讓您將 LINQ 查詢的結果傳遞給此函式。</span><span class="sxs-lookup"><span data-stu-id="c8269-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="c8269-116">這些功能可讓您撰寫程式碼來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="c8269-116">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="c8269-117">下列為範例：</span><span class="sxs-lookup"><span data-stu-id="c8269-117">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="c8269-118">當您建立 XML 樹狀結構時，這些功能也可以讓您撰寫使用 LINQ 查詢結果的程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c8269-118">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="c8269-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="c8269-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  