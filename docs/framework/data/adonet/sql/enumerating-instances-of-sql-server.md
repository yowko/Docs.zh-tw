---
title: 列舉 SQL Server 執行個體 (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: c464762e82a24aab399a23ecb26420b5dce61f55
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782384"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>列舉 SQL Server 執行個體 (ADO.NET)
SQL Server 允許應用程式在目前網路內尋找 SQL Server 實例。 <xref:System.Data.Sql.SqlDataSourceEnumerator> 類別會將此資訊公開至應用程式開發人員，並提供包含所有可見伺服器之相關資訊的 <xref:System.Data.DataTable>。 這個傳回的資料表包含網路上可用的伺服器實例清單，此清單會符合使用者嘗試建立新連接時所提供的清單，並展開包含連接屬性上所有可用伺服器的下拉式清單對話方塊。 顯示的結果不一定是完整的。  
  
> [!NOTE]
> 與大部分的 Windows 服務一樣，最好使用儘可能少的權限來執行 SQL Browser 服務。 如需 SQL Browser 服務及如何管理其行為的詳細資訊，請參閱《SQL Server 線上叢書》。  
  
## <a name="retrieving-an-enumerator-instance"></a>擷取列舉值執行個體  
 若要擷取包含可用 SQL Server 執行個體相關資訊的資料表，必須先使用共用/靜態 <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> 屬性擷取列舉值：  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 擷取靜態執行個體後，您就可以呼叫 <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> 方法，它可用來傳回包含可用伺服器相關資訊的 <xref:System.Data.DataTable>：  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 從方法呼叫傳回的資料表包含下列資料行 (其中都包含 `string` 值)：  
  
|「資料行」|描述|  
|------------|-----------------|  
|**ServerName**|伺服器名稱。|  
|**InstanceName**|伺服器執行個體的名稱。 如果伺服器做為預設執行個體執行，則此處為空白。|  
|**IsClustered**|表示伺服器是否為叢集的一部分。|  
|**版本**|伺服器版本。 例如：<br /><br /> -9.00. x （SQL Server 2005）<br />-10.0. xx （SQL Server 2008）<br />-10.50. x （SQL Server 2008 R2）<br />-11.0. xx （SQL Server 2012）|  
  
## <a name="enumeration-limitations"></a>列舉型別限制  
 可能會，也可能不會列出所有可用的伺服器。 此清單需視逾時及網路流量之類的因素而定。 這可能會導致兩個連續呼叫的清單不同， 而只會列出相同網路上的伺服器。 廣播封包通常不會周遊路由器，因此您可能看不到某個列出的伺服器，但它在所有呼叫中都是穩定的。  
  
 列出的伺服器不一定具有 `IsClustered` 及版本之類的其他資訊。 這要視取得清單的方式而定。 透過 SQL Server 瀏覽器服務列出的伺服器所具有的詳細資訊，要多於透過 Windows 基礎結構找到的伺服器 (僅列出名稱)。  
  
> [!NOTE]
> 只有在完全信任下執行時，伺服器列舉型別才可使用。 執行在部分信任環境中的組件即使具有 <xref:System.Data.SqlClient.SqlClientPermission> 程式碼存取安全性 (CAS) 使用權限，也無法使用伺服器列舉型別。  
  
 SQL Server 透過使用名為<xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser 的外部 Windows 服務，提供的資訊。 依預設會啟用此服務，但系統管理員可能會關閉或停用服務，讓此類別看不到伺服器執行個體。  
  
## <a name="example"></a>範例  
 下列主控台應用程式會擷取所有可見 SQL Server 執行個體的相關資訊，並在主控台視窗中顯示資訊。  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 和 ADO.NET](index.md)
- [ADO.NET 概觀](../ado-net-overview.md)
