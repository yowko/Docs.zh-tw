---
title: 函數式建構 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c2579da6e3cdfea6469742d29935b0137e320bbb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44191010"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="d5be2-102">函數式建構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5be2-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d5be2-103"> 提供一種強大的方式來建立 XML 元素，稱為「函數式建構」。</span><span class="sxs-lookup"><span data-stu-id="d5be2-103"> provides a powerful way to create XML elements called \*functional construction\*.</span></span> <span data-ttu-id="d5be2-104">功能結構是在單一陳述式中建立 XML 樹狀結構的能力。</span><span class="sxs-lookup"><span data-stu-id="d5be2-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="d5be2-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 程式介面有數種主要功能可以使用功能結構：</span><span class="sxs-lookup"><span data-stu-id="d5be2-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="d5be2-106"><xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。</span><span class="sxs-lookup"><span data-stu-id="d5be2-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="d5be2-107">例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="d5be2-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="d5be2-108">您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。</span><span class="sxs-lookup"><span data-stu-id="d5be2-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="d5be2-109">或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="d5be2-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="d5be2-110"><xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。</span><span class="sxs-lookup"><span data-stu-id="d5be2-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="d5be2-111">這可讓您建立包含複雜內容的項目。</span><span class="sxs-lookup"><span data-stu-id="d5be2-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="d5be2-112">如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d5be2-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d5be2-113">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="d5be2-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d5be2-114">這是非常重要的，因為這可讓您將 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果傳遞到建構函式中。</span><span class="sxs-lookup"><span data-stu-id="d5be2-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="d5be2-115">這些功能可讓您撰寫程式碼來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d5be2-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="d5be2-116">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="d5be2-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="d5be2-117">建立 XML 樹狀結構時，這些功能也可讓您撰寫使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢結果的程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5be2-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d5be2-118">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d5be2-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5be2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5be2-119">See Also</span></span>

- [<span data-ttu-id="d5be2-120">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="d5be2-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
