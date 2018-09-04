---
title: 使用 OracleDataReader 從多個 REF CURSOR 擷取資料
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: d9da85f8998905689115cf24fb84870af45ea105
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514945"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="4608a-102">使用 OracleDataReader 從多個 REF CURSOR 擷取資料</span><span class="sxs-lookup"><span data-stu-id="4608a-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>
<span data-ttu-id="4608a-103">此 Microsoft Visual Basic 範例執行可傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用 <xref:System.Data.OracleClient.OracleDataReader> 讀取值。</span><span class="sxs-lookup"><span data-stu-id="4608a-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click( _  
  ByVal sender As Object, ByVal e As System.EventArgs)  _  
  Handles Button1.Click  
  
  Dim connString As New String( _  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter(_  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
    While (rdr.Read())  
        REM do something with the values from the EMP table   
    End While  
  
    rdr.NextResult()  
    While (rdr.Read())  
        REM do something with the values from the DEPT table   
    End While  
    rdr.Close()  
  End Using  
End Sub   
```  
  
## <a name="see-also"></a><span data-ttu-id="4608a-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4608a-104">See Also</span></span>  
 [<span data-ttu-id="4608a-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4608a-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="4608a-106">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4608a-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
