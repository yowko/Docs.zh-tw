---
title: 使用一個或多個 REF CURSOR 填入資料集
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
ms.openlocfilehash: 66dc61a3eb71fcc6657a455f13aa1d67cca554ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a><span data-ttu-id="cdf4c-102">使用一個或多個 REF CURSOR 填入資料集</span><span class="sxs-lookup"><span data-stu-id="cdf4c-102">Filling a DataSet Using One or More REF CURSORs</span></span>
<span data-ttu-id="cdf4c-103">此 Microsoft Visual Basic 範例執行可傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列來填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="cdf4c-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
    "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Dim ds As New DataSet()  
    Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter( _  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
       ParameterDirection.Output  
  
    Dim da As New OracleDataAdapter(cmd)  
    da.TableMappings.Add("Table", "Emp")  
    da.TableMappings.Add("Table1", "Dept")  
    da.Fill(ds)  
  
    ds.Relations.Add("EmpDept", ds.Tables("Dept").Columns("Deptno"), _  
      ds.Tables("Emp").Columns("Deptno"), False)  
  
    DataGrid1.DataSource = ds.Tables("Dept")  
  End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdf4c-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf4c-104">See Also</span></span>  
 [<span data-ttu-id="cdf4c-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="cdf4c-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="cdf4c-106">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="cdf4c-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
