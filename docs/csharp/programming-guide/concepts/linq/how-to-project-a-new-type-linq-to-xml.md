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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>如何投影新類型（LINQ to XML）（c #）

本節中的其他範例顯示的查詢會傳回結果，當做 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> 的 `string`，以及 <xref:System.Collections.Generic.IEnumerable%601> 的 `int`。 這些是常見的結果型別，但這些型別不適用於每個案例。 在許多情況下，您會希望您的查詢傳回其他型別的 <xref:System.Collections.Generic.IEnumerable%601>。

## <a name="example"></a>範例

此範例顯示如何具現化 `select` 子句中的物件。 此程式碼會先利用建構函式定義新的類別，然後修改 `select` 陳述式，讓運算式成為新類別的新執行個體。

此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。

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

這個範例會使用 <xref:System.Xml.Linq.XContainer.Element%2A> [如何抓取單一子專案（LINQ to XML）（c #）](how-to-retrieve-a-single-child-element-linq-to-xml.md)主題中引進的方法。 它也會使用轉換以擷取 <xref:System.Xml.Linq.XContainer.Element%2A> 方法所傳回的元素值。  

這個範例會產生下列輸出：

```output
Lawnmower:1
Baby Monitor:2
```
