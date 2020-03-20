---
title: 使用 OracleDataReader 從多個 REF CURSOR 擷取資料
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 8ece2617dd81161cb19a08d62f14d37c0f8c1f33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149033"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="97258-102">使用 OracleDataReader 從多個 REF CURSOR 擷取資料</span><span class="sxs-lookup"><span data-stu-id="97258-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>
<span data-ttu-id="97258-103">此 Microsoft Visual Basic 範例執行可傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用 <xref:System.Data.OracleClient.OracleDataReader> 讀取值。</span><span class="sxs-lookup"><span data-stu-id="97258-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97258-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97258-104">See also</span></span>

- [<span data-ttu-id="97258-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="97258-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- <span data-ttu-id="97258-106">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="97258-106">[ADO.NET Overview](ado-net-overview.md)</span></span>
