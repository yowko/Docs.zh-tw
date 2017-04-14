---
title: "產生強型別的 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 產生強型別的 DataSet
如果 XML 結構描述是採用 XML 結構描述定義語言 \(XSD\) 標準進行編譯，則可以使用 [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)] 所提供的 XSD.exe 工具產生強型別 <xref:System.Data.DataSet>。  
  
 \(若要從資料庫資料表建立 xsd，請參閱 <xref:System.Data.DataSet.WriteXmlSchema%2A> 或[使用 Visual Studio 中的資料集](http://msdn.microsoft.com/library/8bw9ksd6.aspx)\)。  
  
 下列程式碼顯示使用這個工具來產生 **DataSet** 所用的語法。  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 在這個語法中，`/d` 指示詞告訴工具產生 **DataSet**，而 `/l:` 則告訴工具應該使用哪一種語言 \(例如，C\# 或 Visual Basic .NET\)。  選擇性的 `/eld` 指示詞會指定您可以使用 [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]，查詢產生的 **DataSet**。這個選項會在也有指定 `/d` 選項時使用。  如需詳細資訊，請參閱[查詢具型別 DataSet](../../../../../docs/framework/data/adonet/querying-typed-datasets.md)。  選用的 `/n:` 指示詞會告訴工具也應該產生 **DataSet** 的命名空間，稱為 **XSDSchema.Namespace**。  命令的輸出為 XSDSchemaFileName.cs，可以在 ADO.NET 應用程式中編譯和使用。  產生的程式碼可以編譯為程式庫或模組。  
  
 下列程式碼顯示使用 C\# 編譯器 \(csc.exe\)，將產生的程式碼編譯成程式庫的語法。  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` 指示詞告訴工具要編譯到程式庫，而 `/r:` 指示詞則指定編譯所需要的相依程式庫。  該命令的輸出為 XSDSchemaFileName.dll，而在使用 `/r:` 指示詞編譯 ADO.NET 應用程式時，可以將該檔案傳遞給編譯器。  
  
 下列程式碼顯示存取 ADO.NET 應用程式內傳遞給 XSD.exe 命名空間的語法。  
  
```vb  
Imports XSDSchema.Namespace  
  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 下列程式碼範例使用名為 **CustomerDataSet** 且具型別的 **DataSet**，從 **Northwind** 資料庫載入客戶清單。  一旦使用 **Fill** 方法載入資料，該範例便會使用具型別 **CustomersRow** \(**DataRow**\) 物件，在 **Customers** 資料表內的每個客戶中執行迴圈。  這樣就能直接存取 **CustomerID** 資料行，與透過 **DataColumnCollection** 存取資料行相反。  
  
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
  
```  
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
  
## 請參閱  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataSet>   
 [具型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)