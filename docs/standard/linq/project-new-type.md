---
title: 如何投影新類型-LINQ to XML
description: 您的查詢可能會傳回非通用型別的 IEnumerable。 本文說明如何使用範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: a0ce8d9e5199b290dc759c191c4db7a37ddc9a55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547533"
---
# <a name="how-to-project-a-new-type-linq-to-xml"></a><span data-ttu-id="7ef7a-104">如何投影新類型 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7ef7a-104">How to project a new type (LINQ to XML)</span></span>

<span data-ttu-id="7ef7a-105">本節中的其他範例顯示的查詢會傳回結果，當做 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> 的 `string`，以及 <xref:System.Collections.Generic.IEnumerable%601> 的 `int`。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-105">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="7ef7a-106">這些是常見的結果類型，但並非每個案例都適用。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-106">These are common result types, but they're not appropriate for every scenario.</span></span> <span data-ttu-id="7ef7a-107">在許多情況下，您會想要讓查詢傳回 <xref:System.Collections.Generic.IEnumerable%601> 其他類型的。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-107">In many cases, you'll want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a><span data-ttu-id="7ef7a-108">範例：定義新的型別，並讓 `select` 語句建立型別的實例</span><span class="sxs-lookup"><span data-stu-id="7ef7a-108">Example: Define a new type and have the `select` statement create an instance of the type</span></span>

<span data-ttu-id="7ef7a-109">此範例顯示如何具現化 `select` 子句中的物件。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-109">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="7ef7a-110">程式碼會先叫用一個函式來定義新的類別，然後修改 `select` 語句，讓運算式成為新類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-110">The code first invokes a constructor to define a new class, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span> <span data-ttu-id="7ef7a-111">此範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-111">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

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

```vb
Public Class NameQty
    Public name As String
    Public qty As Integer
    Public Sub New(ByVal n As String, ByVal q As Integer)
        name = n
        qty = q
    End Sub
End Class

Public Class Program
    Shared Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")

        Dim nqList As IEnumerable(Of NameQty) = _
            From n In po...<Item> _
            Select New NameQty( _
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))

        For Each n As NameQty In nqList
            Console.WriteLine(n.name & ":" & n.qty)
        Next
    End Sub
End Class
```

<span data-ttu-id="7ef7a-112">這個範例會使用「 <xref:System.Xml.Linq.XContainer.Element%2A> [如何取出單一子項目」一](retrieve-single-child-element.md) 文中引進的方法。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-112">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the [How to retrieve a single child element](retrieve-single-child-element.md) article.</span></span> <span data-ttu-id="7ef7a-113">它也會使用轉換以擷取 <xref:System.Xml.Linq.XContainer.Element%2A> 方法所傳回的元素值。</span><span class="sxs-lookup"><span data-stu-id="7ef7a-113">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

<span data-ttu-id="7ef7a-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7ef7a-114">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a><span data-ttu-id="7ef7a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef7a-115">See also</span></span>

- [<span data-ttu-id="7ef7a-116">投影和轉換 (LINQ to XML)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="7ef7a-116">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](./work-dictionaries-linq-xml.md)
