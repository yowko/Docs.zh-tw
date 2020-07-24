---
title: '如何投影新類型（LINQ to XML）（c #）'
description: '瞭解如何在 c # 的 LINQ to XML 中建立查詢，以傳回 <T> system.xml.linq.xelement>、string 或 int 以外的類型 IEnumerable，如其他範例所述。'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104648"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="cabeb-103">如何投影新類型（LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="cabeb-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="cabeb-104">本節中的其他範例顯示的查詢會傳回結果，當做 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> 的 `string`，以及 <xref:System.Collections.Generic.IEnumerable%601> 的 `int`。</span><span class="sxs-lookup"><span data-stu-id="cabeb-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="cabeb-105">這些是常見的結果型別，但這些型別不適用於每個案例。</span><span class="sxs-lookup"><span data-stu-id="cabeb-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="cabeb-106">在許多情況下，您會希望您的查詢傳回其他型別的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="cabeb-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="cabeb-107">範例</span><span class="sxs-lookup"><span data-stu-id="cabeb-107">Example</span></span>

<span data-ttu-id="cabeb-108">此範例顯示如何具現化 `select` 子句中的物件。</span><span class="sxs-lookup"><span data-stu-id="cabeb-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="cabeb-109">此程式碼會先利用建構函式定義新的類別，然後修改 `select` 陳述式，讓運算式成為新類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="cabeb-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="cabeb-110">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="cabeb-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
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

<span data-ttu-id="cabeb-111">這個範例會使用 <xref:System.Xml.Linq.XContainer.Element%2A> [如何抓取單一子專案（LINQ to XML）（c #）](how-to-retrieve-a-single-child-element-linq-to-xml.md)主題中引進的方法。</span><span class="sxs-lookup"><span data-stu-id="cabeb-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="cabeb-112">它也會使用轉換以擷取 <xref:System.Xml.Linq.XContainer.Element%2A> 方法所傳回的元素值。</span><span class="sxs-lookup"><span data-stu-id="cabeb-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="cabeb-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cabeb-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
