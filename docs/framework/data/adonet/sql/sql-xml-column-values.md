---
title: SQL XML 資料行值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 29e9ac5b95b62ef2a4467bf41484c3740d550abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964955"
---
# <a name="sql-xml-column-values"></a>SQL XML 資料行值
SQL Server 支援`xml`資料類型, 而開發人員可以使用<xref:System.Data.SqlClient.SqlCommand>類別的標準行為來抓取包含此類型的結果集。 如同擷取任意資料行一樣，您可以擷取 `xml` 資料行 (例如，擷取至 <xref:System.Data.SqlClient.SqlDataReader>)，但是如果您要以 XML 的型式來使用資料行的內容，則必須使用 <xref:System.Xml.XmlReader>。  
  
## <a name="example"></a>範例  
 下列主控台應用程式會從`xml` **AdventureWorks**資料庫<xref:System.Data.SqlClient.SqlDataReader>的**Sales. Store**資料表中, 選取包含資料行的兩個數據列。 針對每個資料列，可使用 `xml` 的 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 方法讀取 <xref:System.Data.SqlClient.SqlDataReader> 資料行的值。 該值儲存在 <xref:System.Xml.XmlReader> 中。 請注意，如果您要將內容設為 <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 變數，則必須使用 <xref:System.Data.IDataRecord.GetValue%2A> 而不是 <xref:System.Data.SqlTypes.SqlXml> 方法；<xref:System.Data.IDataRecord.GetValue%2A> 會以字串的形式傳回 `xml` 的值。  
  
> [!NOTE]
> 當您安裝 SQL Server 時, 預設不會安裝**AdventureWorks**範例資料庫。 您可以藉由執行 SQL Server 安裝程式來安裝它。  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server 中的 XML 資料](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
