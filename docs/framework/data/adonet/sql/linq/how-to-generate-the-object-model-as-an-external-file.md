---
title: 作法：產生物件模型作為外部檔案
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 2442caec5400759ae2bfeca35f99ebd2ff52d011
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180760"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>作法：產生物件模型作為外部檔案

除了使用以屬性 (Attribute) 為基礎的對應，您還可以使用 SQLMetal 命令列工具，產生自己的物件模型做為外部 XML 檔。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。 藉由使用外部 XML 對應檔案，您可以避免程式碼雜亂。 此外，若要變更行為，也只需要修改外部檔案，而無須重新編譯應用程式的二進位碼檔案。 如需詳細資訊，請參閱 [外部對應](external-mapping.md)。  
  
> [!NOTE]
> 物件關聯式設計工具不支援產生外部對應檔案。  
  
## <a name="example"></a>範例  

 下列命令會從 Northwind 範例資料庫產生外部對應檔案。  
  
```console  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>範例  

 下列外部對應檔案摘錄顯示 Northwind 範例資料庫中之 Customers 資料表的對應。 此摘錄是藉由使用 **/map** 選項執行 SQLMetal 所產生。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>另請參閱

- [建立物件模型](creating-the-object-model.md)
- [外部對應](external-mapping.md)
- [作法：以 Visual Basic 或 C# 產生物件模型](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
