---
title: 如何：鏈結軸方法呼叫 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 36160a9dd4cc26b0b1d54e6e8b91d2880dd23abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333772"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>如何：鏈結軸方法呼叫 (LINQ to XML) (C#)
您在程式碼中使用的常見模式為呼叫座標軸方法，然後呼叫其中一個擴充方法座標軸。  
  
 有兩個座標軸可傳回項目集合而且具有 `Elements` 名稱：<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法。 您可以結合這兩個座標軸，在樹狀的指定深度，尋找指定之名稱的所有項目。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>，在所有 `Name` 項目的所有 `Address` 項目中，尋找所有 `PurchaseOrder` 項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 之所以可以這樣做，是因為 `Elements` 軸的其中一個實作是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XContainer>。 <xref:System.Xml.Linq.XElement> 衍生自 <xref:System.Xml.Linq.XContainer>，所以可以呼叫在呼叫結果上的 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法至 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法。  
  
## <a name="example"></a>範例  
 有時候您會想要在可能有也可能沒有介入祖系時，擷取特定項目深度的所有項目。 例如，在下列文件中，您可能想要擷取 `ConfigParameter` 項目子系的所有 `Customer` 項目，但不是 `ConfigParameter` 項目子系的 `Root`。  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 如果要這樣做，您可以使用 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 座標軸，如下所示：  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同技術。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的多份採購單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>請參閱  
 [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
