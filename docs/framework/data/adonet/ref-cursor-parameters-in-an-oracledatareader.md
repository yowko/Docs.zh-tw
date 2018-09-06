---
title: OracleDataReader 中的 REF CURSOR 參數
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 801dff0f-2508-45aa-9416-f45d6887740c
ms.openlocfilehash: 3a2c8949537c749ba30b116a0dc8131336de6092
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43884571"
---
# <a name="ref-cursor-parameters-in-an-oracledatareader"></a><span data-ttu-id="a8b86-102">OracleDataReader 中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="a8b86-102">REF CURSOR Parameters in an OracleDataReader</span></span>
<span data-ttu-id="a8b86-103">此 Microsoft Visual Basic 範例執行可傳回 REF CURSOR 參數的 PL/SQL 預存程序，並以 <xref:System.Data.OracleClient.OracleDataReader> 讀取該值。</span><span class="sxs-lookup"><span data-stu-id="a8b86-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_ONE_CURSOR"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter(  
      "N_EMPNO", OracleType.Number)).Value = 7369  
    cmd.Parameters.Add(New OracleParameter(  
      "IO_CURSOR", OracleType.Cursor)).Direction = ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader()  
    While (rdr.Read())  
        REM do something with the values  
    End While  
  
    rdr.Close()  
  End Using  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8b86-104">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b86-104">See Also</span></span>  
 [<span data-ttu-id="a8b86-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a8b86-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="a8b86-106">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a8b86-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
