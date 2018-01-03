---
title: "列舉 SQL Server 執行個體 (ADO.NET)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 679196a6cc21705c8cc07e373a928f3c77c6befb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>列舉 SQL Server 執行個體 (ADO.NET)
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 允許應用程式在目前網路內尋找 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體。 <xref:System.Data.Sql.SqlDataSourceEnumerator> 類別會將此資訊公開至應用程式開發人員，並提供包含所有可見伺服器之相關資訊的 <xref:System.Data.DataTable>。 傳回這個資料表包含一份符合使用者嘗試建立新的連接時所提供的清單，並展開下拉式清單包含所有可用的伺服器上的網路上可用的伺服器執行個體**連線屬性** 對話方塊。 顯示的結果不一定是完整的。  
  
> [!NOTE]
>  與大部分的 Windows 服務一樣，最好使用儘可能少的權限來執行 SQL Browser 服務。 如需 SQL Browser 服務及如何管理其行為的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》。  
  
## <a name="retrieving-an-enumerator-instance"></a>擷取列舉值執行個體  
 若要擷取包含可用 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體相關資訊的資料表，您必須先使用共用/靜態 <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> 屬性擷取列舉值：  
  
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
  
|Column|描述|  
|------------|-----------------|  
|**伺服器名稱**|伺服器名稱。|  
|**執行個體名稱**|伺服器執行個體的名稱。 如果伺服器做為預設執行個體執行，則此處為空白。|  
|**IsClustered**|表示伺服器是否為叢集的一部分。|  
|**版本**|伺服器版本。 例如: <br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012年)|  
  
## <a name="enumeration-limitations"></a>列舉型別限制  
 可能會，也可能不會列出所有可用的伺服器。 此清單需視逾時及網路流量之類的因素而定。 這可能會導致兩個連續呼叫的清單不同， 而只會列出相同網路上的伺服器。 廣播封包通常不會周遊路由器，因此您可能看不到某個列出的伺服器，但它在所有呼叫中都是穩定的。  
  
 列出的伺服器不一定具有 `IsClustered` 及版本之類的其他資訊。 這要視取得清單的方式而定。 透過 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Browser 服務列出的伺服器所具有的詳細資訊，要多於透過 Windows 基礎結構找到的伺服器 (僅列出名稱)。  
  
> [!NOTE]
>  只有在完全信任下執行時，伺服器列舉型別才可使用。 執行在部分信任環境中的組件即使具有 <xref:System.Data.SqlClient.SqlClientPermission> 程式碼存取安全性 (CAS) 使用權限，也無法使用伺服器列舉型別。  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 可藉由使用名為 SQL Browser 的外部 Windows 服務來提供 <xref:System.Data.Sql.SqlDataSourceEnumerator> 相關資訊。 依預設會啟用此服務，但系統管理員可能會關閉或停用服務，讓此類別看不到伺服器執行個體。  
  
## <a name="example"></a>範例  
 下列主控台應用程式會擷取所有可見 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體的相關資訊，並在主控台視窗中顯示資訊。  
  
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
  
## <a name="see-also"></a>請參閱  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
