---
title: "如何：投影物件圖形 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 293d15d5-3eaf-48de-9a02-3e13cb117b5b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: abf16b36fa8b384c2685a29a1697cc7c3e53a7ec
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-project-an-object-graph-c"></a>如何：投影物件圖形 (C#)
本主題說明如何從 XML 規劃或填入物件圖形。  
  
## <a name="example"></a>範例  
 下列程式碼會填入具有 `Address`、`PurchaseOrder` 及來自[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML 文件之 `PurchaseOrderItem` 類別的物件圖形。  
  
```csharp  
class Address  
{  
    public enum AddressUse  
    {  
        Shipping,  
        Billing,  
    }  
  
    private AddressUse addressType;  
    private string name;  
    private string street;  
    private string city;  
    private string state;  
    private string zip;  
    private string country;  
  
    public AddressUse AddressType {  
        get { return addressType; } set { addressType = value; }  
    }  
  
    public string Name {  
        get { return name; } set { name = value; }  
    }  
  
    public string Street {  
        get { return street; } set { street = value; }  
    }  
  
    public string City {  
        get { return city; } set { city = value; }  
    }  
  
    public string State {  
        get { return state; } set { state = value; }  
    }  
  
    public string Zip {  
        get { return zip; } set { zip = value; }  
    }  
  
    public string Country {  
        get { return country; } set { country = value; }  
    }  
  
    public override string ToString()  
    {  
        StringBuilder sb = new StringBuilder();  
        sb.Append(String.Format("Type: {0}\n",  
          addressType == AddressUse.Shipping ? "Shipping" : "Billing"));  
        sb.Append(String.Format("Name: {0}\n", name));  
        sb.Append(String.Format("Street: {0}\n", street));  
        sb.Append(String.Format("City: {0}\n", city));  
        sb.Append(String.Format("State: {0}\n", state));  
        sb.Append(String.Format("Zip: {0}\n", zip));  
        sb.Append(String.Format("Country: {0}\n", country));  
        return sb.ToString();  
    }  
}  
  
class PurchaseOrderItem  
{  
    private string partNumber;  
    private string productName;  
    private int quantity;  
    private Decimal usPrice;  
    private string comment;  
    private DateTime shipDate;  
  
    public string PartNumber {  
        get { return partNumber; } set { partNumber = value; }  
    }  
  
    public string ProductName {  
        get { return productName; } set { productName = value; }  
    }  
  
    public int Quantity {  
        get { return quantity; } set { quantity = value; }  
    }  
  
    public Decimal USPrice {  
        get { return usPrice; } set { usPrice = value; }  
    }  
  
    public string Comment {  
        get { return comment; } set { comment = value; }  
    }  
  
    public DateTime ShipDate {  
        get { return shipDate; } set { shipDate = value; }  
    }  
  
    public override string ToString()  
    {  
        StringBuilder sb = new StringBuilder();  
        sb.Append(String.Format("PartNumber: {0}\n", partNumber));  
        sb.Append(String.Format("ProductName: {0}\n", productName));  
        sb.Append(String.Format("Quantity: {0}\n", quantity));  
        sb.Append(String.Format("USPrice: {0}\n", usPrice));  
        if (comment != null)  
            sb.Append(String.Format("Comment: {0}\n", comment));  
        if (shipDate != DateTime.MinValue)  
            sb.Append(String.Format("ShipDate: {0:d}\n", shipDate));  
        return sb.ToString();  
    }  
}  
  
class PurchaseOrder  
{  
    private string purchaseOrderNumber;  
    private DateTime orderDate;  
    private string comment;  
    private List<Address> addresses;  
    private List<PurchaseOrderItem> items;  
  
    public string PurchaseOrderNumber {  
        get { return purchaseOrderNumber; } set { purchaseOrderNumber = value; }  
    }  
  
    public DateTime OrderDate {  
        get { return orderDate; } set { orderDate = value; }  
    }  
  
    public string Comment {  
        get { return comment; } set { comment = value; }  
    }  
  
    public List<Address> Addresses {  
        get { return addresses; } set { addresses = value; }  
    }  
  
    public List<PurchaseOrderItem> Items {  
        get { return items; } set { items = value; }  
    }  
  
    public override string ToString()  
    {  
        StringBuilder sb = new StringBuilder();  
        sb.Append(String.Format("PurchaseOrderNumber: {0}\n", purchaseOrderNumber));  
        sb.Append(String.Format("OrderDate: {0:d}\n", orderDate));  
        sb.Append("\n");  
        sb.Append("Addresses\n");  
        sb.Append("=====\n");  
        foreach (Address address in addresses)  
        {  
            sb.Append(address);  
            sb.Append("\n");  
        }  
        sb.Append("Items\n");  
        sb.Append("=====\n");  
        foreach (PurchaseOrderItem item in items)  
        {  
            sb.Append(item);  
            sb.Append("\n");  
        }  
        return sb.ToString();  
    }  
}  
  
class Program {  
    public static void Main()  
    {  
        XElement po = XElement.Load("PurchaseOrder.xml");  
        PurchaseOrder purchaseOrder = new PurchaseOrder {  
            PurchaseOrderNumber = (string)po.Attribute("PurchaseOrderNumber"),  
            OrderDate = (DateTime)po.Attribute("OrderDate"),  
            Addresses = (  
                            from a in po.Elements("Address")  
                            select new Address {  
                                AddressType = ((string)a.Attribute("Type") == "Shipping") ?  
                                    Address.AddressUse.Shipping :   
                                    Address.AddressUse.Billing,  
                                Name = (string)a.Element("Name"),  
                                Street = (string)a.Element("Street"),  
                                City = (string)a.Element("City"),  
                                State = (string)a.Element("State"),  
                                Zip = (string)a.Element("Zip"),  
                                Country = (string)a.Element("Country")  
                            }  
                        ).ToList(),  
            Items = (  
                        from i in po.Element("Items").Elements("Item")  
                        select new PurchaseOrderItem {  
                            PartNumber = (string)i.Attribute("PartNumber"),  
                            ProductName = (string)i.Element("ProductName"),  
                            Quantity = (int)i.Element("Quantity"),  
                            USPrice = (Decimal)i.Element("USPrice"),  
                            Comment = (string)i.Element("Comment"),  
                            ShipDate = (i.Element("ShipDate") != null) ?  
                                (DateTime)i.Element("ShipDate") :  
                                DateTime.MinValue  
                        }  
                    ).ToList()  
        };  
        Console.WriteLine(purchaseOrder);  
    }  
}  
```  
  
 在此範例中，[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢的結果會以 `PurchaseOrderItem` 的 <xref:System.Collections.Generic.IEnumerable%601> 形式傳回。 `PurchaseOrder` 類別中的項目屬於 `PurchaseOrderItem` 的 <xref:System.Collections.Generic.IEnumerable%601> 類型。 此程式碼使用 <xref:System.Linq.Enumerable.ToList%2A> 擴充方法，從查詢結果建立 <xref:System.Collections.Generic.List%601> 集合。  
  
 這個範例會產生下列輸出：  
  
```  
PurchaseOrderNumber: 99503  
OrderDate: 10/20/1999  
  
Addresses  
=====  
Type: Shipping  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 10999  
Country: USA  
  
Type: Billing  
Name: Tai Yee  
Street: 8 Oak Avenue  
City: Old Town  
State: PA  
Zip: 95819  
Country: USA  
  
Items  
=====  
PartNumber: 872-AA  
ProductName: Lawnmower  
Quantity: 1  
USPrice: 148.95  
Comment: Confirm this is electric  
  
PartNumber: 926-AA  
ProductName: Baby Monitor  
Quantity: 2  
USPrice: 39.98  
ShipDate: 5/21/1999  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.Enumerable.Select%2A>   
 <xref:System.Linq.Enumerable.ToList%2A>   
 [投影和轉換 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
