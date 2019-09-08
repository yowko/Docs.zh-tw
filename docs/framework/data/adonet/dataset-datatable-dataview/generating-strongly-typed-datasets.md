---
title: 產生強類型資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: f1c1fd77bed700fae8e5a658da8b267120518ca9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786300"
---
# <a name="generating-strongly-typed-datasets"></a>產生強類型資料集
假設 xml 架構符合 xml 架構定義語言（XSD）標準，您可以<xref:System.Data.DataSet>使用 Windows 軟體發展工具組（SDK）所提供的 xsd.exe 工具來產生強型別。  
  
 （若要從資料庫資料表建立 xsd，請<xref:System.Data.DataSet.WriteXmlSchema%2A>參閱或使用[Visual Studio 中的資料集](/visualstudio/data-tools/dataset-tools-in-visual-studio)）。  
  
 下列程式碼顯示使用此工具產生**資料集**的語法。  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 在此語法中， `/d`指示詞會告訴工具產生**資料集**，而`/l:`會告訴工具所要使用的語言（例如， C#或 Visual Basic .net）。 選擇性`/eld`指示詞會指定您可以使用 LINQ to DataSet 來查詢所產生的**資料集。** 這個選項會在也有指定 `/d` 選項時使用。 如需詳細資訊，請參閱[查詢具類型的資料集](../querying-typed-datasets.md)。 選擇性`/n:`指示詞會告訴工具，也會產生稱為**XSDSchema**之**資料集**的命名空間。 命令的輸出為 XSDSchemaFileName.cs，可以在 ADO.NET 應用程式中編譯和使用。 產生的程式碼可以編譯為程式庫或模組。  
  
 下列程式碼顯示使用 C# 編譯器 (csc.exe)，將產生的程式碼編譯成程式庫的語法。  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` 指示詞告訴工具要編譯到程式庫，而 `/r:` 指示詞則指定編譯所需要的相依程式庫。 該命令的輸出為 XSDSchemaFileName.dll，而在使用 `/r:` 指示詞編譯 ADO.NET 應用程式時，可以將該檔案傳遞給編譯器。  
  
 下列程式碼顯示存取 ADO.NET 應用程式內傳遞給 XSD.exe 命名空間的語法。  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 下列程式碼範例會使用名為**CustomerDataSet**的具類型**資料集**，從**Northwind**資料庫載入客戶清單。 一旦使用**Fill**方法載入資料，此範例就會使用具類型的**CustomersRow** （**DataRow**）物件，在**Customers**資料表中的每個客戶上執行迴圈。 這可讓您直接存取**CustomerID**資料行，而不是透過**DataColumnCollection**。  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 下列為 XML 結構描述範例。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [具類型的 DataSet](typed-datasets.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
