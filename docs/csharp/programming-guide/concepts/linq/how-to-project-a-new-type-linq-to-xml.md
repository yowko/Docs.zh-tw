---
title: 如何：投影新類型 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: f9a46e78a0f80f33764e9f87e3e8ce3560a8e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323767"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="78161-102">如何：投影新類型 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="78161-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>
<span data-ttu-id="78161-103">本節中的其他範例顯示的查詢會傳回結果，當做 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> 的 `string`，以及 <xref:System.Collections.Generic.IEnumerable%601> 的 `int`。</span><span class="sxs-lookup"><span data-stu-id="78161-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="78161-104">這些是常見的結果型別，但這些型別不適用於每個案例。</span><span class="sxs-lookup"><span data-stu-id="78161-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="78161-105">在許多情況下，您會希望您的查詢傳回其他型別的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="78161-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78161-106">範例</span><span class="sxs-lookup"><span data-stu-id="78161-106">Example</span></span>  
 <span data-ttu-id="78161-107">此範例顯示如何具現化 `select` 子句中的物件。</span><span class="sxs-lookup"><span data-stu-id="78161-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="78161-108">此程式碼會先利用建構函式定義新的類別，然後修改 `select` 陳述式，讓運算式成為新類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="78161-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="78161-109">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="78161-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
  
        IEnumerable<NameQty> nqList =  
            from n in po.Descendants("Item")  
            select new NameQty(  
                    (string)n.Element("ProductName"),  
                    (int)n.Element("Quantity")  
                );  
  
        foreach (NameQty n in nqList)  
            Console.WriteLine(n.name + ":" + n.qty);  
    }  
}  
```  
  
 <span data-ttu-id="78161-110">此範例使用[如何：擷取單一子項目 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md) 主題中所引進的 `M:System.Xml.Linq.XElement.Element` 方法。</span><span class="sxs-lookup"><span data-stu-id="78161-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="78161-111">它也會使用轉換以擷取 `M:System.Xml.Linq.XElement.Element` 方法所傳回的元素值。</span><span class="sxs-lookup"><span data-stu-id="78161-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="78161-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="78161-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="78161-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="78161-113">See Also</span></span>  
 [<span data-ttu-id="78161-114">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="78161-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
